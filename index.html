<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Agrodefense - Equilíbrio</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Fredoka+One&family=Nunito:wght@700&display=swap');

        body {
            margin: 0; padding: 0;
            background-color: #2c3e50;
            color: white;
            font-family: 'Nunito', sans-serif;
            display: flex; flex-direction: column; align-items: center;
            user-select: none; touch-action: manipulation;
        }

        #game-wrapper {
            position: relative; margin-top: 10px;
            width: 98vw; max-width: 800px;
            box-shadow: 0 15px 30px rgba(0,0,0,0.6);
            border-radius: 15px; overflow: hidden;
            background-color: #2f3542;
        }

        #start-screen {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(135deg, #27ae60, #2ecc71);
            display: flex; flex-direction: column; align-items: center; justify-content: center;
            z-index: 100;
        }
        #start-screen h1 { font-family: 'Fredoka One', cursive; font-size: clamp(30px, 8vw, 60px); text-shadow: 4px 4px 0px #2c3e50; }
        #start-screen button { font-family: 'Fredoka One', cursive; font-size: 24px; padding: 15px 40px; background-color: #f1c40f; border: none; border-radius: 10px; cursor: pointer; box-shadow: 0 6px 0 #d4ac0d; }

        #ui-panel {
            display: grid; grid-template-columns: 1fr 1fr;
            background-color: #1e272e; padding: 10px;
            border-bottom: 4px solid #485460;
        }
        .stat { font-weight: bold; display: flex; align-items: center; gap: 5px; }
        .money-container { color: #f1c40f; transition: transform 0.1s; }
        
        .bump { animation: coinBump 0.3s ease-out; }
        @keyframes coinBump { 
            0% { transform: scale(1); } 
            50% { transform: scale(1.4); color: #fff; } 
            100% { transform: scale(1); } 
        }

        #game-area { position: relative; background-color: #7bed9f; }
        canvas { display: block; width: 100%; height: auto; }

        #plantation-base {
            position: absolute; right: 0; top: 10%;
            width: 70px; height: 180px;
            background-color: #8b4513; border-left: 5px solid #5c2c09;
            border-radius: 20px 0 0 20px;
            display: none; flex-wrap: wrap; align-content: center; justify-content: center;
            font-size: 25px; z-index: 5;
        }

        #controls {
            display: grid; grid-template-columns: 1fr 1fr; gap: 10px;
            padding: 10px; background-color: #1e272e;
        }
        .btn {
            background-color: #485460; color: white; border: 3px solid #808e9b;
            padding: 8px; border-radius: 8px; cursor: pointer;
            display: flex; flex-direction: column; align-items: center; font-size: 12px;
            position: relative; overflow: hidden;
        }
        .btn.active { border-color: #0be881; background-color: #05c46b; color: #1e272e; }
        
        .btn.cooldown { pointer-events: none; opacity: 0.6; filter: grayscale(0.5); }
        .cooldown-overlay {
            position: absolute; bottom: 0; left: 0; width: 100%; height: 0%;
            background: rgba(0,0,0,0.3); transition: height 0.1s linear;
        }

        .btn-danger { grid-column: span 2; background-color: #ff3f34; }

        #game-over {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); display: none;
            flex-direction: column; align-items: center; justify-content: center; z-index: 200;
        }
    </style>
</head>
<body>

    <div id="game-wrapper">
        <div id="start-screen">
            <h1>🌱 Agrodefense 🚜</h1>
            <button onclick="startGame()">JOGAR</button>
        </div>

        <div id="ui-panel">
            <div class="stat money-container" id="money-ui">💰 Moedas: <span id="money">20</span></div>
            <div class="stat" style="color:#00d8d6">🌊 Onda: <span id="wave">1</span>/25</div>
            <div class="stat" style="color:#ff5e57">❤️ HP: <span id="hp">100</span></div>
            <div class="stat" style="color:#0fb9b1">🌍 Espaço: <span id="space">100</span>%</div>
        </div>
        
        <div id="game-area">
            <canvas id="gameCanvas" width="800" height="500"></canvas>
            <div id="plantation-base">
                <div class="crop">🌽</div><div class="crop">🌾</div><div class="crop">🍅</div>
                <div class="crop">🥕</div><div class="crop">🌽</div><div class="crop">🌾</div>
            </div>
        </div>
        
        <div id="controls">
            <button class="btn active" onclick="selectTower('joaninha')" id="btn-joaninha">
                <span>🐞 Joaninha</span><small>HP: 2 | Custo: 0</small>
                <div class="cooldown-overlay" id="cd-joaninha"></div>
            </button>
            <button class="btn" onclick="selectTower('vespa')" id="btn-vespa">
                <span>🐝 Vespa</span><small>HP: 3 | Custo: 20</small>
            </button>
            <button class="btn" onclick="selectTower('sapo')" id="btn-sapo">
                <span>🐸 Sapo</span><small>HP: 5 | Custo: 50</small>
            </button>
            <button class="btn btn-danger" onclick="useAgrotoxico()">
                <span>☠️ Agrotóxico (Limpa Tudo)</span>
            </button>
        </div>

        <div id="game-over">
            <h1 id="end-message" style="color: #ff3f34; font-family: 'Fredoka One';">FIM DE JOGO</h1>
            <button onclick="location.reload()" style="padding: 10px 20px;">Recomeçar</button>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const uiMoney = document.getElementById('money');
        const uiMoneyContainer = document.getElementById('money-ui');
        const uiWave = document.getElementById('wave');
        const uiHp = document.getElementById('hp');
        const uiSpace = document.getElementById('space');
        const plantationHtml = document.getElementById('plantation-base');

        let money = 20, wave = 1, hp = 100, space = 100;
        let isPlaying = false, isGameOver = false, selectedTower = 'joaninha';
        let enemies = [], towers = [], enemiesToSpawn = [];
        let spawnTimer = 0, waveInProgress = false, frameCount = 0;

        let joaninhaReady = true;
        const JOANINHA_CD_TIME = 1500;

        const path = [
            {x: 0, y: 150}, {x: 250, y: 150}, {x: 250, y: 400},
            {x: 550, y: 400}, {x: 550, y: 150}, {x: 800, y: 150}
        ];

        const TOWER_TYPES = {
            joaninha: { cost: 0, damage: 8, hp: 2, emoji: '🐞', color: '#ff4757' },
            vespa: { cost: 20, damage: 60, hp: 3, emoji: '🐝', color: '#f1c40f' },
            sapo: { cost: 50, damage: 100, hp: 5, emoji: '🐸', color: '#2ecc71' }
        };

        const ENEMY_TYPES = {
            moscabranca: { hp: 20, speed: 1.4, reward: 5, emoji: '🦟', size: 15 }, // Ajustado para 5 moedas
            acaro: { hp: 150, speed: 1.8, reward: 10, emoji: '🕷️', size: 18 },
            pulgao: { hp: 600, speed: 1.1, reward: 15, emoji: '🐛', size: 24 },
            javali: { hp: 5000, speed: 0.7, reward: 505, emoji: '🐗', size: 50 }
        };

        window.startGame = () => {
            document.getElementById('start-screen').style.display = 'none';
            plantationHtml.style.display = 'flex';
            isPlaying = true;
            startWave();
            gameLoop();
        };

        function startWave() {
            if (isGameOver) return;
            waveInProgress = true;
            enemiesToSpawn = [];
            let count = 5 + (wave * 2);
            let type = wave <= 10 ? 'moscabranca' : wave <= 20 ? 'acaro' : 'pulgao';
            if (wave === 25) { enemiesToSpawn.push('javali'); count = 15; type = 'pulgao'; }
            for(let i=0; i<count; i++) enemiesToSpawn.push(type);
            uiWave.innerText = wave;
        }

        window.selectTower = (t) => {
            selectedTower = t;
            document.querySelectorAll('.btn').forEach(b => b.classList.remove('active'));
            document.getElementById('btn-' + t).classList.add('active');
        };

        canvas.addEventListener('mousedown', spawnDefender);
        canvas.addEventListener('touchstart', (e) => {
            e.preventDefault();
            spawnDefender();
        });

        function spawnDefender() {
            if (!isPlaying || isGameOver) return;
            if (selectedTower === 'joaninha' && !joaninhaReady) return;

            const tData = TOWER_TYPES[selectedTower];
            
            if (money >= tData.cost) {
                money -= tData.cost;
                updateMoneyUI();
                
                if (selectedTower === 'joaninha') startJoaninhaCooldown();

                const spawnPoint = path[path.length - 1];
                towers.push({ 
                    x: spawnPoint.x, 
                    y: spawnPoint.y, 
                    ...tData, 
                    currentHp: tData.hp,
                    maxHp: tData.hp,
                    targetIndex: path.length - 2, 
                    animOffset: Math.random() * 100 
                });
            }
        }

        function startJoaninhaCooldown() {
            joaninhaReady = false;
            const btn = document.getElementById('btn-joaninha');
            const overlay = document.getElementById('cd-joaninha');
            btn.classList.add('cooldown');
            
            let start = Date.now();
            let timer = setInterval(() => {
                let elapsed = Date.now() - start;
                let progress = (elapsed / JOANINHA_CD_TIME) * 100;
                overlay.style.height = (100 - progress) + "%";
                
                if (elapsed >= JOANINHA_CD_TIME) {
                    clearInterval(timer);
                    joaninhaReady = true;
                    btn.classList.remove('cooldown');
                    overlay.style.height = "0%";
                }
            }, 30);
        }

        window.useAgrotoxico = () => {
            if (space <= 20) return;
            space -= 20; uiSpace.innerText = space;
            enemies.forEach(e => {
                money += e.reward;
                e.hp = 0;
            });
            updateMoneyUI();
            document.getElementById('game-area').style.filter = 'hue-rotate(120deg) brightness(1.2)';
            setTimeout(() => document.getElementById('game-area').style.filter = '', 400);
        };

        function updateMoneyUI() {
            uiMoney.innerText = money;
            uiMoneyContainer.classList.remove('bump');
            void uiMoneyContainer.offsetWidth; 
            uiMoneyContainer.classList.add('bump');
        }

        function update() {
            if (isGameOver) return;
            frameCount++;

            if (waveInProgress && enemiesToSpawn.length > 0) {
                spawnTimer++;
                if (spawnTimer > 40) {
                    const type = enemiesToSpawn.shift();
                    const d = ENEMY_TYPES[type];
                    enemies.push({ ...d, x: path[0].x, y: path[0].y, targetIndex: 1, progress: 0, maxHp: d.hp });
                    spawnTimer = 0;
                }
            } else if (enemies.length === 0 && waveInProgress) {
                waveInProgress = false;
                wave++;
                if (wave > 25) win(); else setTimeout(startWave, 2000);
            }

            enemies.forEach((e, i) => {
                const target = path[e.targetIndex];
                const dist = Math.hypot(target.x - e.x, target.y - e.y);
                if (dist < e.speed) {
                    e.targetIndex++;
                    if (e.targetIndex >= path.length) {
                        hp -= (e.emoji === '🐗' ? 50 : 5);
                        uiHp.innerText = hp;
                        enemies.splice(i, 1);
                        if (hp <= 0) gameOver();
                    }
                } else {
                    e.x += (target.x - e.x) / dist * e.speed;
                    e.y += (target.y - e.y) / dist * e.speed;
                    e.progress += e.speed;
                }
                if (e.hp <= 0) {
                    money += e.reward;
                    updateMoneyUI();
                    enemies.splice(i, 1);
                }
            });

            for (let i = towers.length - 1; i >= 0; i--) {
                const t = towers[i];
                if (t.targetIndex < 0) { towers.splice(i, 1); continue; }

                const target = path[t.targetIndex];
                const dist = Math.hypot(target.x - t.x, target.y - t.y);
                const speed = 2.5;

                if (dist < speed) t.targetIndex--;
                else {
                    t.x += (target.x - t.x) / dist * speed;
                    t.y += (target.y - t.y) / dist * speed;
                }

                for (let j = enemies.length - 1; j >= 0; j--) {
                    const e = enemies[j];
                    if (Math.hypot(t.x - e.x, t.y - e.y) < 25) {
                        e.hp -= t.damage;
                        t.currentHp -= 1;
                        if (t.currentHp <= 0) { towers.splice(i, 1); break; }
                    }
                }
            }
        }

        function draw() {
            ctx.clearRect(0,0,800,500);
            ctx.strokeStyle = '#c28d57'; ctx.lineWidth = 50; ctx.lineCap = 'round'; ctx.lineJoin = 'round';
            ctx.beginPath(); ctx.moveTo(path[0].x, path[0].y);
            path.forEach(p => ctx.lineTo(p.x, p.y)); ctx.stroke();

            towers.forEach(t => {
                const bounce = Math.sin((frameCount + t.animOffset) * 0.2) * 4;
                ctx.save();
                ctx.globalAlpha = 0.4 + (0.6 * (t.currentHp / t.maxHp));
                ctx.font = '40px Arial'; ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
                ctx.fillText(t.emoji, t.x, t.y + bounce);
                ctx.restore();
            });

            enemies.forEach(e => {
                ctx.font = (e.size * 2) + 'px Arial'; ctx.textAlign = 'center';
                ctx.fillText(e.emoji, e.x, e.y + 10);
                ctx.fillStyle = 'red'; ctx.fillRect(e.x - 15, e.y - 35, 30, 4);
                ctx.fillStyle = '#2ecc71'; ctx.fillRect(e.x - 15, e.y - 35, 30 * (e.hp/e.maxHp), 4);
            });
        }

        function gameLoop() {
            update(); draw();
            if(!isGameOver) requestAnimationFrame(gameLoop);
        }

        function gameOver() { isGameOver = true; document.getElementById('game-over').style.display = 'flex'; }
        function win() { isGameOver = true; document.getElementById('end-message').innerText = "VITÓRIA!"; gameOver(); }
    </script>
</body>
</html>
