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
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📚 45-Day Study Timetable</h1>
        <p class="subtitle">Physics (2.5 hrs/day) • Mathematics (3.5 hrs/day) • May 25 - July 8, 2025</p>
        
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

        // Generate dates starting from May 25, 2025
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
            const startDate = new Date('2025-05-25');
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

        // Handle checkbox clicks
        function handleCheckboxClick(event) {
            const clickedBox = event.currentTarget;
            const day = clickedBox.dataset.day;
            const type = clickedBox.dataset.type;
            
            // Find the other checkbox in the same row
            const otherBox = document.querySelector(
                `.custom-checkbox[data-day="${day}"][data-type="${type === 'check' ? 'cross' : 'check'}"]`
            );
            
            // Toggle clicked checkbox
            if (clickedBox.classList.contains(type === 'check' ? 'checked' : 'crossed')) {
                clickedBox.classList.remove(type === 'check' ? 'checked' : 'crossed');
            } else {
                clickedBox.classList.add(type === 'check' ? 'checked' : 'crossed');
                // Remove the other checkbox state
                otherBox.classList.remove(type === 'check' ? 'crossed' : 'checked');
            }
            
            updateStats();
        }

        // Update statistics
        function updateStats() {
            const totalDays = 45;
            const checkedBoxes = document.querySelectorAll('.custom-checkbox.checked').length;
            const crossedBoxes = document.querySelectorAll('.custom-checkbox.crossed').length;
            const completedDays = checkedBoxes + crossedBoxes;
            const totalHours = checkedBoxes * 6; // 6 hours per successful day
            const successRate = completedDays > 0 ? Math.round((checkedBoxes / completedDays) * 100) : 0;
            
            document.getElementById('completedDays').textContent = completedDays;
            document.getElementById('totalHours').textContent = totalHours;
            document.getElementById('successRate').textContent = successRate + '%';
            
            // Update progress bar
            const progressPercentage = Math.round((completedDays / totalDays) * 100);
            document.getElementById('progressFill').style.width = progressPercentage + '%';
            document.getElementById('progressText').textContent = progressPercentage + '% Complete';
        }

        // Initialize the timetable
        generateTimetable();
        updateStats();
    </script>
</body>
</html>
