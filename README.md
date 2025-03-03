# Form-Validation
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SignIn & SignUp Form Validation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .container {
            width: 350px;
            background: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0px 0px 10px gray;
        }
        input, select {
            width: 100%;
            padding: 8px;
            margin: 5px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .error {
            color: red;
            font-size: 12px;
        }
        button {
            width: 100%;
            padding: 10px;
            background: blue;
            color: white;
            border: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Sign In</h2>
        <form id="signInForm" onsubmit="return validateSignIn()">
            <input type="text" id="signinUsername" placeholder="Username">
            <span class="error" id="signinUserError"></span>
            <input type="password" id="signinPassword" placeholder="Password">
            <span class="error" id="signinPassError"></span>
            <button type="submit">Login</button>
        </form>
    </div>

    <div class="container" style="margin-left: 20px;">
        <h2>Sign Up</h2>
        <form id="signUpForm" onsubmit="return validateSignUp()">
            <input type="text" id="fullname" placeholder="Full Name">
            <span class="error" id="nameError"></span>
            
            <input type="email" id="email" placeholder="Email">
            <span class="error" id="emailError"></span>
            
            <input type="password" id="password" placeholder="Password">
            <span class="error" id="passError"></span>
            
            <input type="password" id="confirmPassword" placeholder="Confirm Password">
            <span class="error" id="confirmPassError"></span>
            
            <input type="number" id="age" placeholder="Age">
            <span class="error" id="ageError"></span>
            
            <input type="text" id="phone" placeholder="Phone Number (10 digits)">
            <span class="error" id="phoneError"></span>
            
            <select id="gender">
                <option value="">Select Gender</option>
                <option value="male">Male</option>
                <option value="female">Female</option>
            </select>
            <span class="error" id="genderError"></span>
            
            <input type="checkbox" id="terms"> I agree to terms and conditions
            <span class="error" id="termsError"></span>
            
            <button type="submit">Register</button>
        </form>
    </div>

    <script>
        function validateSignIn() {
            let username = document.getElementById('signinUsername').value;
            let password = document.getElementById('signinPassword').value;
            let isValid = true;
            
            document.getElementById('signinUserError').innerText = username ? '' : 'Username is required';
            document.getElementById('signinPassError').innerText = password ? '' : 'Password is required';
            
            if (!username || !password) isValid = false;
            return isValid;
        }
        
        function validateSignUp() {
            let name = document.getElementById('fullname').value;
            let email = document.getElementById('email').value;
            let password = document.getElementById('password').value;
            let confirmPassword = document.getElementById('confirmPassword').value;
            let age = document.getElementById('age').value;
            let phone = document.getElementById('phone').value;
            let gender = document.getElementById('gender').value;
            let terms = document.getElementById('terms').checked;
            let isValid = true;

            document.getElementById('nameError').innerText = name ? '' : 'Name is required';
            document.getElementById('emailError').innerText = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email) ? '' : 'Invalid email';
            document.getElementById('passError').innerText = /^(?=.*[0-9])(?=.*[!@#$%^&*])/.test(password) ? '' : 'Password must contain a special character and number';
            document.getElementById('confirmPassError').innerText = (password === confirmPassword) ? '' : 'Passwords do not match';
            document.getElementById('ageError').innerText = (age >= 18 && age <= 60) ? '' : 'Age must be between 18 and 60';
            document.getElementById('phoneError').innerText = /^[0-9]{10}$/.test(phone) ? '' : 'Phone must be 10 digits';
            document.getElementById('genderError').innerText = gender ? '' : 'Please select a gender';
            document.getElementById('termsError').innerText = terms ? '' : 'You must accept the terms';
            
            if (!name || !email || !password || password !== confirmPassword || age < 18 || age > 60 || !/^[0-9]{10}$/.test(phone) || !gender || !terms) isValid = false;
            return isValid;
        }
    </script>
</body>
</html>
