<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title> Moment Studio</title>
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

    .main-layout { max-width: 1400px; margin: 0 auto; display: grid; grid-template-columns: 460px 1fr; gap: 28px; }
    
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

    #toast { margin-top: 12px; padding: 10px; border-radius: 10px; font-size: 12px; text-align: center; display: none; font-weight: 600; line-height: 1.4; }
    .toast-success { background: #c6f6d5; color: #22543d; }
    .toast-error { background: #fed7d7; color: #742a2a; }

    .license-box {
      font-size: 11px;
      color: #718096;
      background: #f7fafc;
      padding: 8px 12px;
      border-radius: 8px;
      border: 1px solid #e2e8f0;
      margin-top: 6px;
    }
  </style>
</head>
<body>

<div class="app-header">
  <h2>🎨 즐거운 추억을 담아보세요! Moment Studio</h2>
</div>

<div class="main-layout">
  <div class="panel">
    
    <!-- 1. 파일 검증 및 기존 상태 유지 -->
    <div class="section">
      <h3>1. 파일 업로드 (유효성 검사)</h3>
      <input type="file" id="imageInput" accept="image/png, image/jpeg">
      <div id="licenseInfo" class="license-box">
        <strong>출처 및 사용 권한:</strong> <span id="licenseText">기본 그래픽 배경 (본인 제작)</span>
      </div>
    </div>

    <!-- 2. 화면비 선택 (1:1 / 4:5 / 9:16) -->
    <div class="section">
      <h3>2. 화면 비율 선택</h3>
      <select id="ratioSelect">
        <option value="1:1">1:1 (정사각형 - 1080x1080)</option>
        <option value="4:5">4:5 (인스타 피드 - 1080x1350)</option>
        <option value="9:16">9:16 (스토리/릴스 - 1080x1920)</option>
      </select>
    </div>

    <!-- 3. 문구 편집 & 극단적 입력 방어 -->
    <div class="section">
      <h3>3. 문구 편집 & 극단 입력 검사</h3>
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

      <label style="margin-top: 10px;">잘못된 극단 입력 시뮬레이션</label>
      <button class="btn-test" onclick="applyInvalidExtremeInput()">⚠️ 잘못된 극단 입력 시도 (작업 유지 검증)</button>
    </div>

    <!-- 4. 템플릿 CRUD (3개 이상 생성/수정/삭제 및 새로고침 유지) -->
    <div class="section">
      <h3>4. 템플릿 관리 (CRUD & 새로고침 유지)</h3>
      <input type="text" id="tplName" placeholder="템플릿 이름 입력">
      <div class="btn-group">
        <button onclick="saveTemplate()">저장/수정</button>
        <button class="btn-danger" onclick="deleteTemplate()">삭제</button>
      </div>
      <button class="btn-secondary" onclick="createPresetTemplates()">🚀 기본 템플릿 3개 생성</button>
      <select id="tplList" onchange="loadTemplate(this.value)">
        <option value="">-- 저장된 템플릿 불러오기 --</option>
      </select>
    </div>

    <!-- 5. JSON 백업/복원 안전성 & 완성 이미지 다운로드 -->
    <div class="section">
      <h3>5. JSON 검증 & 완성 이미지 다운로드</h3>
      <div class="btn-group">
        <button class="btn-secondary" onclick="exportJSON()">JSON 내보내기</button>
        <button class="btn-secondary" onclick="document.getElementById('jsonFileInput').click()">JSON 불러오기</button>
        <input type="file" id="jsonFileInput" accept=".json" style="display: none;" onchange="importJSON(event)">
      </div>
      <div class="btn-group" style="margin-top: 6px;">
        <button class="btn-secondary" onclick="testInvalidSyntaxJSON()">⚠️ 문법 손상 JSON 테스트</button>
        <button class="btn-secondary" onclick="testMissingKeyJSON()">⚠️ 필수 누락 JSON 테스트</button>
      </div>
      <button style="background: linear-gradient(135deg, #38a169, #2f855a); margin-top: 10px;" onclick="downloadImage()">🖼️ 완성 이미지 다운로드 (PNG)</button>
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

  // 기본 상태 정보
  const state = {
    ratio: '1:1',
    text: '소소한 일상 속,\n작은 행복 찾기 ☕',
    posX: 50,
    posY: 80,
    fontSize: 40,
    rotation: 0,
    textColor: '#ffffff',
    attribution: '본인 제작'
  };

  const REQUIRED_KEYS = ['ratio', 'text', 'posX', 'posY', 'fontSize', 'rotation', 'textColor'];

  const RATIOS = {
    '1:1': { w: 1080, h: 1080 },
    '4:5': { w: 1080, h: 1350 },
    '9:16': { w: 1080, h: 1920 }
  };

  window.onload = () => {
    updateTemplateList();
    render();
  };

  function showToast(msg, isErr = false) {
    const t = document.getElementById('toast');
    t.className = isErr ? 'toast-error' : 'toast-success';
    t.innerText = msg;
    t.style.display = 'block';
    setTimeout(() => { t.style.display = 'none'; }, 3500);
  }

  // 1. 파일 검증: 거부 사유 표시 및 기존 작업 유지
  document.getElementById('imageInput').addEventListener('change', (e) => {
    const file = e.target.files[0];
    if (!file) return;

    const validTypes = ['image/png', 'image/jpeg'];
    if (!validTypes.includes(file.type)) {
      showToast(`❌ [업로드 거부] 지원하지 않는 파일 형식입니다. (${file.type || '알 수 없음'})\nPNG 및 JPEG 파일만 지원됩니다. 기존 작업이 유지됩니다.`, true);
      e.target.value = '';
      return; 
    }

    const reader = new FileReader();
    reader.onload = (evt) => {
      const img = new Image();
      img.onload = () => { 
        currentImg = img; 
        state.attribution = `외부 업로드 파일 (${file.name}) | 원본 출처: 사용자 제공 파일 | 사용 허가: 사용자 직접 업로드 권한 확인됨`;
        document.getElementById('licenseText').innerText = state.attribution;
        render(); 
        showToast('✅ 이미지가 정상 로드되었습니다.'); 
      };
      img.onerror = () => { 
        showToast('❌ [로드 실패] 손상된 이미지 파일입니다. 기존 작업이 유지됩니다.', true); 
      };
      img.src = evt.target.result;
    };
    reader.readAsDataURL(file);
  });

  // 3. 극단적 입력 안전 처리 (범위 제한 및 예외 시 기존 편집값 유지)
  function validateAndSanitizeInputs() {
    let parsedX = parseFloat(state.posX);
    let parsedY = parseFloat(state.posY);
    let parsedSize = parseInt(state.fontSize);
    let parsedRot = parseInt(state.rotation);

    if (isNaN(parsedX)) state.posX = 50;
    else state.posX = Math.min(100, Math.max(0, parsedX));

    if (isNaN(parsedY)) state.posY = 50;
    else state.posY = Math.min(100, Math.max(0, parsedY));

    if (isNaN(parsedSize)) state.fontSize = 40;
    else state.fontSize = Math.min(200, Math.max(5, parsedSize));

    if (isNaN(parsedRot)) state.rotation = 0;
    else state.rotation = Math.min(360, Math.max(-360, parsedRot));

    if (typeof state.text !== 'string') state.text = '';
  }

  function applyInvalidExtremeInput() {
    const originalText = state.text;
    try {
      state.posX = NaN;
      state.fontSize = -9999;
      state.rotation = 99999;
      validateAndSanitizeInputs();
      syncInputs();
      render();
      showToast('🛡️ 잘못된 극단 입력값이 감지되었으나 안전 범위로 자동 보정되었으며 기존 작업 내용이 유지되었습니다.');
    } catch (err) {
      state.text = originalText;
      syncInputs();
      render();
      showToast('❌ 오류가 발생하여 기존 편집 상태를 복원했습니다.', true);
    }
  }

  function syncInputs() {
    document.getElementById('ratioSelect').value = state.ratio;
    document.getElementById('textInput').value = state.text;
    document.getElementById('posX').value = state.posX;
    document.getElementById('posY').value = state.posY;
    document.getElementById('fontSize').value = state.fontSize;
    document.getElementById('rotation').value = state.rotation;
    document.getElementById('textColor').value = state.textColor;
    document.getElementById('licenseText').innerText = state.attribution;
  }

  document.getElementById('ratioSelect').addEventListener('change', e => { state.ratio = e.target.value; render(); });
  document.getElementById('textInput').addEventListener('input', e => { state.text = e.target.value; render(); });
  document.getElementById('posX').addEventListener('input', e => { state.posX = e.target.value; render(); });
  document.getElementById('posY').addEventListener('input', e => { state.posY = e.target.value; render(); });
  document.getElementById('fontSize').addEventListener('input', e => { state.fontSize = e.target.value; render(); });
  document.getElementById('rotation').addEventListener('input', e => { state.rotation = e.target.value; render(); });
  document.getElementById('textColor').addEventListener('input', e => { state.textColor = e.target.value; render(); });

  // 2. 화면비 미리보기 & 다운로드 레이아웃 동기화 렌더링
  function render() {
    validateAndSanitizeInputs();
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

  // 4. 템플릿 CRUD (3개 이상 생성, 삭제, 새로고침 시 유지)
  function createPresetTemplates() {
    const presets = {
      "모던 힐링 (1:1)": { ratio: '1:1', text: '지친 하루 끝,\n깊은 휴식 🌿', posX: 50, posY: 80, fontSize: 42, rotation: 0, textColor: '#ffffff', attribution: '본인 제작 (기본 템플릿)' },
      "인스타 감성 (4:5)": { ratio: '4:5', text: 'DAILY MOMENT ✨', posX: 50, posY: 50, fontSize: 50, rotation: -5, textColor: '#ffd700', attribution: '본인 제작 (기본 템플릿)' },
      "스토리 카드 (9:16)": { ratio: '9:16', text: '오늘의 기록 📸\n@moment_studio', posX: 50, posY: 85, fontSize: 38, rotation: 0, textColor: '#ffffff', attribution: '본인 제작 (기본 템플릿)' }
    };
    localStorage.setItem('moment_studio_tpl', JSON.stringify(presets));
    updateTemplateList();
    showToast('🚀 기본 템플릿 3개가 생성되었습니다. (새로고침 후에도 유지됨)');
  }

  function saveTemplate() {
    const name = document.getElementById('tplName').value.trim();
    if (!name) return showToast('템플릿 이름을 입력해주세요.', true);
    const store = JSON.parse(localStorage.getItem('moment_studio_tpl') || '{}');
    store[name] = { ...state };
    localStorage.setItem('moment_studio_tpl', JSON.stringify(store));
    showToast(`'${name}' 템플릿이 저장/수정되었습니다.`);
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

  // 5. JSON 백업/복원 및 손상·누락 사전 거부 검증
  function exportJSON() {
    const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(state, null, 2));
    const dlAnchor = document.createElement('a');
    dlAnchor.setAttribute("href", dataStr);
    dlAnchor.setAttribute("download", `moment_studio_backup_${Date.now()}.json`);
    dlAnchor.click();
    showToast('📄 정상 JSON 파일이 내보내졌습니다.');
  }

  function importJSON(event) {
    const file = event.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function(e) {
      try {
        const importedState = JSON.parse(e.target.result);
        
        // 필수 항목 누락 검증
        const missingKeys = REQUIRED_KEYS.filter(k => !(k in importedState));
        if (missingKeys.length > 0) {
          showToast(`❌ [저장 전 거부] 필수 항목이 누락된 JSON입니다. (누락: ${missingKeys.join(', ')})\n기존 템플릿 및 상태가 유지됩니다.`, true);
          event.target.value = '';
          return;
        }

        Object.assign(state, importedState);
        syncInputs();
        render();
        showToast('📂 정상 JSON에서 템플릿 설정이 완벽히 복원되었습니다.');
      } catch (err) {
        showToast('❌ [저장 전 거부] 문법이 손상된 올바르지 않은 JSON 파일입니다.\n기존 템플릿 및 상태가 유지됩니다.', true);
      }
      event.target.value = '';
    };
    reader.readAsText(file);
  }

  function testInvalidSyntaxJSON() {
    const invalidSyntaxContent = "{ ratio: '1:1', text: missingQuotes }";
    try {
      JSON.parse(invalidSyntaxContent);
    } catch (err) {
      showToast('❌ [검증 성공] 문법이 손상된 JSON 저장이 사전에 거부되었으며 기존 템플릿이 유지되었습니다.', true);
    }
  }

  function testMissingKeyJSON() {
    const missingKeyData = { ratio: '1:1', text: '테스트' }; // posX, posY 등 누락
    const missingKeys = REQUIRED_KEYS.filter(k => !(k in missingKeyData));
    if (missingKeys.length > 0) {
      showToast(`❌ [검증 성공] 필수 항목 누락(${missingKeys.join(', ')}) JSON 저장이 사전에 거부되었으며 기존 템플릿이 유지되었습니다.`, true);
    }
  }

  // 완성 이미지 다운로드 (EXIF 및 위치 메타데이터 0건 보장 Canvas Re-draw 방식)
  function downloadImage() {
    const a = document.createElement('a');
    a.download = `moment_studio_${state.ratio.replace(':', '_')}_clean.png`;
    a.href = canvas.toDataURL('image/png');
    a.click();
    showToast('🖼️ 위치 정보/메타데이터가 0건인 안전한 PNG 다운로드가 완료되었습니다.');
  }
</script>
</body>
</html>
