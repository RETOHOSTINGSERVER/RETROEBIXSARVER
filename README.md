<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EBIXCONSOLPORTAL - Admin Portal</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            background-color: #f0f0f0;
            color: #333;
        }
        
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #333;
        }
        
        .login-box {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
            width: 350px;
            text-align: center;
        }
        
        .login-box h2 {
            margin-bottom: 20px;
            color: #444;
        }
        
        .login-box input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        
        .login-box button {
            width: 100%;
            padding: 12px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 10px;
        }
        
        .login-box button:hover {
            background-color: #45a049;
        }
        
        .footer {
            margin-top: 20px;
            font-size: 12px;
            color: #777;
        }
        
        /* Admin Dashboard Styles */
        .admin-dashboard {
            display: none;
            background-color: #333;
            color: white;
            min-height: 100vh;
        }
        
        .header {
            background-color: #222;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .clock {
            font-size: 18px;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .user-info button {
            padding: 5px 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }
        
        .main-content {
            padding: 20px;
            background-color: #444;
        }
        
        .form-section {
            background-color: #555;
            padding: 20px;
            border-radius: 5px;
            margin-bottom: 20px;
        }
        
        .form-section h3 {
            margin-bottom: 15px;
            color: #4CAF50;
        }
        
        .form-row {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-group {
            flex: 1;
            min-width: 200px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: #ddd;
        }
        
        .form-group input, .form-group select {
            width: 100%;
            padding: 8px;
            border: 1px solid #777;
            border-radius: 4px;
            background-color: #666;
            color: white;
        }
        
        .status-options {
            display: flex;
            gap: 15px;
            margin-top: 10px;
            flex-wrap: wrap;
        }
        
        .status-option {
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .action-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
            flex-wrap: wrap;
        }
        
        .action-buttons button {
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        
        .save-btn {
            background-color: #4CAF50;
            color: white;
        }
        
        .print-btn {
            background-color: #2196F3;
            color: white;
        }
        
        .delete-btn {
            background-color: #f44336;
            color: white;
        }
        
        .file-upload {
            margin-top: 20px;
        }
        
        .file-upload label {
            display: block;
            margin-bottom: 5px;
            color: #ddd;
        }
        
        .records-summary {
            background-color: #555;
            padding: 15px;
            border-radius: 5px;
            margin-top: 20px;
        }
        
        .summary-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
            flex-wrap: wrap;
        }
        
        .summary-item {
            text-align: center;
            flex: 1;
            min-width: 120px;
            margin: 5px 0;
        }
        
        .summary-count {
            font-size: 24px;
            font-weight: bold;
            color: #4CAF50;
        }
        
        .records-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background-color: #666;
        }
        
        .records-table th, .records-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #777;
        }
        
        .records-table th {
            background-color: #444;
            color: #4CAF50;
        }
        
        .records-table tr:hover {
            background-color: #555;
        }
        
        .filter-section {
            margin-bottom: 20px;
            display: flex;
            gap: 10px;
            align-items: center;
            flex-wrap: wrap;
        }
        
        .filter-section select, .filter-section button, .filter-section input {
            padding: 8px 12px;
            border-radius: 4px;
            border: none;
        }
        
        .filter-section button {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        
        .filter-section input {
            background-color: #666;
            color: white;
            border: 1px solid #777;
            flex: 1;
            min-width: 200px;
        }
        
        .view-records-btn {
            background-color: #2196F3;
            color: white;
            padding: 10px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 20px;
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            overflow: auto;
        }
        
        .modal-content {
            background-color: #555;
            margin: 5% auto;
            padding: 20px;
            width: 80%;
            max-width: 900px;
            border-radius: 5px;
        }
        
        .close-btn {
            float: right;
            font-size: 24px;
            cursor: pointer;
        }
        
        /* Change Password Modal */
        .change-password-modal {
            display: none;
        }
        
        .change-password-form, .change-username-form, .assign-engineer-form {
            margin-top: 20px;
        }
        
        .change-password-form input, 
        .change-username-form input,
        .assign-engineer-form select,
        .assign-engineer-form input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 4px;
            border: 1px solid #777;
            background-color: #666;
            color: white;
        }
        
        .change-password-form button, 
        .change-username-form button,
        .assign-engineer-form button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        
        /* Print Styles */
        @media print {
            body * {
                visibility: hidden;
            }
            #print-section, #print-section * {
                visibility: visible;
            }
            #print-section {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                background-color: white;
                color: black;
                padding: 20px;
            }
            .no-print {
                display: none;
            }
        }

        /* Engineer assignment section */
        .engineer-assignment {
            margin-top: 20px;
            background-color: #555;
            padding: 15px;
            border-radius: 5px;
        }

        .engineer-info {
            display: flex;
            gap: 10px;
            align-items: center;
            margin-top: 10px;
        }

        .engineer-info span {
            font-weight: bold;
            color: #4CAF50;
        }

        .assign-btn {
            background-color: #2196F3;
            color: white;
            padding: 5px 10px;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }

        /* Records Statistics Section */
        .records-stats {
            background-color: #555;
            padding: 20px;
            border-radius: 5px;
            margin-top: 20px;
        }
        
        .stats-filters {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }
        
        .stats-filters select {
            padding: 8px 12px;
            border-radius: 4px;
            border: none;
            background-color: #666;
            color: white;
        }
        
        .stats-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            background-color: #666;
        }
        
        .stats-table th, .stats-table td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #777;
        }
        
        .stats-table th {
            background-color: #444;
            color: #4CAF50;
        }
        
        .stats-actions {
            margin-top: 15px;
            display: flex;
            gap: 10px;
        }
        
        .stats-actions button {
            padding: 8px 15px;
            background-color: #2196F3;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Login Section -->
    <div class="login-container" id="login-section">
        <div class="login-box">
            <h2>Admin Login</h2>
            <input type="text" id="username" placeholder="Username" required>
            <input type="password" id="password" placeholder="Password" required>
            <button onclick="login()">Login</button>
            <div class="footer">
                All Rights Reserved By Dev Makwana EBIXCONSOLPORTAL
            </div>
        </div>
    </div>
    
    <!-- Admin Dashboard -->
    <div class="admin-dashboard" id="admin-dashboard">
        <div class="header">
            <div class="logo">EBIXCONSOLPORTAL</div>
            <div class="clock" id="live-clock"></div>
            <div class="user-info">
                <span id="welcome-message">Welcome, Admin</span>
                <button onclick="openChangeUsernameModal()">Change Username</button>
                <button onclick="openChangePasswordModal()">Change Password</button>
                <button onclick="logout()">Logout</button>
            </div>
        </div>
        
        <div class="main-content">
            <div class="filter-section">
                <select id="status-filter">
                    <option value="">All Records</option>
                    <option value="accept">Accept</option>
                    <option value="hold">Hold</option>
                    <option value="running">Running</option>
                    <option value="public-holiday">Public Holiday</option>
                </select>
                <select id="customer-name-filter">
                    <option value="">All Customers</option>
                    <!-- Customer names will be populated by JavaScript -->
                </select>
                <input type="text" id="search-input" placeholder="Search by name, number, etc.">
                <button onclick="filterRecords()">Filter</button>
                <button onclick="clearFilters()">Clear Filters</button>
            </div>
            
            <div class="form-section">
                <h3>Customer Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label for="customer-number">Customer Number</label>
                        <input type="text" id="customer-number" placeholder="Enter customer number">
                    </div>
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" placeholder="Enter name">
                    </div>
                    <div class="form-group">
                        <label for="surname">Surname</label>
                        <input type="text" id="surname" placeholder="Enter surname">
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="email">Email ID</label>
                        <input type="email" id="email" placeholder="Enter email">
                    </div>
                    <div class="form-group">
                        <label for="contact">Contact Number</label>
                        <input type="tel" id="contact" placeholder="Enter contact number">
                    </div>
                    <div class="form-group">
                        <label for="pincode">Pin Code</label>
                        <input type="text" id="pincode" placeholder="Enter pin code">
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="address">Address</label>
                        <input type="text" id="address" placeholder="Enter address">
                    </div>
                    <div class="form-group">
                        <label for="city">City/Village</label>
                        <input type="text" id="city" placeholder="Enter city/village">
                    </div>
                    <div class="form-group">
                        <label for="state">State</label>
                        <input type="text" id="state" placeholder="Enter state">
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Country</label>
                    <input type="text" id="country" value="India" readonly>
                </div>
                
                <div class="action-buttons">
                    <button class="save-btn" onclick="saveCustomerInfo()">Save Customer Info</button>
                </div>
            </div>
            
            <div class="form-section">
                <h3>Machine Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label for="machine-name">Machine Name</label>
                        <input type="text" id="machine-name" placeholder="Enter machine name">
                    </div>
                    <div class="form-group">
                        <label for="serial-number">Serial Number</label>
                        <input type="text" id="serial-number" placeholder="Enter serial number">
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Machine Status</label>
                    <div class="status-options">
                        <div class="status-option">
                            <input type="radio" id="warranty" name="machine-status" value="warranty" checked>
                            <label for="warranty">Under Warranty</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="out-of-warranty" name="machine-status" value="out-of-warranty">
                            <label for="out-of-warranty">Out of Warranty</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="amc" name="machine-status" value="amc">
                            <label for="amc">AMC</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Record Status</label>
                    <div class="status-options">
                        <div class="status-option">
                            <input type="radio" id="accept" name="record-status" value="accept" checked>
                            <label for="accept">Accept</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="hold" name="record-status" value="hold">
                            <label for="hold">Hold</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="running" name="record-status" value="running">
                            <label for="running">Running</label>
                        </div>
                        <div class="status-option">
                            <input type="radio" id="public-holiday" name="record-status" value="public-holiday">
                            <label for="public-holiday">Public Holiday</label>
                        </div>
                    </div>
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="customer-remark">Customer Remark</label>
                        <input type="text" id="customer-remark" placeholder="Enter customer remark">
                    </div>
                    <div class="form-group">
                        <label for="parts-change-remark">Parts Change Remark</label>
                        <input type="text" id="parts-change-remark" placeholder="Enter parts change remark">
                    </div>
                </div>
                
                <div class="file-upload">
                    <label for="invoice-upload">Upload Invoice</label>
                    <input type="file" id="invoice-upload">
                    
                    <label for="zip-upload" style="margin-top: 10px;">Upload ZIP File</label>
                    <input type="file" id="zip-upload">
                </div>
                
                <div class="action-buttons">
                    <button class="save-btn" onclick="saveMachineInfo()">Save Machine Info</button>
                    <button class="print-btn" onclick="printRecord()">Print Record</button>
                    <button class="delete-btn" onclick="deleteRecord()">Delete Record</button>
                </div>
            </div>

            <!-- Engineer Assignment Section -->
            <div class="engineer-assignment">
                <h3>Engineer Assignment</h3>
                <div id="assigned-engineer-display">
                    <p>No engineer assigned yet</p>
                </div>
                <button class="assign-btn" onclick="openAssignEngineerModal()">Assign Engineer</button>
            </div>
            
            <!-- Records Statistics Section -->
            <div class="records-stats">
                <h3>Monthly/Yearly Records</h3>
                <div class="stats-filters">
                    <select id="stats-year">
                        <option value="">All Years</option>
                        <!-- Years will be populated by JavaScript -->
                    </select>
                    <select id="stats-month">
                        <option value="">All Months</option>
                        <option value="1">January</option>
                        <option value="2">February</option>
                        <option value="3">March</option>
                        <option value="4">April</option>
                        <option value="5">May</option>
                        <option value="6">June</option>
                        <option value="7">July</option>
                        <option value="8">August</option>
                        <option value="9">September</option>
                        <option value="10">October</option>
                        <option value="11">November</option>
                        <option value="12">December</option>
                    </select>
                    <button onclick="updateStatsTable()">Show Records</button>
                </div>
                
                <table class="stats-table">
                    <thead>
                        <tr>
                            <th>Month/Year</th>
                            <th>Total Records</th>
                            <th>Accept</th>
                            <th>Hold</th>
                            <th>Running</th>
                            <th>Public Holiday</th>
                        </tr>
                    </thead>
                    <tbody id="stats-table-body">
                        <!-- Stats will be populated here -->
                    </tbody>
                </table>
                
                <div class="stats-actions">
                    <button onclick="saveStatsToCSV()">Save as CSV</button>
                    <button onclick="printStats()">Print Stats</button>
                </div>
            </div>
            
            <div class="records-summary">
                <h3>Records Summary</h3>
                <div class="summary-row">
                    <div class="summary-item">
                        <div class="summary-count" id="total-count">0</div>
                        <div>Total Records</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="accept-count">0</div>
                        <div>Accept</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="hold-count">0</div>
                        <div>Hold</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="running-count">0</div>
                        <div>Running</div>
                    </div>
                    <div class="summary-item">
                        <div class="summary-count" id="holiday-count">0</div>
                        <div>Public Holiday</div>
                    </div>
                </div>
            </div>
            
            <button class="view-records-btn" onclick="openRecordsModal()">View All Records</button>
        </div>
    </div>
    
    <!-- Records Modal -->
    <div id="records-modal" class="modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal('records-modal')">&times;</span>
            <h2>All Records</h2>
            <table class="records-table">
                <thead>
                    <tr>
                        <th>Customer No</th>
                        <th>Name</th>
                        <th>Contact</th>
                        <th>Machine</th>
                        <th>Serial No</th>
                        <th>Status</th>
                        <th>Assigned Engineer</th>
                        <th>Date</th>
                        <th class="no-print">Actions</th>
                    </tr>
                </thead>
                <tbody id="records-table-body">
                    <!-- Records will be populated here -->
                </tbody>
            </table>
        </div>
    </div>
    
    <!-- Print Section (hidden until printing) -->
    <div id="print-section" style="display: none;">
        <h2>Customer Record</h2>
        <div id="print-content"></div>
    </div>
    
    <!-- Change Password Modal -->
    <div id="change-password-modal" class="modal change-password-modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal('change-password-modal')">&times;</span>
            <h2>Change Password</h2>
            <div class="change-password-form">
                <input type="password" id="current-password" placeholder="Current Password">
                <input type="password" id="new-password" placeholder="New Password">
                <input type="password" id="confirm-password" placeholder="Confirm New Password">
                <button onclick="changePassword()">Change Password</button>
            </div>
        </div>
    </div>
    
    <!-- Change Username Modal -->
    <div id="change-username-modal" class="modal change-password-modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal('change-username-modal')">&times;</span>
            <h2>Change Username</h2>
            <div class="change-username-form">
                <input type="text" id="current-username" placeholder="Current Username">
                <input type="text" id="new-username" placeholder="New Username">
                <input type="password" id="username-password" placeholder="Current Password">
                <button onclick="changeUsername()">Change Username</button>
            </div>
        </div>
    </div>

    <!-- Assign Engineer Modal -->
    <div id="assign-engineer-modal" class="modal change-password-modal">
        <div class="modal-content">
            <span class="close-btn" onclick="closeModal('assign-engineer-modal')">&times;</span>
            <h2>Assign Engineer</h2>
            <div class="assign-engineer-form">
                <select id="engineer-select">
                    <option value="">Select Engineer</option>
                    <option value="EI102019004">Dev Makwana (EI102019004)</option>
                    <option value="EI102024889">Mahesh Gupta (EI102024889)</option>
                    <option value="EI011409023">Arvind Sukhla (EI011409023)</option>
                </select>
                <input type="text" id="customer-number-for-assignment" placeholder="Customer Number" readonly>
                <button onclick="assignEngineer()">Assign Engineer</button>
            </div>
        </div>
    </div>
    
    <script>
        // Sample records data
        let records = [];
        let currentUsername = 'devmakwana12';
        let currentPassword = '12345';
        
        // Engineer data
        const engineers = {
            'EI102019004': { name: 'Dev Makwana', id: 'EI102019004' },
            'EI102024889': { name: 'Mahesh Gupta', id: 'EI102024889' },
            'EI011409023': { name: 'Arvind Sukhla', id: 'EI011409023' }
        };
        
        // Update clock every second
        function updateClock() {
            const now = new Date();
            const options = { 
                timeZone: 'Asia/Kolkata',
                hour12: true,
                hour: '2-digit',
                minute: '2-digit',
                second: '2-digit',
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            };
            const formatter = new Intl.DateTimeFormat('en-IN', options);
            const parts = formatter.formatToParts(now);
            
            let dateTime = {};
            parts.forEach(part => {
                dateTime[part.type] = part.value;
            });
            
            const clockStr = `${dateTime.day}/${dateTime.month}/${dateTime.year} ${dateTime.hour}:${dateTime.minute}:${dateTime.second} ${dateTime.dayPeriod}`;
            document.getElementById('live-clock').textContent = clockStr;
        }
        
        setInterval(updateClock, 1000);
        updateClock();
        
        // Login function
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === currentUsername && password === currentPassword) {
                document.getElementById('login-section').style.display = 'none';
                document.getElementById('admin-dashboard').style.display = 'block';
                document.getElementById('welcome-message').textContent = `Welcome, ${currentUsername}`;
                updateSummary();
            } else {
                alert('Invalid username or password');
            }
        }
        
        // Logout function
        function logout() {
            document.getElementById('login-section').style.display = 'flex';
            document.getElementById('admin-dashboard').style.display = 'none';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        }
        
        // Save customer information
        function saveCustomerInfo() {
            const customerNumber = document.getElementById('customer-number').value;
            const name = document.getElementById('name').value;
            const surname = document.getElementById('surname').value;
            const email = document.getElementById('email').value;
            const contact = document.getElementById('contact').value;
            const address = document.getElementById('address').value;
            const city = document.getElementById('city').value;
            const state = document.getElementById('state').value;
            const pincode = document.getElementById('pincode').value;
            
            if (!customerNumber || !name || !contact) {
                alert('Please fill in required fields: Customer Number, Name, and Contact');
                return;
            }
            
            // Check if this is an existing record
            const existingIndex = records.findIndex(r => r.customerNumber === customerNumber);
            
            if (existingIndex >= 0) {
                // Update existing record
                records[existingIndex] = {
                    ...records[existingIndex],
                    name,
                    surname,
                    email,
                    contact,
                    address,
                    city,
                    state,
                    pincode,
                    updatedAt: new Date().toISOString()
                };
            } else {
                // Create new record with just customer info (machine info will be added later)
                records.push({
                    customerNumber,
                    name,
                    surname,
                    email,
                    contact,
                    address,
                    city,
                    state,
                    pincode,
                    country: 'India',
                    createdAt: new Date().toISOString(),
                    updatedAt: new Date().toISOString(),
                    status: 'accept', // default status
                    assignedEngineer: null
                });
            }
            
            alert('Customer information saved successfully');
            updateSummary();
            updateAssignedEngineerDisplay(customerNumber);
        }
        
        // Save machine information
        function saveMachineInfo() {
            const customerNumber = document.getElementById('customer-number').value;
            const machineName = document.getElementById('machine-name').value;
            const serialNumber = document.getElementById('serial-number').value;
            const machineStatus = document.querySelector('input[name="machine-status"]:checked').value;
            const recordStatus = document.querySelector('input[name="record-status"]:checked').value;
            const customerRemark = document.getElementById('customer-remark').value;
            const partsChangeRemark = document.getElementById('parts-change-remark').value;
            
            if (!customerNumber) {
                alert('Please save customer information first');
                return;
            }
            
            if (!machineName || !serialNumber) {
                alert('Please fill in machine name and serial number');
                return;
            }
            
            const recordIndex = records.findIndex(r => r.customerNumber === customerNumber);
            
            if (recordIndex >= 0) {
                records[recordIndex] = {
                    ...records[recordIndex],
                    machineName,
                    serialNumber,
                    machineStatus,
                    status: recordStatus,
                    customerRemark,
                    partsChangeRemark,
                    updatedAt: new Date().toISOString()
                };
                
                alert('Machine information saved successfully');
                updateSummary();
            } else {
                alert('Please save customer information first');
            }
        }
        
        // Update summary counts
        function updateSummary() {
            document.getElementById('total-count').textContent = records.length;
            document.getElementById('accept-count').textContent = records.filter(r => r.status === 'accept').length;
            document.getElementById('hold-count').textContent = records.filter(r => r.status === 'hold').length;
            document.getElementById('running-count').textContent = records.filter(r => r.status === 'running').length;
            document.getElementById('holiday-count').textContent = records.filter(r => r.status === 'public-holiday').length;
            
            // Initialize the filters
            initCustomerNameFilter();
            initYearFilter();
            updateStatsTable();
        }
        
        // Initialize customer name filter dropdown
        function initCustomerNameFilter() {
            const customerFilter = document.getElementById('customer-name-filter');
            customerFilter.innerHTML = '<option value="">All Customers</option>';
            
            const customerNames = [...new Set(records.map(r => r.name))].sort();
            
            customerNames.forEach(name => {
                const option = document.createElement('option');
                option.value = name;
                option.textContent = name;
                customerFilter.appendChild(option);
            });
        }
        
        // Initialize year filter dropdown
        function initYearFilter() {
            const yearFilter = document.getElementById('stats-year');
            yearFilter.innerHTML = '<option value="">All Years</option>';
            
            const years = [...new Set(records.map(r => new Date(r.createdAt).getFullYear()))].sort((a, b) => b - a);
            
            years.forEach(year => {
                const option = document.createElement('option');
                option.value = year;
                option.textContent = year;
                yearFilter.appendChild(option);
            });
        }
        
        // Update stats table based on filters
        function updateStatsTable() {
            const year = document.getElementById('stats-year').value;
            const month = document.getElementById('stats-month').value;
            
            let filteredRecords = records;
            
            if (year) {
                filteredRecords = filteredRecords.filter(r => new Date(r.createdAt).getFullYear() == year);
            }
            
            if (month) {
                filteredRecords = filteredRecords.filter(r => new Date(r.createdAt).getMonth() + 1 == month);
            }
            
            const statsBody = document.getElementById('stats-table-body');
            statsBody.innerHTML = '';
            
            if (!year && !month) {
                // Show yearly summary
                const years = [...new Set(records.map(r => new Date(r.createdAt).getFullYear()))].sort((a, b) => b - a);
                
                years.forEach(year => {
                    const yearRecords = records.filter(r => new Date(r.createdAt).getFullYear() == year);
                    
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${year}</td>
                        <td>${yearRecords.length}</td>
                        <td>${yearRecords.filter(r => r.status === 'accept').length}</td>
                        <td>${yearRecords.filter(r => r.status === 'hold').length}</td>
                        <td>${yearRecords.filter(r => r.status === 'running').length}</td>
                        <td>${yearRecords.filter(r => r.status === 'public-holiday').length}</td>
                    `;
                    statsBody.appendChild(row);
                });
            } else if (year && !month) {
                // Show monthly summary for selected year
                for (let m = 1; m <= 12; m++) {
                    const monthRecords = filteredRecords.filter(r => new Date(r.createdAt).getMonth() + 1 == m);
                    const monthNames = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
                    
                    if (monthRecords.length > 0) {
                        const row = document.createElement('tr');
                        row.innerHTML = `
                            <td>${monthNames[m-1]} ${year}</td>
                            <td>${monthRecords.length}</td>
                            <td>${monthRecords.filter(r => r.status === 'accept').length}</td>
                            <td>${monthRecords.filter(r => r.status === 'hold').length}</td>
                            <td>${monthRecords.filter(r => r.status === 'running').length}</td>
                            <td>${monthRecords.filter(r => r.status === 'public-holiday').length}</td>
                        `;
                        statsBody.appendChild(row);
                    }
                }
            } else {
                // Show detailed records for selected month/year
                const monthNames = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
                const monthName = monthNames[parseInt(month)-1];
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${monthName} ${year}</td>
                    <td>${filteredRecords.length}</td>
                    <td>${filteredRecords.filter(r => r.status === 'accept').length}</td>
                    <td>${filteredRecords.filter(r => r.status === 'hold').length}</td>
                    <td>${filteredRecords.filter(r => r.status === 'running').length}</td>
                    <td>${filteredRecords.filter(r => r.status === 'public-holiday').length}</td>
                `;
                statsBody.appendChild(row);
            }
        }
        
        // Save stats to CSV
        function saveStatsToCSV() {
            const year = document.getElementById('stats-year').value;
            const month = document.getElementById('stats-month').value;
            
            let csvContent = "Month/Year,Total Records,Accept,Hold,Running,Public Holiday\n";
            
            const rows = document.querySelectorAll('#stats-table-body tr');
            rows.forEach(row => {
                const cols = row.querySelectorAll('td');
                const rowData = Array.from(cols).map(col => col.textContent).join(',');
                csvContent += rowData + '\n';
            });
            
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.setAttribute('href', url);
            
            let fileName = 'records_stats';
            if (year) fileName += `_${year}`;
            if (month) fileName += `_${month}`;
            fileName += '.csv';
            
            link.setAttribute('download', fileName);
            link.style.visibility = 'hidden';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
        
        // Print stats
        function printStats() {
            const printWindow = window.open('', '', 'width=800,height=600');
            printWindow.document.write('<html><head><title>Records Statistics</title>');
            printWindow.document.write('<style>table {border-collapse: collapse; width: 100%;} th, td {border: 1px solid #ddd; padding: 8px; text-align: left;} th {background-color: #f2f2f2;}</style>');
            printWindow.document.write('</head><body>');
            printWindow.document.write('<h2>Records Statistics</h2>');
            
            const year = document.getElementById('stats-year').value;
            const month = document.getElementById('stats-month').value;
            if (year) printWindow.document.write(`<p>Year: ${year}</p>`);
            if (month) {
                const monthNames = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
                printWindow.document.write(`<p>Month: ${monthNames[parseInt(month)-1]}</p>`);
            }
            
            printWindow.document.write(document.querySelector('.stats-table').outerHTML);
            printWindow.document.write('</body></html>');
            printWindow.document.close();
            printWindow.focus();
            setTimeout(() => {
                printWindow.print();
                printWindow.close();
            }, 500);
        }
        
        // Filter records
        function filterRecords() {
            const status = document.getElementById('status-filter').value;
            const customerName = document.getElementById('customer-name-filter').value;
            const searchTerm = document.getElementById('search-input').value.toLowerCase();
            
            let filteredRecords = records;
            
            if (status) {
                filteredRecords = filteredRecords.filter(r => r.status === status);
            }
            
            if (customerName) {
                filteredRecords = filteredRecords.filter(r => r.name === customerName);
            }
            
            if (searchTerm) {
                filteredRecords = filteredRecords.filter(r => 
                    (r.customerNumber && r.customerNumber.toLowerCase().includes(searchTerm)) ||
                    (r.name && r.name.toLowerCase().includes(searchTerm)) ||
                    (r.surname && r.surname.toLowerCase().includes(searchTerm)) ||
                    (r.contact && r.contact.toLowerCase().includes(searchTerm)) ||
                    (r.machineName && r.machineName.toLowerCase().includes(searchTerm)) ||
                    (r.serialNumber && r.serialNumber.toLowerCase().includes(searchTerm)) ||
                    (r.assignedEngineer && r.assignedEngineer.name.toLowerCase().includes(searchTerm)) ||
                    (r.assignedEngineer && r.assignedEngineer.id.toLowerCase().includes(searchTerm))
                );
            }
            
            updateRecordsTable(filteredRecords);
            updateSummaryCounts(filteredRecords);
        }
        
        // Update records table
        function updateRecordsTable(recordsToShow) {
            const tbody = document.getElementById('records-table-body');
            
            // Clear existing rows
            tbody.innerHTML = '';
            
            // Add records to table
            recordsToShow.forEach(record => {
                const row = document.createElement('tr');
                
                const date = new Date(record.updatedAt);
                const dateStr = `${date.getDate()}/${date.getMonth()+1}/${date.getFullYear()}`;
                
                const engineerInfo = record.assignedEngineer 
                    ? `${record.assignedEngineer.name} (${record.assignedEngineer.id})` 
                    : 'Not assigned';
                
                row.innerHTML = `
                    <td>${record.customerNumber}</td>
                    <td>${record.name} ${record.surname || ''}</td>
                    <td>${record.contact}</td>
                    <td>${record.machineName || '-'}</td>
                    <td>${record.serialNumber || '-'}</td>
                    <td>${record.status ? record.status.charAt(0).toUpperCase() + record.status.slice(1).replace('-', ' ') : '-'}</td>
                    <td>${engineerInfo}</td>
                    <td>${dateStr}</td>
                    <td class="no-print">
                        <button onclick="loadRecord('${record.customerNumber}')" style="padding: 5px 10px; background-color: #2196F3; color: white; border: none; border-radius: 3px; cursor: pointer;">Load</button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
        }
        
        // Update summary counts
        function updateSummaryCounts(filteredRecords) {
            document.getElementById('total-count').textContent = filteredRecords.length;
            document.getElementById('accept-count').textContent = filteredRecords.filter(r => r.status === 'accept').length;
            document.getElementById('hold-count').textContent = filteredRecords.filter(r => r.status === 'hold').length;
            document.getElementById('running-count').textContent = filteredRecords.filter(r => r.status === 'running').length;
            document.getElementById('holiday-count').textContent = filteredRecords.filter(r => r.status === 'public-holiday').length;
        }
        
        // Clear filters
        function clearFilters() {
            document.getElementById('status-filter').value = '';
            document.getElementById('customer-name-filter').value = '';
            document.getElementById('search-input').value = '';
            updateRecordsTable(records);
            updateSummaryCounts(records);
        }
        
        // Load record into form
        function loadRecord(customerNumber) {
            const record = records.find(r => r.customerNumber === customerNumber);
            
            if (record) {
                document.getElementById('customer-number').value = record.customerNumber || '';
                document.getElementById('name').value = record.name || '';
                document.getElementById('surname').value = record.surname || '';
                document.getElementById('email').value = record.email || '';
                document.getElementById('contact').value = record.contact || '';
                document.getElementById('address').value = record.address || '';
                document.getElementById('city').value = record.city || '';
                document.getElementById('state').value = record.state || '';
                document.getElementById('pincode').value = record.pincode || '';
                
                document.getElementById('machine-name').value = record.machineName || '';
                document.getElementById('serial-number').value = record.serialNumber || '';
                
                // Set machine status radio
                if (record.machineStatus) {
                    document.querySelector(`input[name="machine-status"][value="${record.machineStatus}"]`).checked = true;
                }
                
                // Set record status radio
                if (record.status) {
                    document.querySelector(`input[name="record-status"][value="${record.status}"]`).checked = true;
                }
                
                document.getElementById('customer-remark').value = record.customerRemark || '';
                document.getElementById('parts-change-remark').value = record.partsChangeRemark || '';
                
                // Update assigned engineer display
                updateAssignedEngineerDisplay(record.customerNumber);
                
                closeModal('records-modal');
            }
        }
        
        // Open records modal
        function openRecordsModal() {
            const modal = document.getElementById('records-modal');
            updateRecordsTable(records);
            modal.style.display = 'block';
        }
        
        // Close modal
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        // Open change password modal
        function openChangePasswordModal() {
            document.getElementById('current-password').value = '';
            document.getElementById('new-password').value = '';
            document.getElementById('confirm-password').value = '';
            document.getElementById('change-password-modal').style.display = 'block';
        }
        
        // Open change username modal
        function openChangeUsernameModal() {
            document.getElementById('current-username').value = currentUsername;
            document.getElementById('new-username').value = '';
            document.getElementById('username-password').value = '';
            document.getElementById('change-username-modal').style.display = 'block';
        }

        // Open assign engineer modal
        function openAssignEngineerModal() {
            const customerNumber = document.getElementById('customer-number').value;
            
            if (!customerNumber) {
                alert('Please enter a customer number first');
                return;
            }
            
            document.getElementById('customer-number-for-assignment').value = customerNumber;
            document.getElementById('engineer-select').value = '';
            
            // Check if there's already an assigned engineer
            const record = records.find(r => r.customerNumber === customerNumber);
            if (record && record.assignedEngineer) {
                document.getElementById('engineer-select').value = record.assignedEngineer.id;
            }
            
            document.getElementById('assign-engineer-modal').style.display = 'block';
        }
        
        // Assign engineer to record
        function assignEngineer() {
            const customerNumber = document.getElementById('customer-number-for-assignment').value;
            const engineerId = document.getElementById('engineer-select').value;
            
            if (!customerNumber) {
                alert('Customer number is required');
                return;
            }
            
            if (!engineerId) {
                alert('Please select an engineer');
                return;
            }
            
            const recordIndex = records.findIndex(r => r.customerNumber === customerNumber);
            
            if (recordIndex >= 0) {
                records[recordIndex].assignedEngineer = {
                    id: engineerId,
                    name: engineers[engineerId].name
                };
                
                alert(`Engineer ${engineers[engineerId].name} assigned successfully`);
                updateAssignedEngineerDisplay(customerNumber);
                closeModal('assign-engineer-modal');
            } else {
                alert('Record not found. Please save customer information first.');
            }
        }
        
        // Update assigned engineer display
        function updateAssignedEngineerDisplay(customerNumber) {
            const displayDiv = document.getElementById('assigned-engineer-display');
            const record = records.find(r => r.customerNumber === customerNumber);
            
            if (record && record.assignedEngineer) {
                displayDiv.innerHTML = `
                    <div class="engineer-info">
                        <span>Assigned Engineer:</span>
                        <div>${record.assignedEngineer.name} (${record.assignedEngineer.id})</div>
                    </div>
                `;
            } else {
                displayDiv.innerHTML = '<p>No engineer assigned yet</p>';
            }
        }
        
        // Change password
        function changePassword() {
            const current = document.getElementById('current-password').value;
            const newPass = document.getElementById('new-password').value;
            const confirm = document.getElementById('confirm-password').value;
            
            if (current !== currentPassword) {
                alert('Current password is incorrect');
                return;
            }
            
            if (newPass !== confirm) {
                alert('New passwords do not match');
                return;
            }
            
            if (newPass.length < 5) {
                alert('Password must be at least 5 characters');
                return;
            }
            
            currentPassword = newPass;
            alert('Password changed successfully');
            closeModal('change-password-modal');
        }
        
        // Change username
        function changeUsername() {
            const current = document.getElementById('current-username').value;
            const newUser = document.getElementById('new-username').value;
            const password = document.getElementById('username-password').value;
            
            if (current !== currentUsername) {
                alert('Current username is incorrect');
                return;
            }
            
            if (password !== currentPassword) {
                alert('Password is incorrect');
                return;
            }
            
            if (newUser.length < 5) {
                alert('Username must be at least 5 characters');
                return;
            }
            
            currentUsername = newUser;
            document.getElementById('welcome-message').textContent = `Welcome, ${currentUsername}`;
            alert('Username changed successfully');
            closeModal('change-username-modal');
        }
        
        // Print record
        function printRecord() {
            const customerNumber = document.getElementById('customer-number').value;
            const record = records.find(r => r.customerNumber === customerNumber);
            
            if (!record) {
                alert('No record found for this customer number');
                return;
            }
            
            const printContent = document.getElementById('print-content');
            printContent.innerHTML = '';
            
            // Format date
            const date = new Date(record.updatedAt);
            const dateStr = `${date.getDate()}/${date.getMonth()+1}/${date.getFullYear()}`;
            
            // Engineer info
            const engineerInfo = record.assignedEngineer 
                ? `${record.assignedEngineer.name} (${record.assignedEngineer.id})` 
                : 'Not assigned';
            
            // Create print content
            const printDiv = document.createElement('div');
            printDiv.innerHTML = `
                <h3>Customer Information</h3>
                <p><strong>Customer Number:</strong> ${record.customerNumber || '-'}</p>
                <p><strong>Name:</strong> ${record.name || '-'} ${record.surname || ''}</p>
                <p><strong>Email:</strong> ${record.email || '-'}</p>
                <p><strong>Contact:</strong> ${record.contact || '-'}</p>
                <p><strong>Address:</strong> ${record.address || '-'}</p>
                <p><strong>City/Village:</strong> ${record.city || '-'}</p>
                <p><strong>State:</strong> ${record.state || '-'}</p>
                <p><strong>Pin Code:</strong> ${record.pincode || '-'}</p>
                <p><strong>Country:</strong> ${record.country || '-'}</p>
                
                <h3 style="margin-top: 20px;">Machine Information</h3>
                <p><strong>Machine Name:</strong> ${record.machineName || '-'}</p>
                <p><strong>Serial Number:</strong> ${record.serialNumber || '-'}</p>
                <p><strong>Machine Status:</strong> ${record.machineStatus ? record.machineStatus.charAt(0).toUpperCase() + record.machineStatus.slice(1).replace('-', ' ') : '-'}</p>
                <p><strong>Record Status:</strong> ${record.status ? record.status.charAt(0).toUpperCase() + record.status.slice(1).replace('-', ' ') : '-'}</p>
                <p><strong>Customer Remark:</strong> ${record.customerRemark || '-'}</p>
                <p><strong>Parts Change Remark:</strong> ${record.partsChangeRemark || '-'}</p>
                <p><strong>Assigned Engineer:</strong> ${engineerInfo}</p>
                <p><strong>Last Updated:</strong> ${dateStr}</p>
            `;
            
            printContent.appendChild(printDiv);
            
            // Trigger print
            window.print();
        }
        
        // Delete record
        function deleteRecord() {
            const customerNumber = document.getElementById('customer-number').value;
            
            if (!customerNumber) {
                alert('Please enter a customer number');
                return;
            }
            
            if (confirm('Are you sure you want to delete this record?')) {
                records = records.filter(r => r.customerNumber !== customerNumber);
                alert('Record deleted successfully');
                clearForm();
                updateSummary();
            }
        }
        
        // Clear form
        function clearForm() {
            document.getElementById('customer-number').value = '';
            document.getElementById('name').value = '';
            document.getElementById('surname').value = '';
            document.getElementById('email').value = '';
            document.getElementById('contact').value = '';
            document.getElementById('address').value = '';
            document.getElementById('city').value = '';
            document.getElementById('state').value = '';
            document.getElementById('pincode').value = '';
            document.getElementById('machine-name').value = '';
            document.getElementById('serial-number').value = '';
            document.getElementById('customer-remark').value = '';
            document.getElementById('parts-change-remark').value = '';
            document.getElementById('invoice-upload').value = '';
            document.getElementById('zip-upload').value = '';
            
            // Clear engineer display
            document.getElementById('assigned-engineer-display').innerHTML = '<p>No engineer assigned yet</p>';
        }
    </script>
</body>
</html>
