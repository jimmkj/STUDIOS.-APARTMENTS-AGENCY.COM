
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prime Rentals - House Application</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 30px;
            animation: fadeInDown 0.8s ease;
        }

        .header h1 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        .form-card {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
            animation: fadeInUp 0.8s ease;
        }

        .form-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .form-header h2 {
            font-size: 1.8rem;
            margin-bottom: 5px;
        }

        .form-header p {
            opacity: 0.9;
            font-size: 0.95rem;
        }

        .form-body {
            padding: 40px;
        }

        .section {
            margin-bottom: 35px;
            padding-bottom: 25px;
            border-bottom: 1px solid #e5e7eb;
        }

        .section:last-child {
            border-bottom: none;
            margin-bottom: 0;
        }

        .section-title {
            display: flex;
            align-items: center;
            gap: 10px;
            color: #1f2937;
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 20px;
        }

        .section-title i {
            color: #667eea;
            font-size: 1.3rem;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 20px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group.full-width {
            grid-column: 1 / -1;
        }

        label {
            display: block;
            color: #374151;
            font-weight: 500;
            margin-bottom: 8px;
            font-size: 0.9rem;
        }

        label .required {
            color: #ef4444;
        }

        input[type="text"],
        input[type="email"],
        input[type="tel"],
        input[type="number"],
        input[type="date"],
        select,
        textarea {
            width: 100%;
            padding: 12px 16px;
            border: 2px solid #e5e7eb;
            border-radius: 10px;
            font-size: 0.95rem;
            font-family: 'Inter', sans-serif;
            transition: all 0.3s ease;
            background: #f9fafb;
        }

        input:focus,
        select:focus,
        textarea:focus {
            outline: none;
            border-color: #667eea;
            background: white;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        .radio-group,
        .checkbox-group {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 8px;
        }

        .radio-item,
        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 10px 16px;
            background: #f3f4f6;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }

        .radio-item:hover,
        .checkbox-item:hover {
            background: #e5e7eb;
        }

        .radio-item input:checked + span,
        .checkbox-item input:checked + span {
            color: #667eea;
            font-weight: 600;
        }

        .radio-item:has(input:checked),
        .checkbox-item:has(input:checked) {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        .radio-item input,
        .checkbox-item input {
            width: 18px;
            height: 18px;
            accent-color: #667eea;
        }

        .info-box {
            background: linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%);
            border-left: 4px solid #3b82f6;
            padding: 16px;
            border-radius: 8px;
            margin-bottom: 20px;
            display: flex;
            align-items: flex-start;
            gap: 12px;
        }

        .info-box i {
            color: #3b82f6;
            font-size: 1.2rem;
            margin-top: 2px;
        }

        .info-box p {
            color: #1e40af;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .submit-btn {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 10px;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
        }

        .submit-btn:active {
            transform: translateY(0);
        }

        /* Payment Modal */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            backdrop-filter: blur(5px);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
            animation: fadeIn 0.3s ease;
        }

        .modal-overlay.active {
            display: flex;
        }

        .modal {
            background: white;
            border-radius: 20px;
            max-width: 600px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 25px 80px rgba(0,0,0,0.3);
            animation: slideUp 0.4s ease;
        }

        .modal-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
        }

        .modal-header .success-icon {
            width: 80px;
            height: 80px;
            background: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 15px;
            animation: scaleIn 0.5s ease 0.2s both;
        }

        .success-icon i {
            color: #10b981;
            font-size: 2.5rem;
        }

        .modal-body {
            padding: 35px;
        }

        .payment-details {
            background: #f9fafb;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
        }

        .payment-row {
            display: flex;
            justify-content: space-between;
            padding: 12px 0;
            border-bottom: 1px solid #e5e7eb;
        }

        .payment-row:last-child {
            border-bottom: none;
        }

        .payment-row.total {
            font-size: 1.2rem;
            font-weight: 700;
            color: #1f2937;
            border-top: 2px solid #667eea;
            margin-top: 10px;
            padding-top: 15px;
        }

        .agent-contact {
            background: linear-gradient(135deg, #fef3c7 0%, #fde68a 100%);
            border: 2px solid #f59e0b;
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            margin-bottom: 25px;
        }

        .agent-contact h3 {
            color: #92400e;
            margin-bottom: 10px;
            font-size: 1.1rem;
        }

        .phone-number {
            font-size: 1.8rem;
            font-weight: 700;
            color: #b45309;
            letter-spacing: 1px;
            margin: 10px 0;
        }

        .agent-contact p {
            color: #92400e;
            font-size: 0.9rem;
            margin-top: 8px;
        }

        .refund-notice {
            background: #ecfdf5;
            border: 2px solid #10b981;
            border-radius: 12px;
            padding: 20px;
            display: flex;
            align-items: flex-start;
            gap: 12px;
            margin-bottom: 25px;
        }

        .refund-notice i {
            color: #10b981;
            font-size: 1.5rem;
        }

        .refund-notice h4 {
            color: #065f46;
            margin-bottom: 5px;
        }

        .refund-notice p {
            color: #047857;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .next-steps {
            background: #eff6ff;
            border-radius: 12px;
            padding: 20px;
        }

        .next-steps h4 {
            color: #1e40af;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .next-steps ul {
            list-style: none;
            padding-left: 0;
        }

        .next-steps li {
            padding: 8px 0;
            color: #1e40af;
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 0.95rem;
        }

        .next-steps li i {
            color: #3b82f6;
        }

        .close-modal {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .close-modal:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        }

        .progress-bar {
            display: flex;
            justify-content: space-between;
            margin-bottom: 30px;
            position: relative;
        }

        .progress-bar::before {
            content: '';
            position: absolute;
            top: 15px;
            left: 0;
            right: 0;
            height: 3px;
            background: #e5e7eb;
            z-index: 0;
        }

        .progress-step {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            position: relative;
            z-index: 1;
        }

        .step-circle {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            background: #e5e7eb;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 0.85rem;
            color: #9ca3af;
            transition: all 0.3s ease;
        }

        .progress-step.active .step-circle {
            background: #667eea;
            color: white;
        }

        .progress-step.completed .step-circle {
            background: #10b981;
            color: white;
        }

        .step-label {
            font-size: 0.8rem;
            color: #6b7280;
            font-weight: 500;
        }

        .progress-step.active .step-label {
            color: #667eea;
            font-weight: 600;
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes scaleIn {
            from {
                transform: scale(0);
            }
            to {
                transform: scale(1);
            }
        }

        @media (max-width: 640px) {
            .form-row {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 1.8rem;
            }
            
            .form-body {
                padding: 25px;
            }
            
            .phone-number {
                font-size: 1.4rem;
            }
        }

        .error-message {
            color: #ef4444;
            font-size: 0.85rem;
            margin-top: 5px;
            display: none;
        }

        .form-group.error input,
        .form-group.error select,
        .form-group.error textarea {
            border-color: #ef4444;
        }

        .form-group.error .error-message {
            display: block;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="header">
            <h1><i class="fas fa-home"></i> Prime Rentals</h1>
            <p>Complete your rental application in minutes</p>
        </div>

        <div class="form-card">
            <div class="form-header">
                <h2>Rental Application Form</h2>
                <p>Please fill in all required details accurately</p>
            </div>

            <div class="form-body">
                <div class="progress-bar">
                    <div class="progress-step active" id="step1-indicator">
                        <div class="step-circle">1</div>
                        <span class="step-label">Personal Info</span>
                    </div>
                    <div class="progress-step" id="step2-indicator">
                        <div class="step-circle">2</div>
                        <span class="step-label">Rental Details</span>
                    </div>
                    <div class="progress-step" id="step3-indicator">
                        <div class="step-circle">3</div>
                        <span class="step-label">Preferences</span>
                    </div>
                    <div class="progress-step" id="step4-indicator">
                        <div class="step-circle">4</div>
                        <span class="step-label">Review</span>
                    </div>
                </div>

                <form id="rentalForm">
                    <!-- Section 1: Personal Information -->
                    <div class="section" id="section1">
                        <div class="section-title">
                            <i class="fas fa-user"></i>
                            Personal Information
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label>First Name <span class="required">*</span></label>
                                <input type="text" name="firstName" placeholder="John" required>
                                <span class="error-message">Please enter your first name</span>
                            </div>
                            <div class="form-group">
                                <label>Last Name <span class="required">*</span></label>
                                <input type="text" name="lastName" placeholder="Doe" required>
                                <span class="error-message">Please enter your last name</span>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Email Address <span class="required">*</span></label>
                                <input type="email" name="email" placeholder="john.doe@email.com" required>
                                <span class="error-message">Please enter a valid email</span>
                            </div>
                            <div class="form-group">
                                <label>Phone Number <span class="required">*</span></label>
                                <input type="tel" name="phone" placeholder="+44 7700 900000" required>
                                <span class="error-message">Please enter your phone number</span>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Date of Birth <span class="required">*</span></label>
                                <input type="date" name="dob" required>
                                <span class="error-message">Please enter your date of birth</span>
                            </div>
                            <div class="form-group">
                                <label>National Insurance Number</label>
                                <input type="text" name="nin" placeholder="AB123456C">
                            </div>
                        </div>

                        <div class="form-group full-width">
                            <label>Current Address <span class="required">*</span></label>
                            <textarea name="currentAddress" placeholder="Enter your full current address including postcode" required></textarea>
                            <span class="error-message">Please enter your current address</span>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Current Employment Status <span class="required">*</span></label>
                                <select name="employment" required>
                                    <option value="">Select status</option>
                                    <option value="full-time">Full-time Employed</option>
                                    <option value="part-time">Part-time Employed</option>
                                    <option value="self-employed">Self-employed</option>
                                    <option value="student">Student</option>
                                    <option value="unemployed">Unemployed</option>
                                    <option value="retired">Retired</option>
                                </select>
                                <span class="error-message">Please select employment status</span>
                            </div>
                            <div class="form-group">
                                <label>Monthly Income (£) <span class="required">*</span></label>
                                <input type="number" name="income" placeholder="2500" min="0" required>
                                <span class="error-message">Please enter your monthly income</span>
                            </div>
                        </div>
                    </div>

                    <!-- Section 2: Rental Details -->
                    <div class="section" id="section2">
                        <div class="section-title">
                            <i class="fas fa-file-contract"></i>
                            Rental Details
                        </div>

                        <div class="info-box">
                            <i class="fas fa-info-circle"></i>
                            <p>Please provide accurate rental information. The monthly rent amount will determine your required deposit (typically 4-6 weeks rent).</p>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Monthly Rent Amount (£) <span class="required">*</span></label>
                                <input type="number" name="rentAmount" placeholder="1200" min="0" required>
                                <span class="error-message">Please enter the monthly rent</span>
                            </div>
                            <div class="form-group">
                                <label>Property Type <span class="required">*</span></label>
                                <select name="propertyType" required>
                                    <option value="">Select type</option>
                                    <option value="studio">Studio Apartment</option>
                                    <option value="1bed">1 Bedroom</option>
                                    <option value="2bed">2 Bedroom</option>
                                    <option value="3bed">3 Bedroom</option>
                                    <option value="4bed">4+ Bedroom</option>
                                    <option value="house">Full House</option>
                                    <option value="flat">Flat/Apartment</option>
                                </select>
                                <span class="error-message">Please select property type</span>
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label>Preferred Move-in Date <span class="required">*</span></label>
                                <input type="date" name="moveInDate" required>
                                <span class="error-message">Please select a move-in date</span>
                            </div>
                            <div class="form-group">
                                <label>Duration of Stay <span class="required">*</span></label>
                                <select name="duration" required>
                                    <option value="">Select duration</option>
                                    <option value="6months">6 Months</option>
                                    <option value="12months">12 Months</option>
                                    <option value="18months">18 Months</option>
                                    <option value="24months">24 Months</option>
                                    <option value="36months">36+ Months</option>
                                </select>
                                <span class="error-message">Please select duration of stay</span>
                            </div>
                        </div>

                        <div class="form-group full-width">
                            <label>Preferred Location/Area <span class="required">*</span></label>
                            <input type="text" name="location" placeholder="e.g., Manchester City Centre, Didsbury, etc." required>
                            <span class="error-message">Please enter preferred location</span>
                        </div>

                        <div class="form-group full-width">
                            <label>Reason for Moving <span class="required">*</span></label>
                            <textarea name="reason" placeholder="Briefly explain why you are looking for a new rental property" required></textarea>
                            <span class="error-message">Please provide a reason for moving</span>
                        </div>
                    </div>

                    <!-- Section 3: Preferences & Additional Info -->
                    <div class="section" id="section3">
                        <div class="section-title">
                            <i class="fas fa-sliders-h"></i>
                            Preferences & Additional Information
                        </div>

                        <div class="form-group full-width">
                            <label>Do you have any pets? <span class="required">*</span></label>
                            <div class="radio-group">
                                <label class="radio-item">
                                    <input type="radio" name="pets" value="none" checked>
                                    <span>No Pets</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="pets" value="dog">
                                    <span><i class="fas fa-dog"></i> Dog(s)</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="pets" value="cat">
                                    <span><i class="fas fa-cat"></i> Cat(s)</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="pets" value="other">
                                    <span>Other</span>
                                </label>
                            </div>
                        </div>

                        <div class="form-group full-width" id="petDetails" style="display: none;">
                            <label>Pet Details</label>
                            <textarea name="petDetails" placeholder="Please describe your pet(s) - breed, age, size, etc."></textarea>
                        </div>

                        <div class="form-group full-width">
                            <label>Number of Occupants <span class="required">*</span></label>
                            <div class="radio-group">
                                <label class="radio-item">
                                    <input type="radio" name="occupants" value="1" checked>
                                    <span>Just Me</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="occupants" value="2">
                                    <span>2 People</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="occupants" value="3">
                                    <span>3 People</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="occupants" value="4plus">
                                    <span>4+ People</span>
                                </label>
                            </div>
                        </div>

                        <div class="form-group full-width">
                            <label>Smoking Preference <span class="required">*</span></label>
                            <div class="radio-group">
                                <label class="radio-item">
                                    <input type="radio" name="smoking" value="non-smoker" checked>
                                    <span>Non-Smoker</span>
                                </label>
                                <label class="radio-item">
                                    <input type="radio" name="smoking" value="smoker">
                                    <span>Smoker</span>
                                </label>
                            </div>
                        </div>

                        <div class="form-group full-width">
                            <label>Parking Requirements</label>
                            <div class="checkbox-group">
                                <label class="checkbox-item">
                                    <input type="checkbox" name="parking" value="none">
                                    <span>No Parking Needed</span>
                                </label>
                                <label class="checkbox-item">
                                    <input type="checkbox" name="parking" value="street">
                                    <span>Street Parking</span>
                                </label>
                                <label class="checkbox-item">
                                    <input type="checkbox" name="parking" value="garage">
                                    <span>Garage</span>
                                </label>
                                <label class="checkbox-item">
                                    <input type="checkbox" name="parking" value="driveway">
                                    <span>Driveway</span>
                                </label>
                            </div>
                        </div>

                        <div class="form-group full-width">
                            <label>Additional Requirements or Comments</label>
                            <textarea name="additional" placeholder="Any specific requirements, accessibility needs, or other information you'd like us to know..."></textarea>
                        </div>

                        <div class="form-group full-width">
                            <label class="checkbox-item" style="width: 100%; justify-content: flex-start;">
                                <input type="checkbox" name="terms" required>
                                <span>I confirm that all information provided is accurate and I agree to the terms and conditions <span class="required">*</span></span>
                            </label>
                            <span class="error-message">You must agree to the terms</span>
                        </div>
                    </div>

                    <button type="submit" class="submit-btn">
                        <i class="fas fa-paper-plane"></i> Submit Application
                    </button>
                </form>
            </div>
        </div>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="paymentModal">
        <div class="modal">
            <div class="modal-header">
                <div class="success-icon">
                    <i class="fas fa-check"></i>
                </div>
                <h2>Application Submitted Successfully!</h2>
                <p>Your rental application has been received</p>
            </div>
            
            <div class="modal-body">
                <div class="payment-details">
                    <div class="payment-row">
                        <span>Application Reference</span>
                        <strong id="refNumber">APP-2024-78432</strong>
                    </div>
                    <div class="payment-row">
                        <span>Property Type</span>
                        <strong id="modalPropertyType">-</strong>
                    </div>
                    <div class="payment-row">
                        <span>Monthly Rent</span>
                        <strong id="modalRent">-</strong>
                    </div>
                    <div class="payment-row">
                        <span>Duration</span>
                        <strong id="modalDuration">-</strong>
                    </div>
                    <div class="payment-row total">
                        <span>Required Deposit</span>
                        <strong id="modalDeposit">-</strong>
                    </div>
                </div>

                <div class="agent-contact">
                    <h3><i class="fas fa-phone-alt"></i> Contact Agent to Complete Payment</h3>
                    <div class="phone-number">
                        <i class="fab fa-whatsapp"></i> +44 7853 147161
                    </div>
                    <p>Please contact the agent via WhatsApp or call to complete your deposit payment and finalize your application bid.</p>
                </div>

                <div class="refund-notice">
                    <i class="fas fa-shield-alt"></i>
                    <div>
                        <h4>Fully Refundable Deposit</h4>
                        <p>Your deposit is 100% refundable if your application is unsuccessful or if you decide not to proceed. The deposit will be returned to you within 5-7 working days.</p>
                    </div>
                </div>

                <div class="next-steps">
                    <h4><i class="fas fa-list-check"></i> Next Steps</h4>
                    <ul>
                        <li><i class="fas fa-check-circle"></i> Contact agent at +44 7853 147161 to pay deposit</li>
                        <li><i class="fas fa-check-circle"></i> Receive payment confirmation via email</li>
                        <li><i class="fas fa-check-circle"></i> Application review completed within 24-48 hours</li>
                        <li><i class="fas fa-check-circle"></i> Move in at any moment once approved!</li>
                    </ul>
                </div>

                <button class="close-modal" onclick="closeModal()">
                    <i class="fas fa-times"></i> Close
                </button>
            </div>
        </div>
    </div>

    <script>
        // Form validation and submission
        const form = document.getElementById('rentalForm');
        const modal = document.getElementById('paymentModal');
        
        // Pet details toggle
        document.querySelectorAll('input[name="pets"]').forEach(radio => {
            radio.addEventListener('change', function() {
                const petDetails = document.getElementById('petDetails');
                if (this.value !== 'none') {
                    petDetails.style.display = 'block';
                } else {
                    petDetails.style.display = 'none';
                }
            });
        });

        // Progress indicator update on scroll
        const sections = document.querySelectorAll('.section');
        const progressSteps = document.querySelectorAll('.progress-step');

        window.addEventListener('scroll', () => {
            let current = '';
            sections.forEach((section, index) => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (window.scrollY >= (sectionTop - 200)) {
                    current = index;
                }
            });

            progressSteps.forEach((step, index) => {
                step.classList.remove('active', 'completed');
                if (index < current) {
                    step.classList.add('completed');
                    step.querySelector('.step-circle').innerHTML = '<i class="fas fa-check"></i>';
                } else if (index === current) {
                    step.classList.add('active');
                    step.querySelector('.step-circle').textContent = index + 1;
                } else {
                    step.querySelector('.step-circle').textContent = index + 1;
                }
            });
        });

        // Form submission
        form.addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Validate all required fields
            let isValid = true;
            const requiredFields = form.querySelectorAll('[required]');
            
            requiredFields.forEach(field => {
                const formGroup = field.closest('.form-group');
                if (!field.value || (field.type === 'checkbox' && !field.checked)) {
                    formGroup.classList.add('error');
                    isValid = false;
                } else {
                    formGroup.classList.remove('error');
                }
            });

            if (!isValid) {
                // Scroll to first error
                const firstError = document.querySelector('.form-group.error');
                if (firstError) {
                    firstError.scrollIntoView({ behavior: 'smooth', block: 'center' });
                }
                return;
            }

            // Generate reference number
            const refNum = 'APP-' + new Date().getFullYear() + '-' + Math.floor(10000 + Math.random() * 90000);
            document.getElementById('refNumber').textContent = refNum;

            // Get form values
            const formData = new FormData(form);
            const rentAmount = parseFloat(formData.get('rentAmount')) || 0;
            const propertyType = formData.get('propertyType');
            const duration = formData.get('duration');

            // Calculate deposit (5 weeks rent)
            const deposit = Math.round((rentAmount * 12 / 52) * 5);

            // Update modal content
            const propertyTypeMap = {
                'studio': 'Studio Apartment',
                '1bed': '1 Bedroom',
                '2bed': '2 Bedroom',
                '3bed': '3 Bedroom',
                '4bed': '4+ Bedroom',
                'house': 'Full House',
                'flat': 'Flat/Apartment'
            };

            const durationMap = {
                '6months': '6 Months',
                '12months': '12 Months',
                '18months': '18 Months',
                '24months': '24 Months',
                '36months': '36+ Months'
            };

            document.getElementById('modalPropertyType').textContent = propertyTypeMap[propertyType] || propertyType;
            document.getElementById('modalRent').textContent = '£' + rentAmount.toLocaleString();
            document.getElementById('modalDuration').textContent = durationMap[duration] || duration;
            document.getElementById('modalDeposit').textContent = '£' + deposit.toLocaleString();

            // Show modal
            modal.classList.add('active');
            document.body.style.overflow = 'hidden';
        });

        function closeModal() {
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
            form.reset();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Close modal on overlay click
        modal.addEventListener('click', function(e) {
            if (e.target === modal) {
                closeModal();
            }
        });

        // Real-time validation removal
        document.querySelectorAll('input, select, textarea').forEach(field => {
            field.addEventListener('input', function() {
                const formGroup = this.closest('.form-group');
                if (formGroup && this.value) {
                    formGroup.classList.remove('error');
                }
            });
        });
    </script>
</body>
</html>
