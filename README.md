<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Professional GitHub Profile Generator</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0d1117;
            --bg-secondary: #161b22;
            --bg-tertiary: #21262d;
            --text-primary: #c9d1d9;
            --text-secondary: #8b949e;
            --accent-blue: #58a6ff;
            --accent-green: #238636;
            --accent-purple: #8957e5;
            --accent-pink: #f778ba;
            --border-color: #30363d;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Noto Sans', Helvetica, Arial, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        /* Header Section */
        .profile-header {
            display: flex;
            gap: 2rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .avatar-container {
            position: relative;
            width: 150px;
            height: 150px;
            flex-shrink: 0;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 4px solid var(--bg-secondary);
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            font-weight: bold;
            color: white;
            position: relative;
            overflow: hidden;
            transition: transform 0.3s ease;
        }

        .avatar:hover {
            transform: scale(1.05);
        }

        .status-indicator {
            position: absolute;
            bottom: 8px;
            right: 8px;
            width: 24px;
            height: 24px;
            background: var(--accent-green);
            border: 3px solid var(--bg-primary);
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 0 0 0 rgba(35, 134, 54, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(35, 134, 54, 0); }
        }

        .profile-info {
            flex: 1;
            min-width: 300px;
        }

        .name {
            font-size: 2rem;
            font-weight: 600;
            margin-bottom: 0.25rem;
            background: linear-gradient(90deg, var(--text-primary), var(--accent-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .username {
            font-size: 1.25rem;
            color: var(--text-secondary);
            margin-bottom: 1rem;
            font-weight: 300;
        }

        .bio {
            color: var(--text-primary);
            margin-bottom: 1rem;
            font-size: 1rem;
            max-width: 600px;
        }

        .location-work {
            display: flex;
            gap: 1.5rem;
            flex-wrap: wrap;
            color: var(--text-secondary);
            font-size: 0.875rem;
            margin-bottom: 1rem;
        }

        .location-work span {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .icon {
            width: 16px;
            height: 16px;
            fill: currentColor;
        }

        /* Action Buttons */
        .action-buttons {
            display: flex;
            gap: 0.75rem;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
        }

        .btn {
            padding: 0.5rem 1rem;
            border-radius: 6px;
            font-size: 0.875rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.2s;
            border: 1px solid var(--border-color);
            background: var(--bg-tertiary);
            color: var(--text-primary);
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        .btn:hover {
            background: var(--bg-secondary);
            border-color: var(--text-secondary);
            transform: translateY(-1px);
        }

        .btn-primary {
            background: var(--bg-tertiary);
            border-color: var(--border-color);
        }

        .btn-follow {
            background: var(--accent-green);
            border-color: var(--accent-green);
            color: white;
        }

        .btn-follow:hover {
            background: #2ea043;
            border-color: #2ea043;
        }

        /* Stats Grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .stat-card {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 1.5rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, var(--accent-blue), var(--accent-purple));
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-4px);
            border-color: var(--accent-blue);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }

        .stat-card:hover::before {
            transform: scaleX(1);
        }

        .stat-icon {
            width: 32px;
            height: 32px;
            margin-bottom: 0.75rem;
            fill: var(--accent-blue);
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--text-primary);
            margin-bottom: 0.25rem;
        }

        .stat-label {
            font-size: 0.875rem;
            color: var(--text-secondary);
        }

        /* Tech Stack */
        .section {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
        }

        .section-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .tech-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 0.75rem;
        }

        .tech-badge {
            padding: 0.375rem 0.875rem;
            background: var(--bg-tertiary);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            font-size: 0.875rem;
            color: var(--text-primary);
            transition: all 0.2s;
            cursor: default;
        }

        .tech-badge:hover {
            background: var(--accent-blue);
            color: white;
            transform: translateY(-2px);
            border-color: var(--accent-blue);
        }

        /* Contribution Graph */
        .contribution-graph {
            display: grid;
            grid-template-columns: repeat(53, 1fr);
            gap: 3px;
            margin-top: 1rem;
            overflow-x: auto;
            padding-bottom: 0.5rem;
        }

        .contribution-cell {
            aspect-ratio: 1;
            border-radius: 2px;
            background: var(--bg-tertiary);
            transition: all 0.2s;
            cursor: pointer;
            position: relative;
        }

        .contribution-cell:hover {
            transform: scale(1.2);
            z-index: 10;
            box-shadow: 0 0 10px rgba(88, 166, 255, 0.5);
        }

        .contribution-cell[data-level="1"] { background: #0e4429; }
        .contribution-cell[data-level="2"] { background: #006d32; }
        .contribution-cell[data-level="3"] { background: #26a641; }
        .contribution-cell[data-level="4"] { background: #39d353; }

        .tooltip {
            position: absolute;
            bottom: 100%;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.9);
            color: white;
            padding: 0.5rem;
            border-radius: 6px;
            font-size: 0.75rem;
            white-space: nowrap;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.2s;
            margin-bottom: 4px;
            z-index: 100;
        }

        .contribution-cell:hover .tooltip {
            opacity: 1;
        }

        /* Pinned Repos */
        .repo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1rem;
        }

        .repo-card {
            background: var(--bg-primary);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 1rem;
            transition: all 0.2s;
        }

        .repo-card:hover {
            border-color: var(--accent-blue);
            transform: translateY(-2px);
        }

        .repo-header {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
            color: var(--accent-blue);
            font-weight: 600;
        }

        .repo-description {
            color: var(--text-secondary);
            font-size: 0.875rem;
            margin-bottom: 1rem;
            line-height: 1.5;
        }

        .repo-meta {
            display: flex;
            gap: 1rem;
            font-size: 0.75rem;
            color: var(--text-secondary);
        }

        .repo-meta span {
            display: flex;
            align-items: center;
            gap: 0.25rem;
        }

        .lang-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
        }

        /* Social Links */
        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            background: var(--bg-tertiary);
            border: 1px solid var(--border-color);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s;
            color: var(--text-secondary);
            text-decoration: none;
        }

        .social-link:hover {
            background: var(--accent-blue);
            color: white;
            transform: translateY(-3px) rotate(5deg);
            border-color: var(--accent-blue);
        }

        /* Activity Graph */
        .activity-item {
            display: flex;
            gap: 1rem;
            padding: 0.75rem 0;
            border-bottom: 1px solid var(--border-color);
            animation: slideIn 0.5s ease forwards;
            opacity: 0;
        }

        .activity-item:last-child {
            border-bottom: none;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .activity-icon {
            width: 32px;
            height: 32px;
            background: var(--bg-tertiary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        .activity-content {
            flex: 1;
        }

        .activity-text {
            color: var(--text-primary);
            font-size: 0.875rem;
        }

        .activity-time {
            color: var(--text-secondary);
            font-size: 0.75rem;
            margin-top: 0.25rem;
        }

        /* Tab Navigation */
        .tabs {
            display: flex;
            gap: 0;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 1.5rem;
            overflow-x: auto;
        }

        .tab {
            padding: 0.75rem 1.5rem;
            background: none;
            border: none;
            color: var(--text-secondary);
            cursor: pointer;
            font-size: 0.875rem;
            font-weight: 500;
            border-bottom: 2px solid transparent;
            transition: all 0.2s;
            white-space: nowrap;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .tab:hover {
            color: var(--text-primary);
        }

        .tab.active {
            color: var(--text-primary);
            border-bottom-color: var(--accent-orange, #f78166);
            font-weight: 600;
        }

        .tab-count {
            background: var(--bg-tertiary);
            padding: 0.125rem 0.5rem;
            border-radius: 10px;
            font-size: 0.75rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .profile-header {
                flex-direction: column;
                align-items: center;
                text-align: center;
            }

            .location-work {
                justify-content: center;
            }

            .action-buttons {
                justify-content: center;
            }

            .contribution-graph {
                grid-template-columns: repeat(26, 1fr);
            }
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--bg-primary);
        }

        ::-webkit-scrollbar-thumb {
            background: var(--bg-tertiary);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--border-color);
        }

        /* Loading Animation */
        .skeleton {
            background: linear-gradient(90deg, var(--bg-tertiary) 25%, var(--bg-secondary) 50%, var(--bg-tertiary) 75%);
            background-size: 200% 100%;
            animation: loading 1.5s infinite;
            border-radius: 4px;
        }

        @keyframes loading {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Profile Header -->
        <div class="profile-header">
            <div class="avatar-container">
                <div class="avatar" id="avatar">JD</div>
                <div class="status-indicator"></div>
            </div>
            
            <div class="profile-info">
                <h1 class="name" contenteditable="true">John Doe</h1>
                <div class="username" contenteditable="true">@johndoe</div>
                <p class="bio" contenteditable="true">
                    Full-stack developer passionate about open source. Building scalable web applications and contributing to the developer community. Currently exploring AI/ML and cloud architecture.
                </p>
                
                <div class="location-work">
                    <span>
                        <svg class="icon" viewBox="0 0 16 16"><path d="M11.536 14.01A8.473 8.473 0 0 0 14.026 8a8.473 8.473 0 0 0-2.49-6.01l-.708.707A7.476 7.476 0 0 1 13.025 8c0 2.071-.84 3.946-2.197 5.303l.708.707z"/><path d="M10.121 12.596A6.48 6.48 0 0 0 12.025 8a6.48 6.48 0 0 0-1.904-4.596l-.707.707A5.483 5.483 0 0 1 11.025 8a5.483 5.483 0 0 1-1.61 3.89l.706.706z"/><path d="M10.025 8a4.486 4.486 0 0 1-1.318 3.182L8 10.475A3.489 3.489 0 0 0 9.025 8c0-.966-.392-1.841-1.025-2.475l.707-.707A4.486 4.486 0 0 1 10.025 8zM7 4a.5.5 0 0 0-.812-.39L3.825 5.5H1.5A.5.5 0 0 0 1 6v4a.5.5 0 0 0 .5.5h2.325l2.363 1.89A.5.5 0 0 0 7 12V4zM4.312 6.39 6 5.04v5.92L4.312 9.61A.5.5 0 0 0 4 9.5H2v-3h2a.5.5 0 0 0 .312-.11z"/></svg>
                        San Francisco, CA
                    </span>
                    <span>
                        <svg class="icon" viewBox="0 0 16 16"><path d="M10.478 1.647a.5.5 0 1 0-.956-.294l-4 13a.5.5 0 0 0 .956.294l4-13zM4.854 4.146a.5.5 0 0 1 0 .708L1.707 8l3.147 3.146a.5.5 0 0 1-.708.708l-3.5-3.5a.5.5 0 0 1 0-.708l3.5-3.5a.5.5 0 0 1 .708 0zm6.292 0a.5.5 0 0 0 0 .708L14.293 8l-3.147 3.146a.5.5 0 0 0 .708.708l3.5-3.5a.5.5 0 0 0 0-.708l-3.5-3.5a.5.5 0 0 0-.708 0z"/></svg>
                        @TechCorp
                    </span>
                    <span>
                        <svg class="icon" viewBox="0 0 16 16"><path d="M.05 3.555A2 2 0 0 1 2 2h12a2 2 0 0 1 1.95 1.555L8 8.414.05 3.555zM0 4.697v7.104l5.803-3.558L0 4.697zM6.761 8.83l-6.57 4.027A2 2 0 0 0 2 14h12a2 2 0 0 0 1.808-1.144l-6.57-4.027L8 9.586l-1.239-.757zm3.436-.586L16 11.801V4.697l-5.803 3.546z"/></svg>
                        john@example.com
                    </span>
                </div>

                <div class="action-buttons">
                    <button class="btn btn-follow">Follow</button>
                    <button class="btn">Sponsor</button>
                    <button class="btn">Contact</button>
                    <button class="btn">Hire me</button>
                </div>

                <div class="social-links">
                    <a href="#" class="social-link" title="LinkedIn">
                        <svg width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
                    </a>
                    <a href="#" class="social-link" title="Twitter">
                        <svg width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
                    </a>
                    <a href="#" class="social-link" title="Portfolio">
                        <svg width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
                    </a>
                    <a href="#" class="social-link" title="Email">
                        <svg width="20" height="20" fill="currentColor" viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
                    </a>
                </div>
            </div>
        </div>

        <!-- Stats Overview -->
        <div class="stats-grid">
            <div class="stat-card">
                <svg class="stat-icon" viewBox="0 0 24 24"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
                <div class="stat-value">1.2k</div>
                <div class="stat-label">Repositories</div>
            </div>
            <div class="stat-card">
                <svg class="stat-icon" viewBox="0 0 24 24" style="fill: var(--accent-purple)"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>
                <div class="stat-value">8.5k</div>
                <div class="stat-label">Followers</div>
            </div>
            <div class="stat-card">
                <svg class="stat-icon" viewBox="0 0 24 24" style="fill: var(--accent-green)"><path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/></svg>
                <div class="stat-value">3.4k</div>
                <div class="stat-label">Contributions</div>
            </div>
            <div class="stat-card">
                <svg class="stat-icon" viewBox="0 0 24 24" style="fill: var(--accent-pink)"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>
                <div class="stat-value">12</div>
                <div class="stat-label">Stars Earned</div>
            </div>
        </div>

        <!-- Tabs -->
        <div class="tabs">
            <button class="tab active" onclick="switchTab('overview')">
                Overview
            </button>
            <button class="tab" onclick="switchTab('repositories')">
                Repositories <span class="tab-count">42</span>
            </button>
            <button class="tab" onclick="switchTab('projects')">
                Projects
            </button>
            <button class="tab" onclick="switchTab('packages')">
                Packages
            </button>
        </div>

        <!-- Tech Stack -->
        <div class="section">
            <h2 class="section-title">
                <svg width="20" height="20" fill="currentColor" viewBox="0 0 16 16"><path d="M8.186 1.113a.5.5 0 0 0-.372 0L1.846 3.5 8 5.961 14.154 3.5 8.186 1.113zM15 4.383l-6.5 2.6v7.922l6.5-2.6V4.383zM7.5 14.077V6.383l-6.5-2.6v7.922l6.5 2.6zM7.443.184a1.5 1.5 0 0 1 1.114 0l7.129 2.852A.5.5 0 0 1 16 3.5v8.662a1 1 0 0 1-.629.928l-7.185 2.874a.5.5 0 0 1-.372 0L.63 13.09a1 1 0 0 1-.63-.928V3.5a.5.5 0 0 1 .314-.464L7.443.184z"/></svg>
                Tech Stack
            </h2>
            <div class="tech-grid">
                <span class="tech-badge">JavaScript</span>
                <span class="tech-badge">TypeScript</span>
                <span class="tech-badge">React</span>
                <span class="tech-badge">Node.js</span>
                <span class="tech-badge">Python</span>
                <span class="tech-badge">Go</span>
                <span class="tech-badge">Rust</span>
                <span class="tech-badge">Docker</span>
                <span class="tech-badge">Kubernetes</span>
                <span class="tech-badge">AWS</span>
                <span class="tech-badge">GraphQL</span>
                <span class="tech-badge">PostgreSQL</span>
            </div>
        </div>

        <!-- Contribution Graph -->
        <div class="section">
            <h2 class="section-title">
                <svg width="20" height="20" fill="currentColor" viewBox="0 0 16 16"><path d="M11 6a3 3 0 1 1-6 0 3 3 0 0 1 6 0z"/><path fill-rule="evenodd" d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8zm8-7a7 7 0 0 0-5.468 11.37C3.242 11.226 4.805 10 8 10s4.757 1.225 5.468 2.37A7 7 0 0 0 8 1z"/></svg>
                Contribution Activity
            </h2>
            <div class="contribution-graph" id="contributionGraph"></div>
            <div style="margin-top: 1rem; display: flex; gap: 1rem; align-items: center; font-size: 0.75rem; color: var(--text-secondary);">
                <span>Less</span>
                <div style="display: flex; gap: 3px;">
                    <div style="width: 10px; height: 10px; background: var(--bg-tertiary); border-radius: 2px;"></div>
                    <div style="width: 10px; height: 10px; background: #0e4429; border-radius: 2px;"></div>
                    <div style="width: 10px; height: 10px; background: #006d32; border-radius: 2px;"></div>
                    <div style="width: 10px; height: 10px; background: #26a641; border-radius: 2px;"></div>
                    <div style="width: 10px; height: 10px; background: #39d353; border-radius: 2px;"></div>
                </div>
                <span>More</span>
            </div>
        </div>

        <!-- Pinned Repositories -->
        <div class="section">
            <h2 class="section-title">
                <svg width="20" height="20" fill="currentColor" viewBox="0 0 16 16"><path d="M2 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V2zm10-1H4a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1z"/><path d="M6 5a1 1 0 0 1 1-1h1.188a2.75 2.75 0 0 1 0 5.5H7v2a.5.5 0 0 1-1 0V5zm1 3.5h1.188a1.75 1.75 0 1 0 0-3.5H7v3.5z"/></svg>
                Pinned Repositories
            </h2>
            <div class="repo-grid">
                <div class="repo-card">
                    <div class="repo-header">
                        <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16"><path d="M2 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V2zm10-1H4a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1z"/></svg>
                        awesome-project
                    </div>
                    <div class="repo-description">
                        A revolutionary open-source project that solves real-world problems with cutting-edge technology.
                    </div>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #f1e05a;"></span> JavaScript</span>
                        <span>⭐ 234</span>
                        <span>🍴 45</span>
                    </div>
                </div>
                
                <div class="repo-card">
                    <div class="repo-header">
                        <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16"><path d="M2 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V2zm10-1H4a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1z"/></svg>
                        react-components
                    </div>
                    <div class="repo-description">
                        Collection of reusable React components with TypeScript support and comprehensive documentation.
                    </div>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #3178c6;"></span> TypeScript</span>
                        <span>⭐ 189</span>
                        <span>🍴 32</span>
                    </div>
                </div>
                
                <div class="repo-card">
                    <div class="repo-header">
                        <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16"><path d="M2 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V2zm10-1H4a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1z"/></svg>
                        go-microservices
                    </div>
                    <div class="repo-description">
                        High-performance microservices architecture built with Go, featuring gRPC and Kubernetes deployment.
                    </div>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #00ADD8;"></span> Go</span>
                        <span>⭐ 567</span>
                        <span>🍴 89</span>
                    </div>
                </div>
                
                <div class="repo-card">
                    <div class="repo-header">
                        <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16"><path d="M2 2a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V2zm10-1H4a1 1 0 0 0-1 1v12a1 1 0 0 0 1 1h8a1 1 0 0 0 1-1V2a1 1 0 0 0-1-1z"/></svg>
                        ml-pipeline
                    </div>
                    <div class="repo-description">
                        End-to-end machine learning pipeline with automated training, validation, and deployment workflows.
                    </div>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #3572A5;"></span> Python</span>
                        <span>⭐ 445</span>
                        <span>🍴 67</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Recent Activity -->
        <div class="section">
            <h2 class="section-title">
                <svg width="20" height="20" fill="currentColor" viewBox="0 0 16 16"><path d="M8 16a2 2 0 0 0 2-2H6a2 2 0 0 0 2 2zM8 1.918l-.797.161A4.002 4.002 0 0 0 4 6c0 .628-.134 2.197-.459 3.742-.16.767-.376 1.566-.663 2.258h10.244c-.287-.692-.502-1.49-.663-2.258C12.134 8.197 12 6.628 12 6a4.002 4.002 0 0 0-3.203-3.92L8 1.917zM14.22 12c.223.447.481.801.78 1H1c.299-.199.557-.553.78-1C2.68 10.2 3 6.88 3 6c0-2.42 1.72-4.44 4.005-4.901a1 1 0 1 1 1.99 0A5.002 5.002 0 0 1 13 6c0 .88.32 4.2 1.22 6z"/></svg>
                Recent Activity
            </h2>
            <div id="activityFeed">
                <div class="activity-item" style="animation-delay: 0.1s">
                    <div class="activity-icon">📝</div>
                    <div class="activity-content">
                        <div class="activity-text">Created commit in <strong>awesome-project</strong></div>
                        <div class="activity-time">2 hours ago</div>
                    </div>
                </div>
                <div class="activity-item" style="animation-delay: 0.2s">
                    <div class="activity-icon">⭐</div>
                    <div class="activity-content">
                        <div class="activity-text">Starred <strong>tensorflow/tensorflow</strong></div>
                        <div class="activity-time">5 hours ago</div>
                    </div>
                </div>
                <div class="activity-item" style="animation-delay: 0.3s">
                    <div class="activity-icon">🍴</div>
                    <div class="activity-content">
                        <div class="activity-text">Forked <strong>vercel/next.js</strong></div>
                        <div class="activity-time">1 day ago</div>
                    </div>
                </div>
                <div class="activity-item" style="animation-delay: 0.4s">
                    <div class="activity-icon">🐛</div>
                    <div class="activity-content">
                        <div class="activity-text">Opened issue in <strong>facebook/react</strong></div>
                        <div class="activity-time">2 days ago</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Generate contribution graph
        function generateContributionGraph() {
            const graph = document.getElementById('contributionGraph');
            const weeks = 53;
            const days = 7;
            
            for (let w = 0; w < weeks; w++) {
                for (let d = 0; d < days; d++) {
                    const cell = document.createElement('div');
                    cell.className = 'contribution-cell';
                    
                    // Random contribution level
                    const rand = Math.random();
                    let level = 0;
                    if (rand > 0.9) level = 4;
                    else if (rand > 0.7) level = 3;
                    else if (rand > 0.4) level = 2;
                    else if (rand > 0.2) level = 1;
                    
                    if (level > 0) cell.setAttribute('data-level', level);
                    
                    // Add tooltip
                    const date = new Date();
                    date.setDate(date.getDate() - ((weeks - w) * 7 + (6 - d)));
                    const contributions = level === 0 ? 'No' : Math.floor(Math.random() * 10) + 1;
                    
                    const tooltip = document.createElement('div');
                    tooltip.className = 'tooltip';
                    tooltip.textContent = `${contributions} contributions on ${date.toDateString()}`;
                    cell.appendChild(tooltip);
                    
                    graph.appendChild(cell);
                }
            }
        }

        // Tab switching
        function switchTab(tabName) {
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // Here you would typically show/hide content sections
            console.log('Switched to:', tabName);
        }

        // Initialize
        generateContributionGraph();

        // Add hover effects to stat cards
        document.querySelectorAll('.stat-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-4px)';
            });
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0)';
            });
        });

        // Animate numbers on load
        function animateValue(element, start, end, duration) {
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                element.textContent = Math.floor(progress * (end - start) + start).toLocaleString();
                if (progress < 1) {
                    window.requestAnimationFrame(step);
                }
            };
            window.requestAnimationFrame(step);
        }

        // Animate stats on page load
        window.addEventListener('load', () => {
            const stats = document.querySelectorAll('.stat-value');
            const targets = [1200, 8500, 3400, 12];
            stats.forEach((stat, index) => {
                animateValue(stat, 0, targets[index], 2000);
            });
        });

        // Make content editable save to localStorage
        document.querySelectorAll('[contenteditable]').forEach(element => {
            const key = 'github-profile-' + element.className;
            const saved = localStorage.getItem(key);
            if (saved) element.textContent = saved;
            
            element.addEventListener('blur', () => {
                localStorage.setItem(key, element.textContent);
            });
        });

        // Update avatar initials based on name
        document.querySelector('.name').addEventListener('input', (e) => {
            const name = e.target.textContent;
            const initials = name.split(' ').map(n => n[0]).join('').toUpperCase();
            document.getElementById('avatar').textContent = initials.slice(0, 2);
        });
    </script>
</body>
</html>
