<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>45-Day Study Timetable</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 10px;
            font-size: 2.5rem;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .subtitle {
            text-align: center;
            color: #666;
            margin-bottom: 30px;
            font-size: 1.1rem;
        }

        .sync-panel {
            background: linear-gradient(45deg, #00b894, #00cec9);
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
            text-align: center;
        }

        .sync-panel input {
            padding: 10px;
            border: none;
            border-radius: 5px;
            margin: 5px;
            font-size: 14px;
            width: 200px;
        }

        .sync-panel button {
            background: white;
            color: #00b894;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            margin: 5px;
            cursor: pointer;
            font-weight: bold;
            transition: transform 0.2s;
        }

        .sync-panel button:hover {
            transform: scale(1.05);
        }

        .user-id-display {
            background: rgba(255,255,255,0.2);
            padding: 10px;
            border-radius: 5px;
            margin-top: 10px;
            font-family: monospace;
            font-size: 12px;
            word-break: break-all;
        }
        
        .legend {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 25px;
            flex-wrap: wrap;
        }
        
        .legend-item {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: 500;
        }
        
        .physics-legend {
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
        }
        
        .math-legend {
            background: linear-gradient(45deg, #4834d4, #686de0);
            color: white;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }
        
        th {
            background: linear-gradient(45deg, #2c3e50, #34495e);
            color: white;
            padding: 15px 10px;
            text-align: center;
            font-weight: 600;
            font-size: 0.95rem;
        }
        
        td {
            padding: 12px 8px;
            text-align: center;
            border-bottom: 1px solid #eee;
            vertical-align: middle;
        }
        
        tr:nth-child(even) {
            background-color: #f8f9fa;
        }
        
        tr:hover {
            background-color: #e3f2fd;
            transform: scale(1.01);
            transition: all 0.2s ease;
        }
        
        .day-cell {
            font-weight: 600;
            color: #2c3e50;
            min-width: 80px;
        }
        
        .date-cell {
            color: #7f8c8d;
            font-size: 0.9rem;
            min-width: 90px;
        }
        
        .physics-cell {
            background: linear-gradient(45deg, #ff6b6b22, #ee5a2422);
            color: #c0392b;
            font-weight: 500;
            min-width: 200px;
            text-align: left;
            padding-left: 15px;
        }
        
        .math-cell {
            background: linear-gradient(45deg, #4834d422, #686de022);
            color: #2d3436;
            font-weight: 500;
            min-width: 200px;
            text-align: left;
            padding-left: 15px;
        }
        
        .checkbox-cell {
            min-width: 100px;
        }
        
        .checkbox-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            align-items: center;
        }
        
        .custom-checkbox {
            width: 25px;
            height: 25px;
            border: 2px solid #ddd;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .custom-checkbox.checked {
            background: linear-gradient(45deg, #00b894, #00cec9);
            border-color: #00b894;
            color: white;
        }
        
        .custom-checkbox.crossed {
            background: linear-gradient(45deg, #e17055, #d63031);
            border-color: #d63031;
            color: white;
        }
        
        .custom-checkbox:hover {
            transform: scale(1.1);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .progress-bar {
            width: 100%;
            height: 20px;
            background: #ecf0f1;
            border-radius: 10px;
            margin: 20px 0;
            overflow: hidden;
            position: relative;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(45deg, #00b894, #00cec9);
            width: 0%;
            transition: width 0.5s ease;
            border-radius: 10px;
        }
        
        .progress-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: #2c3e50;
            font-weight: 600;
            font-size: 0.85rem;
        }
        
        .stats {
            display: flex;
            justify-content: space-around;
            margin: 20px 0;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .stat-card {
            background: linear-gradient(45deg, #74b9ff, #0984e3);
            color: white;
            padding: 15px 25px;
            border-radius: 10px;
            text-align: center;
            min-width: 150px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            display: block;
        }
        
        .stat-label {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        .status-indicator {
            text-align: center;
            margin: 10px 0;
            padding: 10px;
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
            font-weight: 600;
            color: #2c3e50;
        }

        .export-import {
            margin: 10px 0;
            text-align: center;
        }

        .export-import button {
            background: #74b9ff;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            margin: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .export-import button:hover {
            background: #0984e3;
        }

        .hidden {
            display: none;
        }

        .setup-instructions {
            background: #fff3cd;
            border: 1px solid #ffeaa7;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .setup-instructions h3 {
            margin-top: 0;
            color: #856404;
        }

        .setup-instructions a {
            color: #007bff;
            text-decoration: none;
        }

        .setup-instructions a:hover {
            text-decoration: underline;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 15px;
                margin: 10px;
            }
            
            table {
                font-size: 0.8rem;
            }
            
            th, td {
                padding: 8px 4px;
            }
            
            .physics-cell, .math-cell {
                min-width: 150px;
                padding-left: 8px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .legend {
                flex-direction: column;
                align-items: center;
            }

            .sync-panel input {
                width: 150px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📚 45-Day Study Timetable</h1>
        <p class="subtitle">Physics (2.5 hrs/day) • Mathematics (3.5 hrs/day) • MAY 28 - July 11, 2025</p>
        
        <div class="setup-instructions">
            <h3>🔧 One-Time Setup for Cloud Sync</h3>
            <p>To enable permanent cloud storage across all your devices:</p>
            <ol>
                <li>Visit <a href="https://jsonbin.io" target="_blank">JSONBin.io</a> and create a free account</li>
                <li>Go to "API Keys" in your dashboard and copy your Access Key</li>
                <li>Paste it in the input below and click "Enable Cloud Sync"</li>
            </ol>
            <div style="margin-top: 10px;">
                <input type="text" id="apiKeyInput" placeholder="Paste your JSONBin API Key here" style="width: 300px; padding: 8px; margin-right: 10px;">
                <button onclick="saveApiKey()" style="background: #00b894; color: white; border: none; padding: 8px 15px; border-radius: 5px; cursor: pointer;">Enable Cloud Sync</button>
            </div>
            <p><small>Your API key is stored locally and used only for your personal data storage.</small></p>
        </div>
        
        <div class="sync-panel">
            <h3 style="margin-top: 0;">🔄 Cross-Device Sync</h3>
            <div>
                <input type="text" id="userIdInput" placeholder="Enter your Study ID to sync" />
                <button onclick="syncWithId()">Sync Data</button>
                <button onclick="generateNewId()">Generate New ID</button>
            </div>
            <div class="user-id-display">
                Your Study ID: <span id="currentUserId">Generating...</span>
                <br><small>Save this ID to access your data from any device!</small>
            </div>
        </div>

        <div class="export-import">
            <button onclick="exportData()">📥 Export Data</button>
            <button onclick="document.getElementById('importFile').click()">📤 Import Data</button>
            <input type="file" id="importFile" accept=".json" onchange="importData(event)" class="hidden">
            <button onclick="clearAllData()" style="background: #e17055;">🗑️ Clear All Data</button>
        </div>

        <div class="status-indicator" id="statusIndicator">
            🟡 Initializing...
        </div>
        
        <div class="legend">
            <div class="legend-item physics-legend">
                <span>🔬</span> Physics (2.5 hours)
            </div>
            <div class="legend-item math-legend">
                <span>📐</span> Mathematics (3.5 hours)
            </div>
        </div>
        
        <div class="stats">
            <div class="stat-card">
                <span class="stat-number" id="completedDays">0</span>
                <span class="stat-label">Days Completed</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" id="totalHours">0</span>
                <span class="stat-label">Hours Studied</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" id="successRate">0%</span>
                <span class="stat-label">Success Rate</span>
            </div>
            <div class="stat-card" style="background: linear-gradient(45deg, #00b894, #00cec9);">
                <span class="stat-number" id="streak">0</span>
                <span class="stat-label">Current Streak</span>
            </div>
        </div>
        
        <div class="progress-bar">
            <div class="progress-fill" id="progressFill"></div>
            <div class="progress-text" id="progressText">0% Complete</div>
        </div>
        
        <table>
            <thead>
                <tr>
                    <th>Day</th>
                    <th>Date</th>
                    <th>🔬 Physics Topics (2.5 hrs)</th>
                    <th>📐 Mathematics Topics (3.5 hrs)</th>
                    <th>Progress</th>
                </tr>
            </thead>
            <tbody id="timetableBody">
                <!-- Table content will be generated by JavaScript -->
            </tbody>
        </table>
    </div>

    <script>
        // Cloud storage configuration
        const JSONBIN_API_URL = 'https://api.jsonbin.io/v3/b';
        let JSONBIN_ACCESS_KEY = null;
        
        let currentUserId = null;
        let currentBinId = null;
        let isOnline = navigator.onLine;
        let autoSaveTimeout = null;

        // Study plan data
        const physicsTopics = [
            "Ch 1: Electric Charges and Fields - Basic concepts",
            "Ch 1: Electric Charges and Fields - Coulomb's Law",
            "Ch 1: Electric Charges and Fields - Electric Field & Gauss Law",
            "Ch 1: Electric Charges and Fields - Applications & Problems",
            "Ch 2: Electrostatic Potential - Potential & Work",
            "Ch 2: Electrostatic Potential - Equipotential surfaces",
            "Ch 2: Capacitance - Basic concepts & types",
            "Ch 2: Capacitance - Energy stored & combinations",
            "Ch 3: Current Electricity - Current & resistance",
            "Ch 3: Current Electricity - Ohm's law & circuits",
            "Ch 3: Current Electricity - Kirchhoff's laws & networks",
            "Ch 3: Current Electricity - Wheatstone bridge & potentiometer",
            "Ch 4: Moving Charges - Magnetic force on charges",
            "Ch 4: Moving Charges - Motion in magnetic field",
            "Ch 4: Moving Charges - Force on current carrying conductors",
            "Ch 4: Moving Charges - Applications & cyclotron",
            "Ch 5: Magnetism & Matter - Magnetic properties",
            "Ch 5: Magnetism & Matter - Earth's magnetism",
            "Ch 5: Magnetism & Matter - Magnetic materials",
            "Ch 6: Electromagnetic Induction - Faraday's laws",
            "Ch 6: Electromagnetic Induction - Lenz's law & motional EMF",
            "Ch 6: Electromagnetic Induction - Self & mutual inductance",
            "Ch 6: Electromagnetic Induction - Applications & eddy currents",
            "Ch 7: Alternating Current - AC fundamentals",
            "Ch 7: Alternating Current - AC circuits with R,L,C",
            "Ch 7: Alternating Current - LCR circuits & resonance",
            "Ch 7: Alternating Current - Power & transformers",
            "Ch 8: Electromagnetic Waves - Wave equation & properties",
            "Ch 8: Electromagnetic Waves - EM spectrum",
            "Ch 8: Electromagnetic Waves - Applications & communication",
            "Ch 14: Semiconductors - Intrinsic & extrinsic",
            "Ch 14: Semiconductors - PN junction & diodes",
            "Ch 14: Semiconductors - Transistors & amplifiers",
            "Ch 14: Semiconductors - Logic gates & applications",
            "Ch 14: Semiconductors - Digital electronics",
            "Ch 1-2: Electrostatics - Complete chapter problems",
            "Ch 3-4: Current & Magnetism - Complete chapter problems",
            "Ch 5-6: Magnetism & Induction - Complete chapter problems",
            "Ch 7-8: AC & EM Waves - Complete chapter problems",
            "Ch 14: Semiconductors - Complete chapter problems",
            "Electric field & potential - Advanced problems",
            "Magnetic field & induction - Advanced problems",
            "AC circuits & waves - Advanced problems",
            "Semiconductor devices - Advanced problems",
            "Mixed problems - All chapters combined"
        ];

        const mathTopics = [
            "Mathematical Logic - Statements & connectives",
            "Mathematical Logic - Truth tables & tautologies",
            "Sets Theory - Basic operations & Venn diagrams",
            "Sets Theory - Relations between sets & cardinality",
            "Relations and Functions - Types of relations",
            "Relations and Functions - Types of functions",
            "Relations and Functions - Inverse & composite functions",
            "Mathematical Induction - Principle & applications",
            "Boolean Algebra - Basic laws & theorems",
            "Boolean Algebra - Simplification & Karnaugh maps",
            "Probability - Basic concepts & sample space",
            "Probability - Addition & multiplication rules",
            "Probability - Conditional probability & Bayes theorem",
            "Statistics - Measures of central tendency",
            "Statistics - Measures of dispersion & correlation",
            "Matrices - Basic operations & types",
            "Matrices - Rank, inverse & elementary operations",
            "Determinants - Properties & cofactor expansion",
            "Determinants - Applications & system of equations",
            "Limits & Continuity - Definition & basic limits",
            "Limits & Continuity - L'Hospital's rule & applications",
            "Limits & Continuity - Continuity & discontinuity",
            "Derivatives - Basic differentiation rules",
            "Derivatives - Chain rule & implicit differentiation",
            "Derivatives - Higher order derivatives",
            "Derivatives - Applications - tangent, normal",
            "Derivatives - Maxima-minima & curve sketching",
            "Integration - Basic integration techniques",
            "Integration - Integration by substitution",
            "Integration - Integration by parts",
            "Integration - Partial fractions & rational functions",
            "Integration - Definite integrals & properties",
            "Integration - Applications of definite integrals",
            "Differential Equations - Formation & first order",
            "Differential Equations - Separable & linear equations",
            "Differential Equations - Applications & modeling",
            "Area Under Curve - Basic area calculations",
            "Area Under Curve - Area between curves",
            "Area Under Curve - Volume of revolution",
            "2D Geometry - Straight lines & circles",
            "2D Geometry - Parabola & ellipse",
            "2D Geometry - Hyperbola & conic applications",
            "3D Geometry - Direction cosines & coordinate geometry",
            "3D Geometry - Equation of planes & lines",
            "Vectors - Basic operations & components",
            "Vectors - Dot product & cross product applications"
        ];

        // Network status monitoring
        window.addEventListener('online', () => {
            isOnline = true;
            updateStatus('🟢 Online - Auto-sync enabled');
            autoSyncToCloud();
        });

        window.addEventListener('offline', () => {
            isOnline = false;
            updateStatus('🔴 Offline - Local storage only');
        });

        // Initialize the application
        function initApp() {
            loadApiKey();
            initializeUserId();
            generateTimetable();
            loadData();
            updateStats();
        }

        // Save API key
        function saveApiKey() {
            const apiKey = document.getElementById('apiKeyInput').value.trim();
            if (!apiKey) {
                alert('Please enter your JSONBin API key');
                return;
            }
            
            JSONBIN_ACCESS_KEY = apiKey;
            localStorage.setItem('jsonbinApiKey', apiKey);
            document.getElementById('apiKeyInput').value = '';
            
            // Hide setup instructions
            document.querySelector('.setup-instructions').style.display = 'none';
            
            updateStatus('🔑 API Key saved - Cloud sync enabled');
            
            // Try to sync existing data
            autoSyncToCloud();
        }

        // Load API key from storage
        function loadApiKey() {
            JSONBIN_ACCESS_KEY = localStorage.getItem('jsonbinApiKey');
            if (JSONBIN_ACCESS_KEY) {
                document.querySelector('.setup-instructions').style.display = 'none';
                updateStatus('🔑 Cloud sync ready');
            }
        }

        // Generate dates starting from May 28, 2025
        function generateDates(startDate, days) {
            const dates = [];
            const current = new Date(startDate);
            
            for (let i = 0; i < days; i++) {
                dates.push(new Date(current));
                current.setDate(current.getDate() + 1);
            }
            
            return dates;
        }

        // Format date for display
        function formatDate(date) {
            const options = { 
                month: 'short', 
                day: 'numeric',
                weekday: 'short'
            };
            return date.toLocaleDateString('en-US', options);
        }

        // Generate unique user ID
        function generateUserId() {
            return 'study_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
        }

        // Initialize user ID
        function initializeUserId() {
            currentUserId = localStorage.getItem('studyTrackerUserId');
            if (!currentUserId) {
                currentUserId = generateUserId();
                localStorage.setItem('studyTrackerUserId', currentUserId);
            }
            document.getElementById('currentUserId').textContent = currentUserId;
            
            // Load bin ID if exists
            currentBinId = localStorage.getItem('studyTrackerBinId_' + currentUserId);
        }

        // Generate new user ID
        function generateNewId() {
            if (confirm('This will create a new Study ID and you will lose access to your current data unless you export it first. Continue?')) {
                currentUserId = generateUserId();
                localStorage.setItem('studyTrackerUserId', currentUserId);
                localStorage.removeItem('studyTrackerBinId_' + currentUserId);
                currentBinId = null;
                document.getElementById('currentUserId').textContent = currentUserId;
                
                // Clear current progress
                document.querySelectorAll('.custom-checkbox').forEach(box => {
                    box.classList.remove('checked', 'crossed');
                });
                
                updateStats();
                saveData();
                updateStatus('🆕 New Study ID generated');
            }
        }

        // Sync with existing ID
        function syncWithId() {
            const inputId = document.getElementById('userIdInput').value.trim();
            if (!inputId) {
                alert('Please enter a Study ID');
                return;
            }
            
            if (confirm('This will sync with the provided Study ID and may overwrite your current progress. Continue?')) {
                currentUserId = inputId;
                localStorage.setItem('studyTrackerUserId', currentUserId);
                document.getElementById('currentUserId').textContent = currentUserId;
                document.getElementById('userIdInput').value = '';
                
                // Reset bin ID for new user
                currentBinId = localStorage.getItem('studyTrackerBinId_' + currentUserId);
                
                // Try to load data for this ID
                loadCloudData();
            }
        }

        // Update status indicator
        function updateStatus(message) {
            document.getElementById('statusIndicator').textContent = message;
        }

        // Generate timetable
        function generateTimetable() {
            const startDate = new Date('2025-05-28');
            const dates = generateDates(startDate, 45);
            const tbody = document.getElementById('timetableBody');
            
            for (let i = 0; i < 45; i++) {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td class="day-cell">Day ${i + 1}</td>
                    <td class="date-cell">${formatDate(dates[i])}</td>
                    <td class="physics-cell">${physicsTopics[i]}</td>
                    <td class="math-cell">${mathTopics[i]}</td>
                    <td class="checkbox-cell">
                        <div class="checkbox-container">
                            <div class="custom-checkbox" data-day="${i + 1}" data-type="check" title="Completed successfully">
                                ✓
                            </div>
                            <div class="custom-checkbox" data-day="${i + 1}" data-type="cross" title="Did not follow routine">
                                ✗
                            </div>
                        </div>
                    </td>
                `;
                
                tbody.appendChild(row);
            }
            
            // Add click listeners to checkboxes
            document.querySelectorAll('.custom-checkbox').forEach(checkbox => {
                checkbox.addEventListener('click', handleCheckboxClick);
            });
        }

        // Get current progress data
        function getProgressData() {
            const progressData = {
                userId: currentUserId,
                timestamp: Date.now(),
                progress: {}
            };
            
            // Get all checked and crossed boxes
            document.querySelectorAll('.custom-checkbox.checked').forEach(box => {
                progressData.progress[box.dataset.day] = 'completed';
            });
            
            document.querySelectorAll('.custom-checkbox.crossed').forEach(box => {
                progressData.progress[box.dataset.day] = 'missed';
            });
            
            return progressData;
        }

        // Apply progress data to checkboxes
        function applyProgressData(data) {
            // Clear all checkboxes first
            document.querySelectorAll('.custom-checkbox').forEach(box => {
                box.classList.remove('checked', 'crossed');
            });
            
            // Apply progress
            if (data.progress) {
                Object.keys(data.progress).forEach(day => {
                    const status = data.progress[day];
                    const checkBox = document.querySelector(`.custom-checkbox[data-day="${day}"][data-type="check"]`);
                    const crossBox = document.querySelector(`.custom-checkbox[data-day="${day}"][data-type="cross"]`);
                    
                    if (checkBox && crossBox) {
                        if (status === 'completed') {
                            checkBox.classList.add('checked');
                            crossBox.classList.remove('crossed');
                        } else if (status === 'missed') {
                            crossBox.classList.add('crossed');
                            checkBox.classList.remove('checked');
                        }
                    }
                });
            }
        }

        // Save data to cloud using JSONBin
        async function saveToCloud(data) {
            if (!isOnline || !JSONBIN_ACCESS_KEY) return false;
            
            try {
                let url = JSONBIN_API_URL;
                let method = 'POST';
                
                // If we have a bin ID, update existing bin
                if (currentBinId) {
                    url = `${JSONBIN_API_URL}/${currentBinId}`;
                    method = 'PUT';
                }
                
                const response = await fetch(url, {
                    method: method,
                    headers: {
                        'Content-Type': 'application/json',
                        'X-Master-Key': JSONBIN_ACCESS_KEY,
                        'X-Bin-Name': `StudyTracker_${currentUserId}`,
                        'X-Bin-Private': 'true'
                    },
                    body: JSON.stringify(data)
                });
                
                if (response.ok) {
                    const result = await response.json();
                    
                    // Save bin ID for future updates
                    if (result.metadata && result.metadata.id) {
                        currentBinId = result.metadata.id;
                        localStorage.setItem('studyTrackerBinId_' + currentUserId, currentBinId);
                    }
                    
                    updateStatus('🟢 Data saved to cloud permanently');
                    return true;
                } else {
                    throw new Error(`HTTP ${response.status}`);
                }
            } catch (error) {
                console.warn('Cloud save failed:', error);
                updateStatus('🟡 Cloud save failed - using local storage only');
                return false;
            }
        }

        // Load data from cloud
        async function loadCloudData() {
            if (!JSONBIN_ACCESS_KEY) {
                loadLocalData();
                return;
            }
            
            updateStatus('🔄 Loading data from cloud...');
            
            try {
                // Try to load with bin ID first
                if (currentBinId) {
                    const response = await fetch(`${JSONBIN_API_URL}/${
