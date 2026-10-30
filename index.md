HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Assignment 8.1 — Dashboard-Style Grid Layout</title>
    <!-- Link to External Stylesheet -->
    <link rel="stylesheet" href="dashboard-style.css">
</head>
<body>

    <!-- Outer Dashboard Layout Grid -->
    <div class="dashboard-grid">

        <!-- --- 1. Dashboard Header --- -->
        <header class="dashboard-header">
            <div class="header-logo">AdminPortal</div>
            <div class="header-user">Welcome, Student</div>
        </header>

        <!-- --- 2. Sidebar Navigation --- -->
        <aside class="sidebar">
            <ul class="sidebar-menu">
                <li><a href="#" class="active">Dashboard</a></li>
                <li><a href="#">Analytics</a></li>
                <li><a href="#">Projects</a></li>
                <li><a href="#">Settings</a></li>
                <li><a href="#">Logout</a></li>
            </ul>
        </aside>

        <!-- --- 3. Main Content Area --- -->
        <main class="main-content">
            <div class="content-title">
                <h1>Overview Statistics</h1>
                <p>Welcome back! Here is a summary of your key metrics.</p>
            </div>

            <!-- --- 3 & 6. Statistic Cards Grid (with Gaps) --- -->
            <div class="stats-grid">
                
                <!-- Stat Card 1 -->
                <div class="stat-card">
                    <h3>Total Users</h3>
                    <p class="stat-value">1,245</p>
                    <span class="stat-trend positive">+12% this month</span>
                </div>

                <!-- Stat Card 2 -->
                <div class="stat-card">
                    <h3>Active Projects</h3>
                    <p class="stat-value">34</p>
                    <span class="stat-trend positive">+4 new today</span>
                </div>

                <!-- Stat Card 3 -->
                <div class="stat-card">
                    <h3>Revenue</h3>
                    <p class="stat-value">$12,840</p>
                    <span class="stat-trend positive">+8% vs last week</span>
                </div>

                <!-- Stat Card 4 -->
                <div class="stat-card">
                    <h3>Support Tickets</h3>
                    <p class="stat-value">7</p>
                    <span class="stat-trend negative">Requires attention</span>
                </div>

            </div>
        </main>

    </div>

</body>
</html>
File 2: dashboard-style.css
CSS
/* --- Global Reset & Design Tokens --- */
:root {
    --primary-color: #1e3a8a;
    --secondary-color: #2563eb;
    --bg-dashboard: #f1f5f9;
    --card-bg: #ffffff;
    --text-main: #1e293b;
    --text-muted: #64748b;
    --border-color: #e2e8f0;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--bg-dashboard);
    color: var(--text-main);
}

/* ==========================================
   4 & 5. OUTER DASHBOARD GRID LAYOUT
   ================================---------- */
.dashboard-grid {
    display: grid;                          /* 4. Enable display: grid */
    grid-template-columns: 260px 1fr;       /* 5. Sidebar column (260px) and flexible main content (1fr) */
    grid-template-rows: 70px 1fr;           /* 5. Header row (70px) and flexible content row */
    min-height: 100vh;
}

/* --- 1. Header Styling --- */
.dashboard-header {
    grid-column: 1 / -1;                    /* Spans across all columns */
    background-color: var(--card-bg);
    border-bottom: 1px solid var(--border-color);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 2rem;
    z-index: 10;
}

.header-logo {
    font-size: 1.25rem;
    font-weight: 700;
    color: var(--primary-color);
}

.header-user {
    font-size: 0.95rem;
    font-weight: 600;
    color: var(--text-muted);
}

/* --- 2. Sidebar Styling --- */
.sidebar {
    background-color: #0f172a;
    color: #ffffff;
    padding: 2rem 1rem;
    border-right: 1px solid var(--border-color);
}

.sidebar-menu {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
}

.sidebar-menu a {
    display: block;
    color: #94a3b8;
    text-decoration: none;
    padding: 0.75rem 1rem;
    border-radius: 6px;
    font-weight: 500;
    transition: background-color 0.2s ease, color 0.2s ease;
}

.sidebar-menu a:hover,
.sidebar-menu a.active {
    background-color: var(--secondary-color);
    color: #ffffff;
}

/* --- 3. Main Content Area --- */
.main-content {
    padding: 2.5rem;
    overflow-y: auto;
}

.content-title {
    margin-bottom: 2rem;
}

.content-title h1 {
    font-size: 1.8rem;
    color: var(--primary-color);
    margin-bottom: 0.25rem;
}

.content-title p {
    color: var(--text-muted);
}

/* --- 3 & 6. Statistic Cards Grid & Gaps --- */
.stats-grid {
    display: grid;                          /* Nested grid for cards */
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); /* Responsive columns */
    gap: 1.5rem;                            /* 6. Use gaps between cards */
}

.stat-card {
    background-color: var(--card-bg);
    border: 1px solid var(--border-color);
    border-radius: 10px;
    padding: 1.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.02);
}

.stat-card h3 {
    font-size: 0.9rem;
    color: var(--text-muted);
    font-weight: 600;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
}

.stat-value {
    font-size: 2rem;
    font-weight: 700;
    color: var(--primary-color);
    margin-bottom: 0.5rem;
}

.stat-trend {
    font-size: 0.85rem;
    font-weight: 600;
}

.stat-trend.positive {
    color: #16a34a;                         /* Green trend */
}

.stat-trend.negative {
    color: #dc2626;                         /* Red trend */
}