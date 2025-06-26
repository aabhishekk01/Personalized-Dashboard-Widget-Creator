<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personalized Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4f46e5;
            --primary-light: #818cf8;
            --secondary: #10b981;
            --dark: #1e293b;
            --light: #f8fafc;
            --danger: #ef4444;
        }

        /* Animation classes */
        .fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .slide-in {
            animation: slideIn 0.3s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); }
            to { transform: translateX(0); }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        /* Custom styles */
        .card {
            transition: all 0.3s ease;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }

        .card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }

        .btn {
            transition: all 0.2s ease;
        }

        .btn:hover {
            transform: translateY(-1px);
        }

        .btn:active {
            transform: translateY(1px);
        }

        /* Loading skeleton */
        .skeleton {
            background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
            background-size: 200% 100%;
            animation: shimmer 1.5s infinite;
        }

        @keyframes shimmer {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }

        /* Focus styles for accessibility */
        *:focus {
            outline: 2px solid var(--primary-light);
            outline-offset: 2px;
        }

        /* Dark mode toggle styles */
        .dark .dark\:bg-dark {
            background-color: var(--dark);
        }

        .dark .dark\:text-light {
            color: var(--light);
        }

        .dark .dark\:card-dark {
            background-color: #334155;
            border-color: #475569;
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen font-sans transition-colors duration-300 dark:bg-dark">
    <!-- App Container -->
    <div id="app" class="min-h-screen flex flex-col">
        <!-- Auth View -->
        <div id="auth-view" class="flex-1 flex items-center justify-center p-4 fade-in">
            <div class="w-full max-w-md bg-white rounded-lg shadow-lg overflow-hidden dark:card-dark">
                <div class="px-10 py-12">
                    <div class="text-center mb-8">
                        <h1 class="text-3xl font-bold text-gray-800 dark:text-light mb-2">Welcome Back</h1>
                        <p class="text-gray-600 dark:text-gray-300">Sign in to access your dashboard</p>
                    </div>
                    
                    <form id="login-form" class="space-y-6">
                        <div>
                            <label for="email" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-1">Email</label>
                            <input 
                                type="email" 
                                id="email" 
                                required
                                aria-required="true"
                                class="w-full px-4 py-2 border border-gray-300 rounded-md focus:ring-2 focus:ring-primary focus:border-transparent dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                                placeholder="your@email.com"
                            >
                        </div>
                        
                        <div>
                            <label for="password" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-1">Password</label>
                            <input 
                                type="password" 
                                id="password" 
                                required
                                aria-required="true"
                                class="w-full px-4 py-2 border border-gray-300 rounded-md focus:ring-2 focus:ring-primary focus:border-transparent dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                                placeholder="••••••••"
                            >
                        </div>
                        
                        <div class="flex items-center justify-between">
                            <div class="flex items-center">
                                <input 
                                    id="remember-me" 
                                    type="checkbox" 
                                    class="h-4 w-4 text-primary focus:ring-primary border-gray-300 rounded dark:bg-gray-700 dark:border-gray-600"
                                >
                                <label for="remember-me" class="ml-2 block text-sm text-gray-700 dark:text-gray-300">Remember me</label>
                            </div>
                            
                            <a href="#" class="text-sm text-primary hover:text-primary-light">Forgot password?</a>
                        </div>
                        
                        <div>
                            <button 
                                type="submit" 
                                class="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-primary hover:bg-primary-light focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary transition-all duration-200"
                            >
                                Sign in
                            </button>
                        </div>
                    </form>
                    
                    <div class="mt-6 text-center">
                        <p class="text-sm text-gray-600 dark:text-gray-400">
                            Don't have an account? 
                            <a href="#" class="font-medium text-primary hover:text-primary-light">Sign up</a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- Dashboard View (initially hidden) -->
        <div id="dashboard-view" class="hidden flex-1 flex flex-col">
            <!-- Header -->
            <header class="bg-white shadow-sm dark:card-dark">
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
                    <h1 class="text-xl font-semibold text-gray-900 dark:text-light">Dashboard</h1>
                    
                    <div class="flex items-center space-x-4">
                        <button 
                            id="dark-mode-toggle"
                            aria-label="Toggle dark mode"
                            class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors"
                        >
                            <i class="fas fa-moon text-gray-600 dark:text-yellow-300"></i>
                        </button>
                        
                        <div class="relative">
                            <button 
                                id="user-menu-button"
                                aria-expanded="false"
                                aria-haspopup="true"
                                class="flex items-center space-x-2 focus:outline-none"
                            >
                                <div class="h-8 w-8 rounded-full bg-primary flex items-center justify-center text-white">
                                    <span id="user-initial">U</span>
                                </div>
                                <span class="text-gray-700 dark:text-gray-300 hidden md:inline">User</span>
                            </button>
                            
                            <div 
                                id="user-menu"
                                class="hidden origin-top-right absolute right-0 mt-2 w-48 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 focus:outline-none dark:card-dark z-10"
                                role="menu"
                            >
                                <div class="py-1" role="none">
                                    <a 
                                        href="#" 
                                        class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-700"
                                        role="menuitem"
                                    >Your Profile</a>
                                    <a 
                                        href="#" 
                                        class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-700"
                                        role="menuitem"
                                    >Settings</a>
                                    <button 
                                        id="logout-btn"
                                        class="block w-full text-left px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-700"
                                        role="menuitem"
                                    >Sign out</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </header>
            
            <!-- Main Content -->
            <main class="flex-1">
                <!-- Stats Overview -->
                <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <!-- Stats Card 1 -->
                        <div class="card bg-white rounded-lg p-6 dark:card-dark fade-in">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm font-medium text-gray-500 dark:text-gray-400">Total Revenue</p>
                                    <div class="mt-2 flex items-center">
                                        <p id="revenue-value" class="text-2xl font-semibold text-gray-900 dark:text-light">$0</p>
                                        <span id="revenue-change" class="ml-2 text-sm flex items-center text-green-500">
                                            <i class="fas fa-arrow-up mr-1"></i>
                                            <span>0%</span>
                                        </span>
                                    </div>
                                </div>
                                <div class="h-12 w-12 rounded-full bg-blue-100 flex items-center justify-center dark:bg-blue-900">
                                    <i class="fas fa-dollar-sign text-blue-600 dark:text-blue-300"></i>
                                </div>
                            </div>
                            <div class="mt-4">
                                <div class="h-2 w-full bg-gray-200 rounded-full overflow-hidden dark:bg-gray-700">
                                    <div id="revenue-progress" class="h-full bg-blue-500 rounded-full" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Stats Card 2 -->
                        <div class="card bg-white rounded-lg p-6 dark:card-dark fade-in" style="animation-delay: 0.1s">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm font-medium text-gray-500 dark:text-gray-400">New Users</p>
                                    <div class="mt-2 flex items-center">
                                        <p id="users-value" class="text-2xl font-semibold text-gray-900 dark:text-light">0</p>
                                        <span id="users-change" class="ml-2 text-sm flex items-center text-green-500">
                                            <i class="fas fa-arrow-up mr-1"></i>
                                            <span>0%</span>
                                        </span>
                                    </div>
                                </div>
                                <div class="h-12 w-12 rounded-full bg-green-100 flex items-center justify-center dark:bg-green-900">
                                    <i class="fas fa-users text-green-600 dark:text-green-300"></i>
                                </div>
                            </div>
                            <div class="mt-4">
                                <div class="h-2 w-full bg-gray-200 rounded-full overflow-hidden dark:bg-gray-700">
                                    <div id="users-progress" class="h-full bg-green-500 rounded-full" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Stats Card 3 -->
                        <div class="card bg-white rounded-lg p-6 dark:card-dark fade-in" style="animation-delay: 0.2s">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm font-medium text-gray-500 dark:text-gray-400">Tasks Completed</p>
                                    <div class="mt-2 flex items-center">
                                        <p id="tasks-value" class="text-2xl font-semibold text-gray-900 dark:text-light">0/0</p>
                                        <span id="tasks-change" class="ml-2 text-sm flex items-center text-red-500">
                                            <i class="fas fa-arrow-down mr-1"></i>
                                            <span>0%</span>
                                        </span>
                                    </div>
                                </div>
                                <div class="h-12 w-12 rounded-full bg-purple-100 flex items-center justify-center dark:bg-purple-900">
                                    <i class="fas fa-tasks text-purple-600 dark:text-purple-300"></i>
                                </div>
                            </div>
                            <div class="mt-4">
                                <div class="h-2 w-full bg-gray-200 rounded-full overflow-hidden dark:bg-gray-700">
                                    <div id="tasks-progress" class="h-full bg-purple-500 rounded-full" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Stats Card 4 -->
                        <div class="card bg-white rounded-lg p-6 dark:card-dark fade-in" style="animation-delay: 0.3s">
                            <div class="flex items-center justify-between">
                                <div>
                                    <p class="text-sm font-medium text-gray-500 dark:text-gray-400">Support Tickets</p>
                                    <div class="mt-2 flex items-center">
                                        <p id="tickets-value" class="text-2xl font-semibold text-gray-900 dark:text-light">0</p>
                                        <span id="tickets-change" class="ml-2 text-sm flex items-center text-green-500">
                                            <i class="fas fa-arrow-up mr-1"></i>
                                            <span>0%</span>
                                        </span>
                                    </div>
                                </div>
                                <div class="h-12 w-12 rounded-full bg-yellow-100 flex items-center justify-center dark:bg-yellow-900">
                                    <i class="fas fa-ticket-alt text-yellow-600 dark:text-yellow-300"></i>
                                </div>
                            </div>
                            <div class="mt-4">
                                <div class="h-2 w-full bg-gray-200 rounded-full overflow-hidden dark:bg-gray-700">
                                    <div id="tickets-progress" class="h-full bg-yellow-500 rounded-full" style="width: 0%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </section>
                
                <!-- Charts Section -->
                <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4">
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                        <!-- Line Chart -->
                        <div class="card bg-white rounded-lg p-6 dark:card-dark fade-in" style="animation-delay: 0.4s">
                            <div class="flex items-center justify-between mb-4">
                                <h2 class="text-lg font-medium text-gray-900 dark:text-light">Revenue Overview</h2>
                                <div class="relative">
                                    <select 
                                        id="chart-period"
                                        class="appearance-none bg-gray-50 border border-gray-300 text-gray-700 py-1 px-3 pr-8 rounded-md leading-tight focus:outline-none focus:ring-2 focus:ring-primary dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                                    >
                                        <option>Last 7 days</option>
                                        <option>Last 30 days</option>
                                        <option>Last 90 days</option>
                                    </select>
                                    <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700 dark:text-gray-300">
                                        <i class="fas fa-chevron-down"></i>
                                    </div>
                                </div>
                            </div>
                            <div class="h-64">
                                <canvas id="line-chart"></canvas>
                            </div>
                            <div id="line-chart-loading" class="h-64 flex items-center justify-center">
                                <div class="text-center">
                                    <i class="fas fa-circle-notch fa-spin text-2xl text-primary mb-2"></i>
                                    <p class="text-gray-500 dark:text-gray-400">Loading chart data...</p>
                                </div>
                            </div>
                        </div>
                        
                        <!-- Pie Chart -->
                        <div class="card bg-white rounded-lg p-6 dark:card-dark fade-in" style="animation-delay: 0.5s">
                            <div class="flex items-center justify-between mb-4">
                                <h2 class="text-lg font-medium text-gray-900 dark:text-light">Traffic Sources</h2>
                                <button 
                                    id="refresh-traffic"
                                    aria-label="Refresh traffic data"
                                    class="p-1 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors"
                                >
                                    <i class="fas fa-sync-alt text-gray- 600 dark:text-gray-300"></i>
                                </button>
                            </div>
                            <div class="h-64">
                                <canvas id="pie-chart"></canvas>
                            </div>
                            <div id="pie-chart-loading" class="h-64 flex items-center justify-center">
                                <div class="text-center">
                                    <i class="fas fa-circle-notch fa-spin text-2xl text-primary mb-2"></i>
                                    <p class="text-gray-500 dark:text-gray-400">Loading chart data...</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </section>
            </main>
        </div>
    </div>
    <script>
        document.getElementById('login-form').addEventListener('submit', function(event) {
            event.preventDefault();
            // Simulate login
            document.getElementById('auth-view').classList.add('hidden');
            document.getElementById('dashboard-view').classList.remove('hidden');
        });

        document.getElementById('dark-mode-toggle').addEventListener('click', function() {
            document.body.classList.toggle('dark');
        });

        document.getElementById('logout-btn').addEventListener('click', function() {
            document.getElementById('dashboard-view').classList.add('hidden');
            document.getElementById('auth-view').classList.remove('hidden');
        });

        // Simulate loading data for charts
        setTimeout(() => {
            document.getElementById('line-chart-loading').style.display = 'none';
            document.getElementById('pie-chart-loading').style.display = 'none';
            // Initialize charts here
        }, 2000);
    </script>
</body>
</html> 
