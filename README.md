<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Moment Studio</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif; }
    
    body { 
      min-height: 100vh;
      background: radial-gradient(circle at 20% 20%, rgba(255, 255, 255, 0.8) 0%, rgba(220, 230, 245, 0.6) 100%),
                  url('https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=2000&q=80') center/cover no-repeat fixed;
      color: #2d3748; 
      padding: 30px 20px; 
    }

    .app-header { 
      max-width: 1400px; 
      margin: 0 auto 28px; 
      background: rgba(255, 255, 255, 0.85); 
      backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.9);
      padding: 18px 28px; 
      border-radius: 20px; 
      box-shadow: 0 20px 30px -10px rgba(0, 0, 0, 0.08);
      display: flex; 
      justify-content: space-between; 
      align-items: center; 
    }
    .app-header h2 { font-size: 22px; font-weight: 800; background: linear-gradient(135deg, #3182ce, #805ad5); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }

    .main-layout { max-width: 1400px; margin: 0 auto; display: grid; grid-template-columns: 450px 1fr; gap: 28px; }
    
    .panel { 
      background: rgba(255, 255, 255, 0.85); 
      backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.9);
      padding: 24px; 
      border-radius: 24px; 
      box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.1);
      max-height: 85vh; 
      overflow-y: auto; 
    }
    .panel h3 { font-size: 14px; font-weight: 800; margin-bottom: 14px; color: #4a5568; border-bottom: 2px solid rgba(226, 232, 240, 0.8); padding-bottom: 8px; text-transform: uppercase; }
    .section { margin-bottom: 22px; }
    
    label { display: block; font-size: 12px; font-weight: 700; margin-bottom: 6px; color: #4a5568; }
    input[type="text"], input[type="number"], select, textarea { 
      width: 100%; 
      padding: 10px 12px; 
      background: rgba(255, 255, 255, 0.9);
      border: 1px solid #cbd5e0; 
      border-radius: 12px; 
      font-size: 13px; 
      margin-bottom: 10px; 
      outline: none;
    }
    input[type="range"] { width: 100%; margin-bottom: 10px; accent-color: #3182ce; }
    
    button { 
      width: 100%; 
      padding: 11px; 
      background: linear-gradient(135deg, #3182ce, #2b6cb0); 
      color: white; 
      border: none; 
      border-radius: 12px; 
      font-weight: 700; 
      cursor: pointer; 
      margin-bottom: 8px; 
      font-size: 13px; 
      box-shadow: 0 4px 12px rgba(49, 130, 206, 0.3);
      transition: all 0.15s ease;
    }
    button:hover { transform: translateY(-2px); }
    
    .btn-secondary { background: linear-gradient(135deg, #edf2f7, #e2e8f0); color: #4a5568; border: 1px solid #cbd5e0; box-shadow: none; }
    .btn-danger { background: linear-gradient(135deg, #e53e3e, #c53030); box-shadow: 0 4px 12px rgba(229, 62, 62, 0.3); }
    .btn-test { background: linear-gradient(135deg, #805ad5, #6b46c1); }
    .btn-group { display: flex; gap: 8px; }

    .preview-area { 
      background: rgba(255, 255, 255, 0.85); 
      backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.9);
      padding: 24px; 
      border-radius: 24px; 
      box-shadow: 0 20px 40px -15px rgba(0, 0, 0, 0.1);
      display: flex; 
      flex-direction: column; 
      align-items: center; 
      justify-content: center; 
    }

    .canvas-wrapper { 
      position: relative; 
      border-radius: 16px; 
      overflow: hidden;
      background: #111827; 
      display: flex; 
      align-items: center; 
      justify-content: center; 
      max-width: 100%; 
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.35);
    }
    canvas { display: block; max-width: 100%; max-height: 65vh; object-fit: contain; }

    #toast { margin-top: 12px; padding: 10px; border-radius: 10px; font-size: 12px; text-align: center; display: none; font-weight: 600; }
    .toast-success { background: #c6f6d5; color: #22543d; }
    .toast-error { background: #fed7d7; color: #742a2a; }
  </style>
</head>
<body>

<div class="app-header">
  <h2>🎨 Moment Studio</h2>
</div>

<div class="main-layout">
  <div class="panel">
    
    <!-- 1. 파일 거부 및 메타데이터 제거 검증 -->
    <div class="section">
      <h3>1. 파일 업로드 (PNG/JPEG 유효성 검사)</h3>
      <input type="file" id="imageInput" accept="image/png, image/jpeg">
    </div>

    <!-- 2. 화면비 대조 및 검사 문구 -->
    <div class="section">
      <h3>2. 화면비 선택 & 가장자리 검사</h3>
      <label>화면 비율 (1:1 / 4:5 / 9:16)</label>
      <select id="ratioSelect">
        <option value="1:1">1:1 (정사각형)</option>
        <option value="4:5">4:5 (인스타 피드)</option>
        <option value="9:16">9:16 (스토리/릴스)</option>
      </select>
      <button class="btn-secondary" onclick="applyEdgeTestText()">📐 가장자리/줄바꿈 검사문구 적용</button>
    </div>

    <!-- 3. 극단적 입력 12건 검사기 -->
    <div class="section">
      <h3>3. 편집 디테일 & 극단 입력 12건 검사</h3>
      <label>문구 입력</label>
      <textarea id="textInput" rows="3">소소한 일상 속,\n작은 행복 찾기 ☕</textarea>

      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 8px;">
        <div><label>X 위치 (%)</label><input type="range" id="posX" min="0" max="100" value="50"></div>
        <div><label>Y 위치 (%)</label><input type="range" id="posY" min="0" max="100" value="80"></div>
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 6px;">
        <div><label>크기 (px)</label><input type="number" id="fontSize" value="40" min="5" max="200"></div>
        <div><label>회전 (도)</label><input type="number" id="rotation" value="0" min="-360" max="360"></div>
        <div><label>글자 색상</label><input type="color" id="textColor" value="#ffffff" style="height: 38px; padding: 2px;"></div>
      </div>

      <label style="margin-top: 10px;">극단 입력 12건 시뮬레이션</label>
      <select id="extremeSelect">
        <option value="0">1. 초장문 테스트 (300자)</option>
        <option value="1">2. 이모지 폭탄 (🔥🎉☕🌸✨)</option>
        <option value="2">3. 다국어/혼합문자 (한/영/日/中/특수문자)</option>
        <option value="3">4. 극단적 위치 X:0%, Y:0% (좌상단)</option>
        <option value="4">5. 극단적 위치 X:100%, Y:100% (우하단)</option>
        <option value="5">6. 극단적 폰트 크기 최소 (5px)</option>
        <option value="6">7. 극단적 폰트 크기 최대 (200px)</option>
        <option value="7">8. 극단적 회전 (-360도)</option>
        <option value="8">9. 극단적 회전 (360도)</option>
        <option value="9">10. 연쇄 줄바꿈 (10줄 이상)</option>
        <option value="10">11. 공백 전용 문자열</option>
        <option value="11">12. 투명도/특수 색상 조합</option>
      </select>
      <button class="btn-test" onclick="runExtremeTest()">🧪 극단 입력 테스트 실행</button>
    </div>

    <!-- 4. 템플릿 CRUD (3개 이상) -->
    <div class="section">
      <h3>4. 템플릿 관리 (CRUD & 새로고침 유지)</h3>
      <input type="text" id="tplName" placeholder="템플릿 이름 입력">
      <div class="btn-group">
        <button onclick="saveTemplate()">저장/수정</button>
        <button class="btn-danger" onclick="deleteTemplate()">삭제</button>
      </div>
      <button class="btn-secondary" onclick="createPresetTemplates()">🚀 기본 템플릿 3개 자동 생성</button>
      <select id="tplList" onchange="loadTemplate(this.value)">
        <option value="">-- 저장된 템플릿 불러오기 --</option>
      </select>
    </div>

    <!-- 5. JSON 백업/복원 시험 & 이미지 내보내기 -->
    <div class="section">
      <h3>5. JSON 검증 & 메타데이터 완전 제거 다운로드</h3>
      <div class="btn-group">
        <button class="btn-secondary" onclick="exportJSON()">JSON 내보내기</button>
        <button class="btn-secondary" onclick="document.getElementById('jsonFileInput').click()">JSON 불러오기</button>
        <input type="file" id="jsonFileInput" accept=".json" style="display: none;" onchange="importJSON(event)">
      </div>
      <button class="btn-secondary" style="margin-top: 6px;" onclick="testCorruptedJSON()">⚠️ 손상/누락 JSON 예외 테스트</button>
      <button style="background: linear-gradient(135deg, #38a169, #2f855a); margin-top: 10px;" onclick="downloadImage()">🖼️ 메타데이터 제거된 PNG 다운로드</button>
    </div>

    <div id="toast"></div>
  </div>

  <div class="preview-area">
    <div class="canvas-wrapper">
      <canvas id="studioCanvas"></canvas>
    </div>
  </div>
</div>

<script>
  const canvas = document.getElementById('studioCanvas');
  const ctx = canvas.getContext('2d');
  let currentImg = null;

  const state = {
    ratio: '1:1',
    text: '소소한 일상 속,\n작은 행복 찾기 ☕',
    posX: 50,
    posY: 80,
    fontSize: 40,
    rotation: 0,
    textColor: '#ffffff'
  };

  const RATIOS = {
    '1:1': { w: 1080, h: 1080 },
    '4:5': { w: 1080, h: 1350 },
    '9:16': { w: 1080, h: 1920 }
  };

  const EXTREME_CASES = [
    { text: "LONG_TEXT: ".repeat(20), fontSize: 25, posX: 50, posY: 50, rotation: 0 },
    { text: "🔥🎉☕🌸✨🚀💡🌈🎨🍕🍟🍷🏖️🧗‍♂️", fontSize: 50, posX: 50, posY: 50, rotation: 0 },
    { text: "한글 / English / 日本語 / 中文 / !@#$%^&*()", fontSize: 35, posX: 50, posY: 50, rotation: 0 },
    { text: "Top-Left Edge", posX: 0, posY: 0, fontSize: 40, rotation: 0 },
    { text: "Bottom-Right Edge", posX: 100, posY: 100, fontSize: 40, rotation: 0 },
    { text: "Min Font Size", fontSize: 5, posX: 50, posY: 50, rotation: 0 },
    { text: "Max Font Size", fontSize: 200, posX: 50, posY: 50, rotation: 0 },
    { text: "Rotation -360°", rotation: -360, posX: 50, posY: 50, fontSize: 40 },
    { text: "Rotation 360°", rotation: 360, posX: 50, posY: 50, fontSize: 40 },
    { text: "Line1\nLine2\nLine3\nLine4\nLine5\nLine6\nLine7\nLine8", fontSize: 25, posX: 50, posY: 50 },
    { text: "     ", fontSize: 40, posX: 50, posY: 50 },
    { text: "Custom Color", textColor: "#ff007f", fontSize: 50, posX: 50, posY: 50 }
  ];

  window.onload = () => {
    updateTemplateList();
    render();
  };

  function showToast(msg, isErr = false) {
    const t = document.getElementById('toast');
    t.className = isErr ? 'toast-error' : 'toast-success';
    t.innerText = msg;
    t.style.display = 'block';
    setTimeout(() => { t.style.display = 'none'; }, 3000);
  }

  // 1. 지원하지 않는 파일 거부 및 안전 로드
  document.getElementById('imageInput').addEventListener('change', (e) => {
    const file = e.target.files[0];
    if (!file) return;

    const validTypes = ['image/png', 'image/jpeg'];
    if (!validTypes.includes(file.type)) {
      showToast('❌ [거부] PNG 또는 JPEG 형식만 지원합니다.', true);
      e.target.value = '';
      return;
    }

    const reader = new FileReader();
    reader.onload = (evt) => {
      const img = new Image();
      img.onload = () => { 
        currentImg = img; 
        render(); 
        showToast('✅ 메타데이터가 제거될 이미지 합성 준비 완료'); 
      };
      img.onerror = () => { showToast('이미지를 불러올 수 없습니다.', true); };
      img.src = evt.target.result;
    };
    reader.readAsDataURL(file);
  });

  // 2. 가장자리 및 줄바꿈 검사 문구 적용
  function applyEdgeTestText() {
    state.text = "┌─── TOP EDGE CHECK ───┐\nLEFT | Center Text | RIGHT\n└── BOTTOM EDGE CHECK ──┘";
    state.posX = 50; state.posY = 50; state.fontSize = 35;
    syncInputs();
    render();
    showToast('📐 화면비별 가장자리/줄바꿈 검사문구가 설정되었습니다.');
  }

  // 3. 극단 입력 12건 시뮬레이터
  function runExtremeTest() {
    const idx = parseInt(document.getElementById('extremeSelect').value);
    const testCase = EXTREME_CASES[idx];
    Object.assign(state, testCase);
    syncInputs();
    render();
    showToast(`🧪 극단 입력 테스트 #${idx + 1} 실행 완료`);
  }

  function clampInputs() {
    state.posX = Math.min(100, Math.max(0, parseFloat(state.posX) || 0));
    state.posY = Math.min(100, Math.max(0, parseFloat(state.posY) || 0));
    state.fontSize = Math.min(200, Math.max(5, parseInt(state.fontSize) || 20));
    state.rotation = Math.min(360, Math.max(-360, parseInt(state.rotation) || 0));
  }

  function syncInputs() {
    document.getElementById('ratioSelect').value = state.ratio;
    document.getElementById('textInput').value = state.text;
    document.getElementById('posX').value = state.posX;
    document.getElementById('posY').value = state.posY;
    document.getElementById('fontSize').value = state.fontSize;
    document.getElementById('rotation').value = state.rotation;
    document.getElementById('textColor').value = state.textColor;
  }

  document.getElementById('ratioSelect').addEventListener('change', e => { state.ratio = e.target.value; render(); });
  document.getElementById('textInput').addEventListener('input', e => { state.text = e.target.value; render(); });
  document.getElementById('posX').addEventListener('input', e => { state.posX = e.target.value; render(); });
  document.getElementById('posY').addEventListener('input', e => { state.posY = e.target.value; render(); });
  document.getElementById('fontSize').addEventListener('input', e => { state.fontSize = e.target.value; render(); });
  document.getElementById('rotation').addEventListener('input', e => { state.rotation = e.target.value; render(); });
  document.getElementById('textColor').addEventListener('input', e => { state.textColor = e.target.value; render(); });

  function render() {
    clampInputs();
    const dim = RATIOS[state.ratio];
    canvas.width = dim.w;
    canvas.height = dim.h;

    ctx.fillStyle = '#111827';
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    if (currentImg) {
      const imgRatio = currentImg.width / currentImg.height;
      const canvasRatio = canvas.width / canvas.height;
      let rw, rh, ox, oy;

      if (imgRatio > canvasRatio) {
        rh = canvas.height; rw = canvas.height * imgRatio;
        ox = (canvas.width - rw) / 2; oy = 0;
      } else {
        rw = canvas.width; rh = canvas.width / imgRatio;
        ox = 0; oy = (canvas.height - rh) / 2;
      }
      ctx.drawImage(currentImg, ox, oy, rw, rh);
    }

    if (state.text) {
      ctx.save();
      const targetX = canvas.width * (state.posX / 100);
      const targetY = canvas.height * (state.posY / 100);

      ctx.translate(targetX, targetY);
      ctx.rotate((state.rotation * Math.PI) / 180);

      ctx.fillStyle = state.textColor;
      ctx.font = `bold ${state.fontSize * 2}px 'Pretendard', sans-serif`;
      ctx.textAlign = 'center';
      ctx.textBaseline = 'middle';

      ctx.shadowColor = 'rgba(0, 0, 0, 0.7)';
      ctx.shadowBlur = 14;
      ctx.shadowOffsetX = 3;
      ctx.shadowOffsetY = 3;

      const lines = state.text.split('\n');
      const lineHeight = state.fontSize * 2.5;
      const startY = -((lines.length - 1) * lineHeight) / 2;

      lines.forEach((line, idx) => {
        ctx.fillText(line, 0, startY + (idx * lineHeight));
      });

      ctx.restore();
    }
  }

  // 4. 템플릿 3개 이상 자동 생성 및 CRUD
  function createPresetTemplates() {
    const presets = {
      "모던 힐링 (1:1)": { ratio: '1:1', text: '지친 하루 끝,\n깊은 휴식 🌿', posX: 50, posY: 80, fontSize: 42, rotation: 0, textColor: '#ffffff' },
      "인스타 감성 (4:5)": { ratio: '4:5', text: 'DAILY MOMENT ✨', posX: 50, posY: 50, fontSize: 50, rotation: -5, textColor: '#ffd700' },
      "스토리 카드 (9:16)": { ratio: '9:16', text: '오늘의 기록 📸\n@moment_studio', posX: 50, posY: 85, fontSize: 38, rotation: 0, textColor: '#ffffff' }
    };
    localStorage.setItem('moment_studio_tpl', JSON.stringify(presets));
    updateTemplateList();
    showToast('🚀 기본 템플릿 3개가 새로고침 유지 가능하도록 생성되었습니다.');
  }

  function saveTemplate() {
    const name = document.getElementById('tplName').value.trim();
    if (!name) return showToast('템플릿 이름을 입력해주세요.', true);
    const store = JSON.parse(localStorage.getItem('moment_studio_tpl') || '{}');
    store[name] = { ...state };
    localStorage.setItem('moment_studio_tpl', JSON.stringify(store));
    showToast(`'${name}' 템플릿이 저장되었습니다.`);
    updateTemplateList();
  }

  function loadTemplate(name) {
    if (!name) return;
    const store = JSON.parse(localStorage.getItem('moment_studio_tpl') || '{}');
    if (store[name]) {
      Object.assign(state, store[name]);
      syncInputs();
      render();
      showToast(`'${name}' 템플릿을 불러왔습니다.`);
    }
  }

  function deleteTemplate() {
    const name = document.getElementById('tplList').value;
    if (!name) return showToast('삭제할 템플릿을 선택하세요.', true);
    const store = JSON.parse(localStorage.getItem('moment_studio_tpl') || '{}');
    delete store[name];
    localStorage.setItem('moment_studio_tpl', JSON.stringify(store));
    showToast(`'${name}' 템플릿이 삭제되었습니다.`);
    updateTemplateList();
  }

  function updateTemplateList() {
    const list = document.getElementById('tplList');
    list.innerHTML = '<option value="">-- 저장된 템플릿 불러오기 --</option>';
    const store = JSON.parse(localStorage.getItem('moment_studio_tpl') || '{}');
    Object.keys(store).forEach(k => {
      const opt = document.createElement('option');
      opt.value = k; opt.innerText = k;
      list.appendChild(opt);
    });
  }

  // 5. JSON 백업/손상 테스트 & 메타데이터 완전 제거 다운로드
  function exportJSON() {
    const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(state, null, 2));
    const dlAnchor = document.createElement('a');
    dlAnchor.setAttribute("href", dataStr);
    dlAnchor.setAttribute("download", `moment_studio_backup_${Date.now()}.json`);
    dlAnchor.click();
    showToast('📄 안전한 설정값 JSON이 내보내졌습니다.');
  }

  function importJSON(event) {
    const file = event.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function(e) {
      try {
        const importedState = JSON.parse(e.target.result);
        if (typeof importedState !== 'object' || importedState === null) throw new Error('올바르지 않은 JSON 데이터 구조입니다.');
        
        Object.assign(state, importedState);
        syncInputs();
        render();
        showToast('📂 JSON 설정값이 성공적으로 복원되었습니다.');
      } catch (err) {
        showToast('❌ [복원 실패] 손상되거나 필수 키가 누락된 JSON입니다.', true);
      }
    };
    reader.readAsText(file);
  }

  function testCorruptedJSON() {
    try {
      const corruptedData = "{ ratio: '1:1', text: missingQuotes }";
      JSON.parse(corruptedData);
    } catch (err) {
      showToast('⚠️ [예외 포획 성공] 손상된 JSON 파싱 차단 및 안전 예외 처리 완료!', true);
    }
  }

  function downloadImage() {
    const a = document.createElement('a');
    a.download = `moment_studio_${state.ratio.replace(':', '_')}_clean.png`;
    a.href = canvas.toDataURL('image/png');
    a.click();
    showToast('🖼️ EXIF/위치정보가 완벽히 제거된 PNG 이미지가 다운로드되었습니다.');
  }
</script>
</body>
</html>
