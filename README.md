<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>45-Day Study Timetable - Cloud Sync</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1400px;
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
            margin-bottom: 20px;
            font-size: 1.1rem;
        }
        
        .setup-section {
            background: linear-gradient(45deg, #74b9ff, #0984e3);
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 25px;
        }
        
        .setup-section h3 {
            margin-top: 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .setup-steps {
            background: rgba(255,255,255,0.1);
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
        }
        
        .setup-steps ol {
            margin: 0;
            padding-left: 20px;
        }
        
        .setup-steps li {
            margin: 8px 0;
            line-height: 1.5;
        }
        
        .setup-input {
            display: flex;
            gap: 10px;
            align-items: center;
            flex-wrap: wrap;
            margin-top: 15px;
        }
        
        .setup-input input {
            flex: 1;
            min-width: 250px;
            padding: 10px;
            border: none;
            border-radius: 5px;
            font-size: 14px;
        }
        
        .setup-input button {
            padding: 10px 20px;
            background: #00b894;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .setup-input button:hover {
            background: #00a085;
            transform: translateY(-2px);
        }
        
        .connection-status {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 15px;
            padding: 10px;
            border-radius: 5px;
            font-weight: 600;
        }
        
        .status-connected {
            background: rgba(0, 184, 148, 0.2);
            color: #00b894;
        }
        
        .status-disconnected {
            background: rgba(225, 112, 85, 0.2);
            color: #e17055;
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
            min-width: 150px;
            padding: 8px;
        }
        
        .subject-checkbox-container {
            display: flex;
            flex-direction: column;
            gap: 8px;
            align-items: center;
        }
        
        .checkbox-row {
            display: flex;
            align-items: center;
            gap: 8px;
            justify-content: center;
        }
        
        .subject-label {
            font-size: 0.8rem;
            font-weight: 600;
            min-width: 45px;
            text-align: right;
        }
        
        .physics-label {
            color: #c0392b;
        }
        
        .math-label {
            color: #2d3436;
        }
        
        .checkbox-group {
            display: flex;
            gap: 5px;
        }
        
        .custom-checkbox {
            width: 22px;
            height: 22px;
            border: 2px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            position: relative;
            font-size: 0.75rem;
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
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
        }
        
        .progress-container {
            margin: 20px 0;
        }
        
        .progress-bar {
            width: 100%;
            height: 20px;
            background: #ecf0f1;
            border-radius: 10px;
            margin: 10px 0;
            overflow: hidden;
            position: relative;
        }
        
        .progress-fill {
            height: 100%;
            width: 0%;
            transition: width 0.5s ease;
            border-radius: 10px;
        }
        
        .physics-progress {
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
        }
        
        .math-progress {
            background: linear-gradient(45deg, #4834d4, #686de0);
        }
        
        .overall-progress {
            background: linear-gradient(45deg, #00b894, #00cec9);
        }
        
        .progress-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-weight: 600;
            font-size: 0.85rem;
            text-shadow: 0 1px 2px rgba(0,0,0,0.3);
        }
        
        .progress-label {
            font-weight: 600;
            margin-bottom: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }
        
        .stat-card {
            background: linear-gradient(45deg, #74b9ff, #0984e3);
            color: white;
            padding: 15px 20px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .physics-stat {
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
        }
        
        .math-stat {
            background: linear-gradient(45deg, #4834d4, #686de0);
        }
        
        .sync-stat {
            background: linear-gradient(45deg, #00b894, #00cec9);
            cursor: pointer;
        }
        
        .reset-stat {
            background: linear-gradient(45deg, #e17055, #d63031);
            cursor: pointer;
        }
        
        .stat-number {
            font-size: 1.8rem;
            font-weight: bold;
            display: block;
        }
        
        .stat-label {
            font-size: 0.85rem;
            opacity: 0.9;
            margin-top: 5px;
        }
        
        .sync-indicator {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 10px 15px;
            border-radius: 20px;
            color: white;
            font-weight: 600;
            font-size: 0.9rem;
            z-index: 1000;
            opacity: 0;
            transition: all 0.3s ease;
        }
        
        .sync-indicator.show {
            opacity: 1;
        }
        
        .sync-success {
            background: linear-gradient(45deg, #00b894, #00cec9);
        }
        
        .sync-error {
            background: linear-gradient(45deg, #e17055, #d63031);
        }
        
        .sync-loading {
            background: linear-gradient(45deg, #74b9ff, #0984e3);
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 15px;
                margin: 10px;
            }
            
            .setup-input {
                flex-direction: column;
                align-items: stretch;
            }
            
            .setup-input input {
                min-width: auto;
            }
            
            table {
                font-size: 0.75rem;
            }
            
            th, td {
                padding: 6px 4px;
            }
            
            .physics-cell, .math-cell {
                min-width: 140px;
                padding-left: 8px;
            }
            
            .checkbox-cell {
                min-width: 120px;
            }
            
            .custom-checkbox {
                width: 18px;
                height: 18px;
                font-size: 0.7rem;
            }
            
            .subject-label {
                font-size: 0.7rem;
                min-width: 35px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .legend {
                flex-direction: column;
                align-items: center;
            }
            
            .stats {
                grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            }
            
            .sync-indicator {
                top: 10px;
                right: 10px;
                font-size: 0.8rem;
                padding: 8px 12px;
            }
        }
    </style>
</head>
<body>
    <div class="sync-indicator" id="syncIndicator"></div>
    
    <div class="container">
        <h1>📚 45-Day Study Timetable</h1>
        <p class="subtitle">Physics (2.5 hrs/day) • Mathematics (3.5 hrs/day) • May 28 - July 11, 2025</p>
        
        <div class="setup-section">
            <h3>☁️ Google Sheets Integration</h3>
            <div class="setup-steps">
                <p><strong>Setup Instructions:</strong></p>
                <ol>
                    <li>Create a new Google Sheet with columns: Day, Date, Physics, Math</li>
                    <li>Go to Extensions → Apps Script in your Google Sheet</li>
                    <li>Replace the default code with the provided script (see instructions below)</li>
                    <li>Deploy as Web App and copy the URL</li>
                    <li>Paste the URL below and click Connect</li>
                </ol>
            </div>
            <div class="setup-input">
                <input type="text" id="sheetUrl" placeholder="Paste your Google Apps Script Web App URL here..." value="">
                <button onclick="connectToSheet()">Connect</button>
                <button onclick="testConnection()" style="background: #fdcb6e;">Test</button>
            </div>
            <div class="connection-status status-disconnected" id="connectionStatus">
                ❌ Not Connected - Enter your Google Sheet URL above
            </div>
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
            <div class="stat-card physics-stat">
                <span class="stat-number" id="physicsCompleted">0</span>
                <span class="stat-label">🔬 Physics Completed</span>
            </div>
            <div class="stat-card math-stat">
                <span class="stat-number" id="mathCompleted">0</span>
                <span class="stat-label">📐 Math Completed</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" id="totalHours">0</span>
                <span class="stat-label">Total Hours Studied</span>
            </div>
            <div class="stat-card">
                <span class="stat-number" id="overallProgress">0%</span>
                <span class="stat-label">Overall Progress</span>
            </div>
            <div class="stat-card sync-stat" onclick="syncWithSheet()" title="Sync with Google Sheets">
                <span class="stat-number">☁️</span>
                <span class="stat-label">Sync Now</span>
            </div>
            <div class="stat-card reset-stat" onclick="clearAllData()" title="Clear all progress data">
                <span class="stat-number">🗑️</span>
                <span class="stat-label">Reset Data</span>
            </div>
        </div>
        
        <div class="progress-container">
            <div class="progress-label">
                <span>🔬 Physics Progress</span>
                <span id="physicsProgressText">0/45</span>
            </div>
            <div class="progress-bar">
                <div class="progress-fill physics-progress" id="physicsProgressFill"></div>
            </div>
            
            <div class="progress-label">
                <span>📐 Mathematics Progress</span>
                <span id="mathProgressText">0/45</span>
            </div>
            <div class="progress-bar">
                <div class="progress-fill math-progress" id="mathProgressFill"></div>
            </div>
            
            <div class="progress-label">
                <span>📊 Overall Progress</span>
                <span id="overallProgressText">0/90</span>
            </div>
            <div class="progress-bar">
                <div class="progress-fill overall-progress" id="overallProgressFill"></div>
            </div>
        </div>
        
        <table>
            <thead>
                <tr>
                    <th>Day</th>
                    <th>Date</th>
                    <th>🔬 Physics Topics (2.5 hrs)</th>
                    <th>📐 Mathematics Topics (3.5 hrs)</th>
                    <th>Progress Tracking</th>
                </tr>
            </thead>
            <tbody id="timetableBody">
                <!-- Table content will be generated by JavaScript -->
            </tbody>
        </table>
        
        <div class="setup-section" style="margin-top: 30px;">
            <h3>📋 Google Apps Script Code</h3>
            <div class="setup-steps">
                <p><strong>Copy this code to your Google Apps Script:</strong></p>
                <pre style="background: rgba(255,255,255,0.1); padding: 15px; border-radius: 8px; overflow-x: auto; font-size: 0.9rem; line-height: 1.4;">
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSheet();
  const data = JSON.parse(e.postData.contents);
  
  // Clear existing data (except headers)
  if (sheet.getLastRow() > 1) {
    sheet.deleteRows(2, sheet.getLastRow() - 1);
  }
  
  // Set headers if not present
  if (sheet.getLastRow() === 0) {
    sheet.getRange(1, 1, 1, 4).setValues([['Day', 'Date', 'Physics', 'Math']]);
  }
  
  // Add data
  const rows = [];
  Object.keys(data).forEach(key => {
    const [day, date] = key.split('|');
    const progress = data[key];
    rows.push([day, date, progress.physics || '', progress.math || '']);
  });
  
  if (rows.length > 0) {
    sheet.getRange(2, 1, rows.length, 4).setValues(rows);
  }
  
  return ContentService.createTextOutput(JSON.stringify({success: true}));
}

function doGet() {
  const sheet = SpreadsheetApp.getActiveSheet();
  const data = sheet.getDataRange().getValues();
  
  if (data.length <= 1) return ContentService.createTextOutput(JSON.stringify({}));
  
  const result = {};
  for (let i = 1; i < data.length; i++) {
    const [day, date, physics, math] = data[i];
    if (day && date) {
      const key = `${day}|${date}`;
      result[key] = {
        physics: physics || '',
        math: math || ''
      };
    }
  }
  
  return ContentService.createTextOutput(JSON.stringify(result));
}
                </pre>
            </div>
        </div>
    </div>

    <script>
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

        let googleSheetUrl = '';
        let isConnected = false;

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
                        <div class="subject-checkbox-container">
                            <div class="checkbox-row">
                                <span class="subject-label physics-label">PHY:</span>
                                <div class="checkbox-group">
                                    <div class="custom-checkbox" data-day="${i + 1}" data-date="${formatDate(dates[i])}" data-subject="physics" data-type="check" title="Physics completed successfully">✓</div>
                                    <div class="custom-checkbox" data-day="${i + 1}" data-date="${formatDate(dates[i])}" data-subject="physics" data-type="cross" title="Physics not completed">✗</div>
                                </div>
                            </div>
                            <div class="checkbox-row">
                                <span class="subject-label math-label">MATH:</span>
                                <div class="checkbox-group">
                                    <div class="custom-checkbox" data-day="${i + 1}" data-date="${formatDate(dates[i])}" data-subject="math" data-type="check" title="Math completed successfully">✓</div>
                                    <div class="custom-checkbox" data-day="${i + 1}" data-date="${formatDate(dates[i])}" data-subject="math" data-type="cross" title="Math not completed">✗</div>
                                </div>
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

        // Connect to Google Sheet
        function connectToSheet() {
            const url = document.getElementById('sheetUrl').value.trim();
            if (!url) {
                alert('Please enter your Google Apps Script URL');
                return;
            }
            
            googleSheetUrl = url;
            localStorage.setItem('googleSheetUrl', url);
            
            testConnection();
        }

        // Test connection to Google Sheet
        async function testConnection() {
            if (!googleSheetUrl) {
                showSyncIndicator('Please connect to Google Sheets first', 'error');
                return;
            }
            
            showSyncIndicator('Testing connection...', 'loading');
            
            try {
                const response = await fetch(googleSheetUrl);
                const data = await response.json();
                
                isConnected = true;
                updateConnectionStatus(true);
                showSyncIndicator('Connected successfully!', 'success');
                
                // Load data from sheet
                loadFromSheet(data);
                
            } catch (error) {
                isConnected = false;
                updateConnectionStatus(false);
                showSyncIndicator('Connection failed. Check your URL.', 'error');
                console.error('Connection error:',
