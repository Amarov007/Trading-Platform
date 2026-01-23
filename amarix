<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AMARX | Advanced Cryptocurrency Exchange</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/d3@7"></script>
    <script src="https://unpkg.com/recharts"></script>
    <script src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
        }
        body {
            background: #0a0b0d;
            color: #f0f0f0;
            overflow-x: hidden;
        }
        .gradient-bg {
            background: linear-gradient(135deg, #0a0b0d 0%, #131722 50%, #1a1f2e 100%);
        }
        .hero-gradient {
            background: radial-gradient(circle at 50% 0%, rgba(45, 65, 255, 0.15), transparent 50%);
        }
        .card-gradient {
            background: linear-gradient(145deg, rgba(30, 33, 45, 0.8), rgba(20, 22, 30, 0.9));
            border: 1px solid rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(10px);
        }
        .btn-primary {
            background: linear-gradient(90deg, #2d41ff, #6c72ff);
            color: white;
            font-weight: 600;
            padding: 12px 28px;
            border-radius: 10px;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(45, 65, 255, 0.3);
        }
        .nav-link {
            color: #a0a0b0;
            transition: color 0.3s;
        }
        .nav-link:hover {
            color: #ffffff;
        }
        .chart-container {
            background: rgba(15, 17, 26, 0.8);
            border-radius: 16px;
            padding: 20px;
        }
        .glow {
            box-shadow: 0 0 40px rgba(45, 65, 255, 0.1);
        }
        .feature-icon {
            background: linear-gradient(135deg, rgba(45, 65, 255, 0.2), rgba(108, 114, 255, 0.1));
            border-radius: 14px;
            padding: 16px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }
        .ticker {
            background: rgba(20, 22, 30, 0.9);
            border-top: 1px solid rgba(255, 255, 255, 0.05);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }
        .mobile-menu {
            transform: translateX(100%);
            transition: transform 0.4s ease;
        }
        .mobile-menu.open {
            transform: translateX(0);
        }
        .number-counter {
            font-weight: 700;
            background: linear-gradient(90deg, #ffffff, #a0a0ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .security-ring {
            animation: rotate 20s linear infinite;
        }
        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .pulse {
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
    </style>
</head>
<body class="gradient-bg">
    <!-- Navigation -->
    <nav class="sticky top-0 z-50 card-gradient py-4 px-6 lg:px-12">
        <div class="container mx-auto flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="w-10 h-10 rounded-lg bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center font-bold text-xl">A</div>
                <span class="text-2xl font-bold bg-gradient-to-r from-blue-400 to-purple-300 bg-clip-text text-transparent">AMARX</span>
            </div>
            <div class="hidden md:flex items-center space-x-8">
                <a href="#features" class="nav-link">Features</a>
                <a href="#trading" class="nav-link">Trading</a>
                <a href="#security" class="nav-link">Security</a>
                <a href="#infrastructure" class="nav-link">Infrastructure</a>
                <button class="btn-primary">Launch Exchange</button>
            </div>
            <button id="menuBtn" class="md:hidden text-gray-300">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                </svg>
            </button>
        </div>
        <div id="mobileMenu" class="mobile-menu fixed top-0 right-0 h-full w-64 card-gradient p-6">
            <div class="flex justify-between items-center mb-10">
                <div class="flex items-center space-x-2">
                    <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center font-bold">A</div>
                    <span class="text-xl font-bold">AMARX</span>
                </div>
                <button id="closeMenu" class="text-gray-300">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </div>
            <div class="flex flex-col space-y-6">
                <a href="#features" class="nav-link text-lg">Features</a>
                <a href="#trading" class="nav-link text-lg">Trading</a>
                <a href="#security" class="nav-link text-lg">Security</a>
                <a href="#infrastructure" class="nav-link text-lg">Infrastructure</a>
                <button class="btn-primary mt-4">Launch Exchange</button>
            </div>
        </div>
    </nav>

    <!-- Live Ticker -->
    <div class="ticker py-3 overflow-hidden">
        <div id="tickerContent" class="flex space-x-12 whitespace-nowrap"></div>
    </div>

    <!-- Hero -->
    <section class="hero-gradient py-20 px-6 lg:px-12">
        <div class="container mx-auto max-w-6xl text-center">
            <h1 class="text-5xl lg:text-7xl font-bold mb-6 leading-tight">
                <span class="bg-gradient-to-r from-blue-300 via-white to-purple-300 bg-clip-text text-transparent">Professional-Grade</span><br/>
                <span>Crypto Trading Platform</span>
            </h1>
            <p class="text-xl text-gray-300 mb-10 max-w-3xl mx-auto">
                AMARX delivers cutting-edge trading tools, institutional-grade security, and ultra-low latency infrastructure for traders worldwide.
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                <button class="btn-primary glow">Start Trading Now</button>
                <button class="px-8 py-3 rounded-lg border border-gray-700 text-gray-300 hover:border-blue-500 hover:text-white transition">Explore Features</button>
            </div>
            <div class="mt-20 grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="text-center">
                    <div class="text-5xl number-counter mb-2" id="volumeCounter">0</div>
                    <p class="text-gray-400">24h Trading Volume</p>
                </div>
                <div class="text-center">
                    <div class="text-5xl number-counter mb-2" id="usersCounter">0</div>
                    <p class="text-gray-400">Active Traders</p>
                </div>
                <div class="text-center">
                    <div class="text-5xl number-counter mb-2" id="coinsCounter">0</div>
                    <p class="text-gray-400">Supported Assets</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Features -->
    <section id="features" class="py-20 px-6 lg:px-12">
        <div class="container mx-auto max-w-6xl">
            <h2 class="text-4xl font-bold text-center mb-16">Comprehensive Exchange <span class="text-blue-400">Features</span></h2>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div class="card-gradient p-8 rounded-2xl">
                    <div class="feature-icon mb-6">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Advanced Trading Tools</h3>
                    <p class="text-gray-400">Spot, futures, and margin trading with advanced order types, depth charts, and real-time analytics.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl">
                    <div class="feature-icon mb-6">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-green-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Multi-Layer Security</h3>
                    <p class="text-gray-400">Cold wallet storage, 2FA, biometric login, DDoS protection, and institutional-grade encryption.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl">
                    <div class="feature-icon mb-6">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">High Performance</h3>
                    <p class="text-gray-400">Scalable backend with sub-10ms latency, capable of processing 100K+ transactions per second.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl">
                    <div class="feature-icon mb-6">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-yellow-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">Regulatory Compliance</h3>
                    <p class="text-gray-400">Full KYC/AML verification, audit trails, and compliance with global regulatory standards.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl">
                    <div class="feature-icon mb-6">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-red-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.192l-3.536 3.536M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-5 0a4 4 0 11-8 0 4 4 0 018 0z" />
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">24/7 Support</h3>
                    <p class="text-gray-400">Multilingual customer support via live chat, ticketing, and comprehensive knowledge base.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl">
                    <div class="feature-icon mb-6">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-indigo-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4">API & Integration</h3>
                    <p class="text-gray-400">REST & WebSocket APIs for algorithmic trading, wallet integration, and custom solutions.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Trading Interface Preview -->
    <section id="trading" class="py-20 px-6 lg:px-12">
        <div class="container mx-auto max-w-6xl">
            <h2 class="text-4xl font-bold text-center mb-16">Professional <span class="text-blue-400">Trading Interface</span></h2>
            <div class="chart-container glow mb-8">
                <div class="h-80" id="tradingChart"></div>
            </div>
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <div class="card-gradient p-6 rounded-xl">
                    <h4 class="text-xl font-bold mb-4">Spot Trading</h4>
                    <p class="text-gray-400 mb-4">Trade cryptocurrencies instantly with competitive fees and deep liquidity.</p>
                    <ul class="space-y-2 text-gray-300">
                        <li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-3"></span>Limit, Market, Stop Orders</li>
                        <li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-3"></span>Real-time Order Book</li>
                        <li class="flex items-center"><span class="w-2 h-2 bg-blue-500 rounded-full mr-3"></span>Advanced Charting Tools</li>
                    </ul>
                </div>
                <div class="card-gradient p-6 rounded-xl">
                    <h4 class="text-xl font-bold mb-4">Futures & Margin</h4>
                    <p class="text-gray-400 mb-4">Leverage up to 100x with isolated/isolated margin and risk management.</p>
                    <ul class="space-y-2 text-gray-300">
                        <li class="flex items-center"><span class="w-2 h-2 bg-green-500 rounded-full mr-3"></span>Cross & Isolated Margin</li>
                        <li class="flex items-center"><span class="w-2 h-2 bg-green-500 rounded-full mr-3"></span>Liquidation Protection</li>
                        <li class="flex items-center"><span class="w-2 h-2 bg-green-500 rounded-full mr-3"></span>Funding Rate Alerts</li>
                    </ul>
                </div>
                <div class="card-gradient p-6 rounded-xl">
                    <h4 class="text-xl font-bold mb-4">Additional Services</h4>
                    <p class="text-gray-400 mb-4">Staking, lending, and referral programs for earning passive income.</p>
                    <ul class="space-y-2 text-gray-300">
                        <li class="flex items-center"><span class="w-2 h-2 bg-purple-500 rounded-full mr-3"></span>Staking & Yield Farming</li>
                        <li class="flex items-center"><span class="w-2 h-2 bg-purple-500 rounded-full mr-3"></span>Crypto Wallet Integration</li>
                        <li class="flex items-center"><span class="w-2 h-2 bg-purple-500 rounded-full mr-3"></span>Referral Commission Program</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- Security Visualization -->
    <section id="security" class="py-20 px-6 lg:px-12">
        <div class="container mx-auto max-w-6xl">
            <h2 class="text-4xl font-bold text-center mb-16">Enterprise <span class="text-green-400">Security Architecture</span></h2>
            <div class="flex flex-col lg:flex-row items-center">
                <div class="lg:w-1/2 mb-12 lg:mb-0">
                    <div class="relative w-64 h-64 mx-auto">
                        <div class="absolute inset-0 security-ring border-4 border-transparent border-t-green-500 border-r-blue-500 rounded-full"></div>
                        <div class="absolute inset-8 security-ring border-4 border-transparent border-t-purple-500 border-r-yellow-500 rounded-full" style="animation-direction: reverse;"></div>
                        <div class="absolute inset-16 pulse bg-gradient-to-br from-green-900/20 to-blue-900/20 rounded-full flex items-center justify-center">
                            <div class="text-center">
                                <div class="text-3xl font-bold">99.9%</div>
                                <div class="text-gray-400">Funds Secured</div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="lg:w-1/2 space-y-8">
                    <div class="card-gradient p-6 rounded-xl">
                        <h4 class="text-xl font-bold mb-3 flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-green-400 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
                            </svg>
                            Cold Wallet Storage
                        </h4>
                        <p class="text-gray-400">95% of digital assets stored in offline, multi-signature cold wallets with geographical distribution.</p>
                    </div>
                    <div class="card-gradient p-6 rounded-xl">
                        <h4 class="text-xl font-bold mb-3 flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-400 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z" />
                            </svg>
                            Multi-Factor Authentication
                        </h4>
                        <p class="text-gray-400">2FA, biometric verification, and hardware key support for all account actions and withdrawals.</p>
                    </div>
                    <div class="card-gradient p-6 rounded-xl">
                        <h4 class="text-xl font-bold mb-3 flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-purple-400 mr-3" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4" />
                            </svg>
                            DDoS Protection
                        </h4>
                        <p class="text-gray-400">Advanced distributed denial-of-service protection with automatic scaling and traffic filtering.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Infrastructure -->
    <section id="infrastructure" class="py-20 px-6 lg:px-12">
        <div class="container mx-auto max-w-6xl">
            <h2 class="text-4xl font-bold text-center mb-16">High-Performance <span class="text-purple-400">Infrastructure</span></h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="card-gradient p-8 rounded-2xl text-center">
                    <div class="text-5xl font-bold text-purple-400 mb-4">&lt;10ms</div>
                    <h3 class="text-2xl font-bold mb-4">Ultra-Low Latency</h3>
                    <p class="text-gray-400">Matching engine latency under 10 milliseconds for high-frequency trading.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl text-center">
                    <div class="text-5xl font-bold text-blue-400 mb-4">100K+</div>
                    <h3 class="text-2xl font-bold mb-4">TPS Capacity</h3>
                    <p class="text-gray-400">Scalable architecture handling over 100,000 transactions per second.</p>
                </div>
                <div class="card-gradient p-8 rounded-2xl text-center">
                    <div class="text-5xl font-bold text-green-400 mb-4">99.99%</div>
                    <h3 class="text-2xl font-bold mb-4">Uptime SLA</h3>
                    <p class="text-gray-400">Enterprise-grade reliability with 99.99% uptime service level agreement.</p>
                </div>
            </div>
            <div class="mt-16 card-gradient p-8 rounded-2xl">
                <h3 class="text-2xl font-bold mb-6">Global Server Distribution</h3>
                <div class="h-64" id="serverMap"></div>
                <p class="text-gray-400 mt-6">AMARX operates across multiple global regions with redundant data centers for optimal performance worldwide.</p>
            </div>
        </div>
    </section>

    <!-- CTA -->
    <section class="py-20 px-6 lg:px-12">
        <div class="container mx-auto max-w-4xl text-center card-gradient py-16 px-8 rounded-3xl">
            <h2 class="text-4xl font-bold mb-6">Ready to Trade Like a Pro?</h2>
            <p class="text-xl text-gray-300 mb-10">Join thousands of traders who trust AMARX for secure, advanced cryptocurrency trading.</p>
            <div class="flex flex-col sm:flex-row gap-6 justify-center">
                <button class="btn-primary glow px-10 py-4 text-lg">Create Free Account</button>
                <button class="px-10 py-4 text-lg rounded-lg border border-gray-700 text-gray-300 hover:border-blue-500 hover:text-white transition">Request Demo</button>
            </div>
            <p class="text-gray-500 mt-10 text-sm">No credit card required • 30-day free trial • 24/7 support</p>
        </div>
    </section>

    <!-- Footer -->
    <footer class="border-t border-gray-900 py-12 px-6 lg:px-12">
        <div class="container mx-auto max-w-6xl">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="mb-8 md:mb-0">
                    <div class="flex items-center space-x-2 mb-4">
                        <div class="w-10 h-10 rounded-lg bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center font-bold text-xl">A</div>
                        <span class="text-2xl font-bold">AMARX</span>
                    </div>
                    <p class="text-gray-500 max-w-md">Professional cryptocurrency exchange platform offering advanced trading tools, institutional security, and lightning-fast execution.</p>
                </div>
                <div class="grid grid-cols-2 md:grid-cols-3 gap-8">
                    <div>
                        <h4 class="font-bold text-lg mb-4">Platform</h4>
                        <ul class="space-y-2 text-gray-500">
                            <li><a href="#" class="hover:text-white transition">Spot Trading</a></li>
                            <li><a href="#" class="hover:text-white transition">Futures</a></li>
                            <li><a href="#" class="hover:text-white transition">Margin Trading</a></li>
                            <li><a href="#" class="hover:text-white transition">Staking</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold text-lg mb-4">Resources</h4>
                        <ul class="space-y-2 text-gray-500">
                            <li><a href="#" class="hover:text-white transition">API Documentation</a></li>
                            <li><a href="#" class="hover:text-white transition">Help Center</a></li>
                            <li><a href="#" class="hover:text-white transition">Blog</a></li>
                            <li><a href="#" class="hover:text-white transition">Status</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold text-lg mb-4">Legal</h4>
                        <ul class="space-y-2 text-gray-500">
                            <li><a href="#" class="hover:text-white transition">Privacy Policy</a></li>
                            <li><a href="#" class="hover:text-white transition">Terms of Service</a></li>
                            <li><a href="#" class="hover:text-white transition">Cookie Policy</a></li>
                            <li><a href="#" class="hover:text-white transition">Compliance</a></li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="border-t border-gray-900 mt-12 pt-8 text-center text-gray-500 text-sm">
                <p>&copy; 2025 AMARX Exchange. All rights reserved. Cryptocurrency trading involves risk.</p>
            </div>
        </div>
    </footer>

    <script>
        // Mobile Menu Toggle
        const menuBtn = document.getElementById('menuBtn');
        const closeMenu = document.getElementById('closeMenu');
        const mobileMenu = document.getElementById('mobileMenu');
        
        menuBtn.addEventListener('click', () => {
            mobileMenu.classList.add('open');
        });
        
        closeMenu.addEventListener('click', () => {
            mobileMenu.classList.remove('open');
        });
        
        // Animated Counters
        function animateCounter(elementId, finalValue, duration) {
            let element = document.getElementById(elementId);
            let start = 0;
            let increment = finalValue / (duration / 16);
            let current = 0;
            
            let timer = setInterval(() => {
                current += increment;
                if (current >= finalValue) {
                    element.innerText = finalValue.toLocaleString();
                    clearInterval(timer);
                } else {
                    element.innerText = Math.floor(current).toLocaleString();
                }
            }, 16);
        }
        
        // Initialize counters
        window.addEventListener('load', () => {
            animateCounter('volumeCounter', 2547000000, 2000);
            animateCounter('usersCounter', 125800, 1500);
            animateCounter('coinsCounter', 350, 1000);
        });
        
        // Live Ticker
        const tickerData = [
            { symbol: 'BTC/USDT', price: '$64,832.45', change: '+2.34%' },
            { symbol: 'ETH/USDT', price: '$3,245.67', change: '+1.56%' },
            { symbol: 'SOL/USDT', price: '$142.89', change: '+5.23%' },
            { symbol: 'XRP/USDT', price: '$0.5234', change: '-0.45%' },
            { symbol: 'ADA/USDT', price: '$0.4521', change: '+3.12%' },
            { symbol: 'DOT/USDT', price: '$7.89', change: '+0.89%' },
            { symbol: 'AVAX/USDT', price: '$36.45', change: '+4.21%' },
            { symbol: 'DOGE/USDT', price: '$0.1567', change: '+1.23%' }
        ];
        
        const tickerContent = document.getElementById('tickerContent');
        tickerData.forEach(item => {
            const tickerItem = document.createElement('div');
            tickerItem.className = 'flex items-center space-x-4';
            tickerItem.innerHTML = `
                <span class="font-bold">${item.symbol}</span>
                <span class="text-gray-300">${item.price}</span>
                <span class="px-2 py-1 rounded text-xs ${item.change.startsWith('+') ? 'bg-green-900/30 text-green-400' : 'bg-red-900/30 text-red-400'}">${item.change}</span>
            `;
            tickerContent.appendChild(tickerItem);
        });
        
        // Clone ticker items for seamless scroll
        const cloneContent = tickerContent.cloneNode(true);
        tickerContent.parentNode.appendChild(cloneContent);
        
        // Animate ticker
        let tickerPosition = 0;
        function animateTicker() {
            tickerPosition -= 1;
            if (tickerPosition <= -tickerContent.offsetWidth) {
                tickerPosition = 0;
            }
            tickerContent.style.transform = `translateX(${tickerPosition}px)`;
            cloneContent.style.transform = `translateX(${tickerPosition + tickerContent.offsetWidth}px)`;
            requestAnimationFrame(animateTicker);
        }
        
        // Start animation
        animateTicker();
        
        // Simple Trading Chart with D3
        function initTradingChart() {
            const width = 800;
            const height = 320;
            const data = [];
            
            // Generate sample price data
            let price = 50000;
            for (let i = 0; i < 50; i++) {
                price += (Math.random() - 0.5) * 1000;
                data.push({ time: i, price: price });
            }
            
            const svg = d3.select("#tradingChart")
                .append("svg")
                .attr("width", "100%")
                .attr("height", "100%")
                .attr("viewBox", `0 0 ${width} ${height}`);
            
            const x = d3.scaleLinear()
                .domain([0, 49])
                .range([0, width - 100]);
            
            const y = d3.scaleLinear()
                .domain([d3.min(data, d => d.price) * 0.99, d3.max(data, d => d.price) * 1.01])
                .range([height - 50, 30]);
            
            const line = d3.line()
                .x(d => x(d.time))
                .y(d => y(d.price))
                .curve(d3.curveMonotoneX);
            
            svg.append("path")
                .datum(data)
                .attr("fill", "none")
                .attr("stroke", "#2d41ff")
                .attr("stroke-width", 2)
                .attr("d", line);
            
            // Add gradient under line
            const area = d3.area()
                .x(d => x(d.time))
                .y0(height - 50)
                .y1(d => y(d.price))
                .curve(d3.curveMonotoneX);
            
            svg.append("path")
                .datum(data)
                .attr("fill", "url(#area-gradient)")
                .attr("opacity", 0.2)
                .attr("d", area);
            
            // Define gradient
            const defs = svg.append("defs");
            const gradient = defs.append("linearGradient")
                .attr("id", "area-gradient")
                .attr("x1", "0%")
                .attr("y1", "0%")
                .attr("x2", "0%")
                .attr("y2", "100%");
            
            gradient.append("stop")
                .attr("offset", "0%")
                .attr("stop-color", "#2d41ff")
                .attr("stop-opacity", 0.5);
            
            gradient.append("stop")
                .attr("offset", "100%")
                .attr("stop-color", "#2d41ff")
                .attr("stop-opacity", 0);
        }
        
        // Initialize chart when DOM is loaded
        document.addEventListener('DOMContentLoaded', initTradingChart);
        
        // Server Map Visualization with Three.js
        function initServerMap() {
            const container = document.getElementById('serverMap');
            if (!container) return;
            
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, container.clientWidth / container.clientHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
            renderer.setSize(container.clientWidth, container.clientHeight);
            container.appendChild(renderer.domElement);
            
            // Add globe points
            const geometry = new THREE.SphereGeometry(0.05, 8, 8);
            const material = new THREE.MeshBasicMaterial({ color: 0x2d41ff });
            
            const points = [
                { x: -2, y: 1, z: 0 },
                { x: -1, y: 0.5, z: -1 },
                { x: 0, y: 0, z: 0 },
                { x: 1, y: -0.5, z: 1 },
                { x: 2, y: 0, z: -1 },
                { x: -1.5, y: -1, z: 1 },
                { x: 1.5, y: 1, z: -1 }
            ];
            
            points.forEach(point => {
                const sphere = new THREE.Mesh(geometry, material);
                sphere.position.set(point.x, point.y, point.z);
                scene.add(sphere);
            });
            
            // Add connecting lines
            const lineMaterial = new THREE.LineBasicMaterial({ color: 0x2d41ff, opacity: 0.3, transparent: true });
            
            for (let i = 0; i < points.length; i++) {
                for (let j = i + 1; j < points.length; j++) {
                    const lineGeometry = new THREE.BufferGeometry().setFromPoints([
                        new THREE.Vector3(points[i].x, points[i].y, points[i].z),
                        new THREE.Vector3(points[j].x, points[j].y, points[j].z)
                    ]);
                    const line = new THREE.Line(lineGeometry, lineMaterial);
                    scene.add(line);
                }
            }
            
            camera.position.z = 5;
            
            function animate() {
                requestAnimationFrame(animate);
                scene.rotation.y += 0.005;
                renderer.render(scene, camera);
            }
            
            animate();
            
            // Handle resize
            window.addEventListener('resize', () => {
                camera.aspect = container.clientWidth / container.clientHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(container.clientWidth, container.clientHeight);
            });
        }
        
        // Initialize map
        if (document.getElementById('serverMap')) {
            initServerMap();
        }
    </script>
</body>
</html>
