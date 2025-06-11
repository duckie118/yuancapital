<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>元木资本 - Crypto 投资计划</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
    <!-- Color Palette: Energetic & Playful -->
    <!-- Confirmation: NEITHER Mermaid JS NOR SVG were used in this file. All diagrams are built with HTML/CSS and all charts are rendered on Canvas by Chart.js. -->
    <style>
        body {
            font-family: 'Noto Sans SC', sans-serif;
            background-color: #f0f2f5;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }
        @media (max-width: 768px) {
            .chart-container {
                height: 300px;
                max-height: 350px;
            }
        }
        .kpi-card {
            background-color: white;
            border-radius: 0.75rem;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
            border-left: 5px solid #0078F6;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .kpi-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -2px rgb(0 0 0 / 0.1);
        }
        .flowchart-node {
            border: 2px solid #6000F6;
            background-color: #ffffff;
            color: #1f2937;
        }
        .flowchart-line {
            background-color: #6000F6;
            height: 2px;
            width: 100%;
        }
        .flowchart-line-v {
            background-color: #6000F6;
            width: 2px;
            height: 100%;
        }
        .modal {
            display: none;
            position: fixed;
            z-index: 100;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.4);
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: #fefefe;
            margin: auto;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 700px;
            position: relative;
        }
        .close-button {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close-button:hover,
        .close-button:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
        .spinner {
            border: 4px solid rgba(0, 0, 0, 0.1);
            border-left-color: #0078F6;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="bg-gray-100 text-gray-800">

    <main class="container mx-auto p-4 md:p-8">

        <header class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold text-gray-900">元木资本 Crypto 投资计划</h1>
            <p class="text-xl text-gray-600 mt-2">一份面向未来的战略、风险与回报分析</p>
        </header>

        <section id="objective" class="mb-16">
             <div class="bg-white rounded-xl shadow-2xl p-8 md:p-12 border-t-8 border-cyan-400" style="--tw-border-opacity: 1; border-color: #00F6F6;">
                <p class="text-2xl font-semibold text-gray-700 text-center">核心投资目标</p>
                <div class="text-center text-7xl md:text-8xl font-extrabold my-4" style="color: #0078F6;">
                    35%
                </div>
                <p class="text-2xl font-semibold text-gray-700 text-center">净年化收益率 (Net APY)</p>
                <p class="text-center text-gray-500 mt-4 max-w-2xl mx-auto">我们的首要目标是为流动性资产实现卓越的净回报，通过精心设计的多元化策略组合，在可控风险下追求最大化收益。</p>
            </div>
        </section>
        
        <section id="strategy-allocation" class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-4">战略资产配置</h2>
            <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">我们的投资组合构建于两大基石之上：稳健的市场中性策略和高增长潜力的趋势策略。这种平衡的配置旨在捕捉不同市场环境下的机会，同时平滑整体回报曲线。</p>
            <div class="grid grid-cols-1 md:grid-cols-5 gap-8 items-center">
                <div class="md:col-span-2">
                    <div class="chart-container mx-auto h-[400px] md:h-[450px]">
                        <canvas id="strategySplitChart"></canvas>
                    </div>
                </div>
                <div class="md:col-span-3">
                    <div class="space-y-6">
                        <div>
                            <h3 class="font-bold text-xl mb-2 text-gray-800">市场中性策略 (Market Neutral)</h3>
                            <p class="text-gray-600 mb-4">这类策略旨在剥离市场方向性风险 (Beta)，赚取纯粹的超额收益 (Alpha)。它们是我们投资组合的稳定器。</p>
                            <div class="chart-container h-[250px]">
                                <canvas id="marketNeutralChart"></canvas>
                            </div>
                        </div>
                         <div>
                            <h3 class="font-bold text-xl mb-2 text-gray-800">趋势策略 (Trend)</h3>
                            <p class="text-gray-600 mb-4">通过捕捉市场的主要动能和趋势来获取回报。这是我们投资组合的增长引擎，目标是在明确的市场方向中获得高额回报。</p>
                            <div class="chart-container h-[250px]">
                                 <canvas id="trendChart"></canvas>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="market-landscape" class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-4">加密市场格局分析</h2>
             <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">了解我们所处的生态系统至关重要。我们深入分析了市场上各类参与者的资产管理规模（AUM）分布，以及不同资金体量下典型的特殊目的公司（SPC）结构。</p>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div class="bg-white rounded-lg shadow-md p-6">
                    <h3 class="text-xl font-bold text-center mb-4">交易团队 AUM 分布</h3>
                    <p class="text-center text-sm text-gray-500 mb-4">下图展示了市场上不同规模交易团队的数量，揭示了行业内由少数巨头和大量中小型团队构成的金字塔结构。</p>
                    <div class="chart-container">
                        <canvas id="aumDistributionChart"></canvas>
                    </div>
                </div>
                <div class="bg-white rounded-lg shadow-md p-6">
                    <h3 class="text-xl font-bold text-center mb-4">SPC 结构资金分配</h3>
                    <p class="text-center text-sm text-gray-500 mb-4">根据资金规模的不同，SPC的资产配置比例也有所侧重。中等规模（2000万至2亿）的资金是市场的中坚力量。</p>
                    <div class="chart-container">
                        <canvas id="spcStructureChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <section id="trading-strategies" class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-4">核心交易策略矩阵</h2>
            <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">我们将采用一个多元化的策略矩阵，结合多种经过市场验证的交易方法，以适应不同的市场条件并分散风险。点击 ✨ 按钮获取AI解释！</p>
            <div class="flex flex-col items-center">
                <div class="flowchart-node font-bold py-3 px-6 rounded-lg shadow-lg mb-4">核心策略库</div>
                <div class="w-full flex justify-center mb-4">
                     <div class="flowchart-line-v h-8"></div>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-8 gap-y-12 w-full relative">
                    <div class="absolute top-1/2 left-0 w-full h-0.5 bg-purple-400 -translate-y-1/2 hidden lg:block"></div>
                    <div class="flex flex-col items-center text-center">
                        <div class="flowchart-node rounded-lg p-4 w-full max-w-xs shadow-md">
                            <h4 class="font-bold text-lg mb-2">套利策略</h4>
                            <p class="text-sm">跨交易所价差、资金费率、统计套利</p>
                            <button class="mt-4 bg-purple-600 text-white px-4 py-2 rounded-md shadow-md hover:bg-purple-700 transition duration-300" onclick="getStrategyExplanation('套利策略')">✨ 了解更多</button>
                        </div>
                    </div>
                    <div class="flex flex-col items-center text-center">
                        <div class="flowchart-node rounded-lg p-4 w-full max-w-xs shadow-md">
                            <h4 class="font-bold text-lg mb-2">趋势跟踪</h4>
                            <p class="text-sm">CTA / 动量策略</p>
                            <button class="mt-4 bg-purple-600 text-white px-4 py-2 rounded-md shadow-md hover:bg-purple-700 transition duration-300" onclick="getStrategyExplanation('趋势跟踪')">✨ 了解更多</button>
                        </div>
                    </div>
                    <div class="flex flex-col items-center text-center">
                        <div class="flowchart-node rounded-lg p-4 w-full max-w-xs shadow-md">
                            <h4 class="font-bold text-lg mb-2">做市策略</h4>
                            <p class="text-sm">提供流动性</p>
                            <button class="mt-4 bg-purple-600 text-white px-4 py-2 rounded-md shadow-md hover:bg-purple-700 transition duration-300" onclick="getStrategyExplanation('做市策略')">✨ 了解更多</button>
                        </div>
                    </div>
                     <div class="flex flex-col items-center text-center">
                        <div class="flowchart-node rounded-lg p-4 w-full max-w-xs shadow-md">
                            <h4 class="font-bold text-lg mb-2">波动率套利</h4>
                            <p class="text-sm">期权组合策略</p>
                            <button class="mt-4 bg-purple-600 text-white px-4 py-2 rounded-md shadow-md hover:bg-purple-700 transition duration-300" onclick="getStrategyExplanation('波动率套利')">✨ 了解更多</button>
                        </div>
                    </div>
                     <div class="flex flex-col items-center text-center">
                        <div class="flowchart-node rounded-lg p-4 w-full max-w-xs shadow-md">
                            <h4 class="font-bold text-lg mb-2">多空对冲</h4>
                            <p class="text-sm">市场中性</p>
                            <button class="mt-4 bg-purple-600 text-white px-4 py-2 rounded-md shadow-md hover:bg-purple-700 transition duration-300" onclick="getStrategyExplanation('多空对冲')">✨ 了解更多</button>
                        </div>
                    </div>
                     <div class="flex flex-col items-center text-center">
                        <div class="flowchart-node rounded-lg p-4 w-full max-w-xs shadow-md">
                            <h4 class="font-bold text-lg mb-2">复合策略</h4>
                            <p class="text-sm">混合 Alpha + Beta</p>
                            <button class="mt-4 bg-purple-600 text-white px-4 py-2 rounded-md shadow-md hover:bg-purple-700 transition duration-300" onclick="getStrategyExplanation('复合策略')">✨ 了解更多</button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="kpis-risk" class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-4">绩效指标与风险控制</h2>
            <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">我们设定了严格的绩效目标和风险管理红线，以确保投资组合在追求高回报的同时，始终保持稳健和可控。</p>
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                <div class="kpi-card">
                    <p class="text-gray-500 font-semibold">年化收益率 (APY)</p>
                    <p class="text-4xl font-bold my-2" style="color: #0078F6;">&ge;20%</p>
                </div>
                <div class="kpi-card">
                    <p class="text-gray-500 font-semibold">夏普比率 (Sharpe Ratio)</p>
                    <p class="text-4xl font-bold my-2" style="color: #0078F6;">&ge;2</p>
                </div>
                 <div class="kpi-card" style="border-color: #F60078;">
                    <p class="text-gray-500 font-semibold">最大回撤 (Overall)</p>
                    <p class="text-4xl font-bold my-2" style="color: #F60078;">&le;10%</p>
                </div>
                <div class="kpi-card" style="border-color: #F68400;">
                    <p class="text-gray-500 font-semibold">最大杠杆</p>
                    <p class="text-4xl font-bold my-2" style="color: #F68400;">&le;5x</p>
                </div>
            </div>
        </section>

        <section id="team-requirements" class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-4">合作团队筛选标准</h2>
            <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">我们将与市场上最顶尖的交易团队合作。以下是我们严格的筛选标准，确保我们的合作伙伴拥有卓越的能力和良好的信誉。</p>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 text-center">
                <div class="bg-white rounded-lg shadow-md p-6">
                    <div class="text-4xl mb-3" style="color: #6000F6;">📅</div>
                    <h4 class="font-bold text-lg">实盘经验</h4>
                    <p class="text-gray-600">&ge;3 年</p>
                </div>
                <div class="bg-white rounded-lg shadow-md p-6">
                    <div class="text-4xl mb-3" style="color: #6000F6;">📈</div>
                    <h4 class="font-bold text-lg">完整业绩记录</h4>
                    <p class="text-gray-600">&ge;2 个市场周期</p>
                </div>
                 <div class="bg-white rounded-lg shadow-md p-6">
                    <div class="text-4xl mb-3" style="color: #6000F6;">🌏</div>
                    <h4 class="font-bold text-lg">团队背景</h4>
                    <p class="text-gray-600">优先亚洲团队 (3/4)</p>
                </div>
                <div class="bg-white rounded-lg shadow-md p-6">
                    <div class="text-4xl mb-3" style="color: #6000F6;">🔒</div>
                    <h4 class="font-bold text-lg">透明度与托管</h4>
                    <p class="text-gray-600">提供托管方案和透明报告</p>
                </div>
            </div>
        </section>
        
        <section id="deployment-plan" class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-4">初步配置建议</h2>
            <p class="text-center text-gray-600 max-w-3xl mx-auto mb-8">我们建议从一个精简的配置开始，通过独立管理账户（SMA）和基金两种形式，小步快跑，逐步建立我们的投资组合。</p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                 <div class="bg-gradient-to-br from-blue-500 to-indigo-600 text-white rounded-xl shadow-lg p-8 text-center">
                    <h3 class="text-2xl font-bold">独立管理账户 (SMA)</h3>
                    <p class="mt-2 mb-4">直接控制，更高透明度</p>
                    <p class="text-4xl font-extrabold">2 个团队</p>
                    <p class="text-lg mt-2">每团队 $30万 - $50万 美金</p>
                </div>
                 <div class="bg-gradient-to-br from-cyan-400 to-teal-500 text-white rounded-xl shadow-lg p-8 text-center">
                    <h3 class="text-2xl font-bold">投资基金 (Fund)</h3>
                    <p class="mt-2 mb-4">分散风险，配置更便捷</p>
                    <p class="text-4xl font-extrabold">1-2 个基金</p>
                    <p class="text-lg mt-2">每基金 $10万 - $20万 美金</p>
                </div>
            </div>
        </section>

    </main>
    
    <footer class="text-center p-4 bg-gray-800 text-gray-400">
        <p>&copy; 2025 元木资本。保留所有权利。</p>
    </footer>

    <!-- Strategy Explanation Modal -->
    <div id="strategyModal" class="modal">
        <div class="modal-content">
            <span class="close-button" onclick="document.getElementById('strategyModal').style.display='none'">&times;</span>
            <h3 id="modalTitle" class="text-2xl font-bold mb-4 text-gray-900"></h3>
            <div id="modalSpinner" class="spinner"></div>
            <div id="modalContent" class="text-gray-700 leading-relaxed max-h-96 overflow-y-auto"></div>
        </div>
    </div>

    <script>
        const vibrantPalette = ['#00F6F6', '#0078F6', '#6000F6', '#F60078', '#F68400', '#F6C600'];
        const tooltipTitleCallback = {
            plugins: {
                tooltip: {
                    callbacks: {
                        title: function(tooltipItems) {
                            const item = tooltipItems[0];
                            let label = item.chart.data.labels[item.dataIndex];
                            if (Array.isArray(label)) {
                              return label.join(' ');
                            } else {
                              return label;
                            }
                        }
                    }
                },
                legend: {
                     position: 'bottom',
                     labels: {
                        color: '#4b5563',
                        font: {
                            size: 14
                        }
                     }
                }
            }
        };

        function wrapLabel(label) {
            const maxLength = 16;
            if (typeof label !== 'string' || label.length <= maxLength) {
                return label;
            }
            const words = label.split(' ');
            const lines = [];
            let currentLine = '';
            for (const word of words) {
                if ((currentLine + ' ' + word).trim().length > maxLength) {
                    lines.push(currentLine.trim());
                    currentLine = word;
                } else {
                    currentLine = (currentLine + ' ' + word).trim();
                }
            }
            if (currentLine) {
                lines.push(currentLine.trim());
            }
            return lines;
        }

        const strategySplitCtx = document.getElementById('strategySplitChart').getContext('2d');
        new Chart(strategySplitCtx, {
            type: 'doughnut',
            data: {
                labels: ['市场中性策略', '趋势策略'],
                datasets: [{
                    label: '策略大类配置',
                    data: [55, 45],
                    backgroundColor: [vibrantPalette[1], vibrantPalette[0]],
                    borderColor: '#ffffff',
                    borderWidth: 4,
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                cutout: '70%',
                plugins: tooltipTitleCallback.plugins
            }
        });
        
        const marketNeutralCtx = document.getElementById('marketNeutralChart').getContext('2d');
        new Chart(marketNeutralCtx, {
            type: 'bar',
            data: {
                labels: ['HFT MM+套利', 'DeFi', 'MFT 套利'],
                datasets: [{
                    label: '目标回报 (%)',
                    data: [30, 20, 10],
                    backgroundColor: [vibrantPalette[2], vibrantPalette[3], vibrantPalette[4]],
                    borderRadius: 4,
                }]
            },
            options: {
                indexAxis: 'y',
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        beginAtZero: true,
                        title: { display: true, text: '目标回报 (%)' }
                    }
                },
                plugins: tooltipTitleCallback.plugins
            }
        });

        const trendCtx = document.getElementById('trendChart').getContext('2d');
        new Chart(trendCtx, {
            type: 'bar',
            data: {
                labels: ['趋势/动量'],
                datasets: [{
                    label: '目标回报范围 (%)',
                    data: [[40, 50]],
                    backgroundColor: [vibrantPalette[0]],
                    borderRadius: 4,
                }]
            },
            options: {
                 indexAxis: 'y',
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    x: {
                        beginAtZero: true,
                        title: { display: true, text: '目标回报 (%)' }
                    }
                },
                plugins: tooltipTitleCallback.plugins
            }
        });

        const aumDistributionCtx = document.getElementById('aumDistributionChart').getContext('2d');
        const aumLabels = ['10亿+ 美金', '5-10亿 美金', '2-5亿 美金', '2亿以下 美金'].map(wrapLabel);
        new Chart(aumDistributionCtx, {
            type: 'bar',
            data: {
                labels: aumLabels,
                datasets: [{
                    label: '团队数量',
                    data: [1, 3, 10, 20],
                    backgroundColor: vibrantPalette.slice(0, 4),
                    borderColor: vibrantPalette.slice(0, 4),
                    borderWidth: 1,
                    borderRadius: 4,
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    y: {
                        beginAtZero: true,
                         title: { display: true, text: '团队数量' }
                    }
                },
                plugins: tooltipTitleCallback.plugins
            }
        });
        
        const spcStructureCtx = document.getElementById('spcStructureChart').getContext('2d');
        const spcLabels = ['2亿+ 美金', '5000万-2亿 美金', '2000万-5000万 美金', '2000万以下 美金'].map(wrapLabel);
        new Chart(spcStructureCtx, {
            type: 'pie',
            data: {
                labels: spcLabels,
                datasets: [{
                    label: '资金分配比例',
                    data: [15, 35, 35, 15],
                    backgroundColor: [vibrantPalette[0], vibrantPalette[1], vibrantPalette[2], vibrantPalette[3]],
                    borderColor: '#ffffff',
                    borderWidth: 2,
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: tooltipTitleCallback.plugins
            }
        });

        async function getStrategyExplanation(strategyName) {
            const modal = document.getElementById('strategyModal');
            const modalTitle = document.getElementById('modalTitle');
            const modalContent = document.getElementById('modalContent');
            const modalSpinner = document.getElementById('modalSpinner');

            modalTitle.textContent = `${strategyName} 策略详解`;
            modalContent.innerHTML = '';
            modalSpinner.style.display = 'block';
            modal.style.display = 'flex';

            let prompt = `请详细解释加密货币投资中的 "${strategyName}" 策略，包括其原理、常见类型、风险和收益特点，用中文回答，内容应简洁明了，适合作为信息图表的一部分。`;

            let chatHistory = [];
            chatHistory.push({ role: "user", parts: [{ text: prompt }] });
            const payload = { contents: chatHistory };
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

            try {
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const text = result.candidates[0].content.parts[0].text;
                    modalContent.innerHTML = text.replace(/\n/g, '<br>');
                } else {
                    modalContent.textContent = '无法获取策略解释，请稍后再试。';
                }
            } catch (error) {
                modalContent.textContent = '请求失败，请检查网络连接或稍后再试。';
                console.error('Gemini API call failed:', error);
            } finally {
                modalSpinner.style.display = 'none';
            }
        }
    </script>
</body>
</html>
