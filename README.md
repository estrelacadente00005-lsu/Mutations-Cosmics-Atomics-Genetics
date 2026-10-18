
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Impressora Quântica 6D - Simulação Cibernética</title>
    <style>
        :root {
            --bg-color: #050814;
            --panel-bg: rgba(10, 16, 34, 0.85);
            --neon-cyan: #00f3ff;
            --neon-purple: #bd00ff;
            --neon-green: #00ff66;
            --text-color: #e0ffc7;
            --border-color: rgba(0, 243, 255, 0.3);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Courier New', Courier, monospace;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            overflow-x: hidden;
        }

        header {
            text-align: center;
            margin-bottom: 20px;
        }

        h1 {
            font-size: 1.8rem;
            color: var(--neon-cyan);
            text-shadow: 0 0 10px rgba(0, 243, 255, 0.5);
            letter-spacing: 2px;
        }

        p.subtitle {
            font-size: 0.9rem;
            color: #8fa3cc;
            margin-top: 5px;
        }

        .main-container {
            display: grid;
            grid-template-columns: 350px 1fr;
            gap: 20px;
            width: 100%;
            max-width: 1200px;
        }

        @media (max-width: 900px) {
            .main-container {
                grid-template-columns: 1fr;
            }
        }

        .panel {
            background: var(--panel-bg);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 0 20px rgba(0, 243, 255, 0.1);
            backdrop-filter: blur(5px);
        }

        .panel h2 {
            font-size: 1.1rem;
            color: var(--neon-purple);
            margin-bottom: 15px;
            border-bottom: 1px solid rgba(189, 0, 255, 0.3);
            padding-bottom: 5px;
        }

        .stat-group {
            margin-bottom: 15px;
        }

        .stat-label {
            font-size: 0.8rem;
            color: #8fa3cc;
            display: block;
            margin-bottom: 3px;
        }

        .stat-value {
            font-size: 1.1rem;
            color: var(--neon-cyan);
            font-weight: bold;
        }

        .progress-bar-container {
            width: 100%;
            background: #101932;
            height: 10px;
            border-radius: 5px;
            border: 1px solid var(--border-color);
            margin-top: 5px;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, var(--neon-cyan), var(--neon-purple));
            transition: width 0.3s ease;
            box-shadow: 0 0 10px var(--neon-cyan);
        }

        .controls {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 20px;
        }

        button {
            background: transparent;
            border: 1px solid var(--neon-cyan);
            color: var(--neon-cyan);
            padding: 10px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            text-transform: uppercase;
            transition: all 0.3s ease;
            box-shadow: 0 0 5px rgba(0, 243, 255, 0.2);
        }

        button:hover {
            background: var(--neon-cyan);
            color: var(--bg-color);
            box-shadow: 0 0 15px var(--neon-cyan);
        }

        button.active {
            background: var(--neon-purple);
            border-color: var(--neon-purple);
            color: #fff;
            box-shadow: 0 0 15px var(--neon-purple);
        }

        .canvas-wrapper {
            position: relative;
            width: 100%;
            height: 550px;
            background: #02040a;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        canvas {
            display: block;
        }

        .log-box {
            background: #02040a;
            border: 1px solid rgba(143, 163, 204, 0.2);
            border-radius: 4px;
            padding: 10px;
            height: 120px;
            overflow-y: auto;
            font-size: 0.75rem;
            color: #a3c1ff;
            margin-top: 15px;
        }

        .log-entry {
            margin-bottom: 4px;
        }
    </style>
</head>
<body>

    <header>
        <h1>SISTEMA DE IMPRESSÃO QUÂNTICA 6D</h1>
        <p class="subtitle">Cenário 1: Integração Nanotecnológica, Biônica e Hipercondutora (Iron Man / Batman / Cyborg)</p>
    </header>

    <div class="main-container">
        <!-- Painel de Controle e Diagnóstico -->
        <div class="panel">
            <h2>DIAGNÓSTICO DO CHASSI</h2>
            
            <div class="stat-group">
                <span class="stat-label">MODO DE OPERAÇÃO:</span>
                <span class="stat-value" id="modeStatus">STANDBY</span>
            </div>

            <div class="stat-group">
                <span class="stat-label">INTEGRIDADE ÓSSEA (NANO-CHASSI):</span>
                <span class="stat-value" id="integrityValue">0.0%</span>
                <div class="progress-bar-container">
                    <div class="progress-bar" id="integrityBar"></div>
                </div>
            </div>

            <div class="stat-group">
                <span class="stat-label">ALINHAMENTO DE SPIN QUÂNTICO:</span>
                <span class="stat-value" id="spinValue">1.000 Spin</span>
            </div>

            <div class="stat-group">
                <span class="stat-label">LIGA HIPERCONDUTORA (MHD):</span>
                <span class="stat-value" id="mhdValue">Inativo</span>
            </div>

            <div class="controls">
                <button id="startBtn" onclick="toggleSimulation()">INICIAR IMPRESSÃO 6D</button>
                <button onclick="resetSimulation()">RESETAR SISTEMA</button>
            </div>

            <div class="log-box" id="logBox">
                <div class="log-entry">> Sistema inicializado. Aguardando comando...</div>
            </div>
        </div>

        <!-- Visor Gráfico / Canvas 2D -->
        <div class="canvas-wrapper">
            <canvas id="simulationCanvas" width="700" height="550"></canvas>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('simulationCanvas');
        const ctx = canvas.getContext('2d');

        let isRunning = false;
        let progress = 0;
        let laserY = 50;
        let laserDirection = 1;
        let particles = [];
        let circuitNodes = [];

        // Inicializar nós do esqueleto cibernético (simulando ossos, articulações e sistema nervoso)
        const skeletonBones = [
            { x: 350, y: 120, name: 'Crânio / SAMS Neurossensor' }, // Cabeça
            { x: 350, y: 160, name: 'Coluna Cervical' },
            { x: 350, y: 220, name: 'Chassi Torácico (Grade Costal)' },
            { x: 310, y: 200, name: 'Ombro Esquerdo (MHD)' },
            { x: 390, y: 200, name: 'Ombro Direito (MHD)' },
            { x: 270, y: 270, name: 'Braço Esquerdo Hipercondutor' },
            { x: 430, y: 270, name: 'Braço Direito Hipercondutor' },
            { x: 350, y: 310, name: 'Pelve / Matriz Nanométrica' },
            { x: 320, y: 410, name: 'Fêmur Esquerdo' },
            { x: 380, y: 410, name: 'Fêmur Direito' },
            { x: 300, y: 500, name: 'Tíbia / Pé Esquerdo' },
            { x: 400, y: 500, name: 'Tíbia / Pé Direito' }
        ];

        function addLog(message) {
            const logBox = document.getElementById('logBox');
            const time = new Date().toLocaleTimeString();
            logBox.innerHTML += `<div class="log-entry">[${time}] ${message}</div>`;
            logBox.scrollTop = logBox.scrollHeight;
        }

        function toggleSimulation() {
            isRunning = !isRunning;
            const btn = document.getElementById('startBtn');
            const modeStatus = document.getElementById('modeStatus');
            
            if (isRunning) {
                btn.textContent = 'PAUSAR IMPRESSÃO';
                btn.classList.add('active');
                modeStatus.textContent = 'IMPRESSÃO ATIVA (6D)';
                addLog('Iniciando manipulação de spin quântico e fase dimensional...');
            } else {
                btn.textContent = 'RETOMAR IMPRESSÃO';
                btn.classList.remove('active');
                modeStatus.textContent = 'PAUSADO';
                addLog('Impressão pausada pelo operador.');
            }
        }

        function resetSimulation() {
            isRunning = false;
            progress = 0;
            laserY = 50;
            particles = [];
            document.getElementById('startBtn').textContent = 'INICIAR IMPRESSÃO 6D';
            document.getElementById('startBtn').classList.remove('active');
            document.getElementById('modeStatus').textContent = 'STANDBY';
            document.getElementById('integrityValue').textContent = '0.0%';
            document.getElementById('integrityBar').style.width = '0%';
            document.getElementById('spinValue').textContent = '1.000 Spin';
            document.getElementById('mhdValue').textContent = 'Inativo';
            document.getElementById('logBox').innerHTML = '<div class="log-entry">> Sistema reiniciado. Pronto para nova varredura.</div>';
        }

        // Criar partículas de nanorrobôs quânticos
        function spawnParticles() {
            if (Math.random() < 0.6) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: laserY + (Math.random() * 20 - 10),
                    vx: (Math.random() - 0.5) * 2,
                    vy: Math.random() * 2 + 1,
                    size: Math.random() * 2 + 1,
                    color: Math.random() > 0.5 ? '#00f3ff' : '#bd00ff'
                });
            }
        }

        function updateSimulation() {
            if (isRunning) {
                if (progress < 100) {
                    progress += 0.25;
                    if (progress > 100) progress = 100;
                    
                    document.getElementById('integrityValue').textContent = progress.toFixed(1) + '%';
                    document.getElementById('integrityBar').style.width = progress + '%';
                    
                    document.getElementById('spinValue').textContent = (1.0 + (progress * 0.05)).toFixed(3) + ' Spin';
                    document.getElementById('mhdValue').textContent = progress > 50 ? 'Ativo (Nível Nuclear)' : 'Sincronizando...';

                    // Movimento do feixe laser da impressora
                    laserY += laserDirection * 2.5;
                    if (laserY > 520 || laserY < 50) {
                        laserDirection *= -1;
                    }

                    if (Math.floor(progress) === 25) addLog('Fase 1: Nanocomponentes fundidos ao tecido celular.');
                    if (Math.floor(progress) === 50) addLog('Fase 2: Ligas de Levitação Magnética (MHD) ativadas nos ossos.');
                    if (Math.floor(progress) === 75) addLog('Fase 3: Micro-piezoelétricos SAMS integrados ao sistema nervoso.');
                    if (Math.floor(progress) >= 100) {
                        addLog('>>> INTEGRAÇÃO CONCLUÍDA: Chassi indestrutível ativado com sucesso!');
                        isRunning = false;
                        document.getElementById('startBtn').textContent = 'CONCLUÍDO';
                        document.getElementById('modeStatus').textContent = 'OPERACIONAL';
                    }
                }
            }
        }

        function drawGrid() {
            ctx.strokeStyle = 'rgba(0, 243, 255, 0.05)';
            ctx.lineWidth = 1;
            const gridSize = 30;

            for (let x = 0; x < canvas.width; x += gridSize) {
                ctx.beginPath();
                ctx.moveTo(x, 0);
                ctx.lineTo(x, canvas.height);
                ctx.stroke();
            }
            for (let y = 0; y < canvas.height; y += gridSize) {
                ctx.beginPath();
                ctx.moveTo(0, y);
                ctx.lineTo(canvas.width, y);
                ctx.stroke();
            }
        }

        function drawSkeleton() {
            // Desenhar conexões esqueléticas estruturais (linhas cinza claro/ciano)
            ctx.lineWidth = 2;
            ctx.strokeStyle = 'rgba(143, 163, 204, 0.2)';
            
            // Coluna e tronco
            ctx.beginPath();
            ctx.moveTo(350, 120); ctx.lineTo(350, 310); // Coluna
            ctx.moveTo(310, 200); ctx.lineTo(390, 200); // Ombros
            ctx.moveTo(310, 200); ctx.lineTo(270, 270); // Braço esquerdo
            ctx.moveTo(390, 200); ctx.lineTo(430, 270); // Braço direito
            ctx.moveTo(310, 270); ctx.lineTo(350, 310); // Tronco inferior esq
            ctx.moveTo(390, 270); ctx.lineTo(350, 310); // Tronco inferior dir
            ctx.moveTo(350, 310); ctx.lineTo(320, 410); // Pelve ao fêmur esq
            ctx.moveTo(350, 310); ctx.lineTo(380, 410); // Pelve ao fêmur dir
            ctx.moveTo(320, 410); ctx.lineTo(300, 500); // Perna esq
            ctx.moveTo(380, 410); ctx.lineTo(400, 500); // Perna dir
            ctx.stroke();

            // Desenhar os nós (ossos/componentes)
            skeletonBones.forEach((bone, index) => {
                const isPrinted = (bone.y <= laserY && isRunning) || (progress >= 100) || (bone.y * 0.1 <= progress);
                
                ctx.beginPath();
                ctx.arc(bone.x, bone.y, 6, 0, Math.PI * 2);
                
                if (isPrinted || progress >= 100) {
                    ctx.fillStyle = '#00f3ff';
                    ctx.shadowColor = '#00f3ff';
                    ctx.shadowBlur = 10;
                } else {
                    ctx.fillStyle = '#223255';
                    ctx.shadowBlur = 0;
                }
                ctx.fill();
                ctx.shadowBlur = 0; // Resetar sombra
            });
        }

        function drawLaserAndParticles() {
            if (!isRunning && progress === 0) return;

            // Feixe laser horizontal da impressora 6D
            ctx.strokeStyle = 'rgba(189, 0, 255, 0.8)';
            ctx.lineWidth = 3;
            ctx.shadowColor = '#bd00ff';
            ctx.shadowBlur = 15;
            ctx.beginPath();
            ctx.moveTo(50, laserY);
            ctx.lineTo(650, laserY);
            ctx.stroke();
            ctx.shadowBlur = 0;

            // Atualizar e desenhar partículas de nanorrobôs
            if (isRunning) spawnParticles();

            particles.forEach((p, index) => {
                p.x += p.vx;
                p.y += p.vy;

                ctx.fillStyle = p.color;
                ctx.fillRect(p.x, p.y, p.size, p.size);

                // Remover partículas fora da tela
                if (p.y > canvas.height) {
                    particles.splice(index, 1);
                }
            });
        }

        function render() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            drawGrid();
            drawSkeleton();
            drawLaserAndParticles();
            
            updateSimulation();
            requestAnimationFrame(render);
        }

        // Iniciar loop de renderização
        render();
    </script>
</body>
</html>
