<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Signup & Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f3f3f3;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            width: 300px;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .form-box {
            text-align: center;
        }
        input {
            width: 90%;
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 95%;
            padding: 10px;
            background: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background: #0056b3;
        }
        p {
            font-size: 14px;
        }
        a {
            color: #007bff;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        #signup-message, #login-message {
            color: red;
            font-size: 12px;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <div class="container">

        <!-- Signup Form -->
        <div class="form-box" id="signup-box">
            <h2>Signup</h2>
            <input type="text" id="signup-username" placeholder="Username">
            <input type="password" id="signup-password" placeholder="Password">
            <button onclick="signup()">Signup</button>
            <p>Already have an account? <a href="#" onclick="showLogin()">Login</a></p>
            <p id="signup-message"></p>
        </div>

        <!-- Login Form -->
        <div class="form-box" id="login-box" style="display:none;">
            <h2>Login</h2>
            <input type="text" id="login-username" placeholder="Username">
            <input type="password" id="login-password" placeholder="Password">
            <button onclick="login()">Login</button>
            <p>Don't have an account? <a href="#" onclick="showSignup()">Signup</a></p>
            <p id="login-message"></p>
        </div>

    </div>

    <script>
        function showSignup() {
            document.getElementById("signup-box").style.display = "block";
            document.getElementById("login-box").style.display = "none";
        }

        function showLogin() {
            document.getElementById("signup-box").style.display = "none";
            document.getElementById("login-box").style.display = "block";
        }

        function signup() {
            let username = document.getElementById("signup-username").value;
            let password = document.getElementById("signup-password").value;
            let message = document.getElementById("signup-message");

            if (username === "" || password === "") {
                message.style.color = "red";
                message.innerText = "Please fill all fields.";
                return;
            }

            localStorage.setItem(username, password);
            message.style.color = "green";
            message.innerText = "Signup successful!";
        }

        function login() {
            let username = document.getElementById("login-username").value;
            let password = document.getElementById("login-password").value;
            let message = document.getElementById("login-message");

            let storedPassword = localStorage.getItem(username);

            if (storedPassword === null) {
                message.style.color = "red";
                message.innerText = "User not found!";
            } else if (storedPassword !== password) {
                message.style.color = "red";
                message.innerText = "Incorrect password!";
            } else {
                message.style.color = "green";
                message.innerText = "Login successful!";
            }
        }
    </script>
</body>
</html>
