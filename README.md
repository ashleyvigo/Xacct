<!DOCTYPE html>
<html>
<head>
    <title>Pursuit Social User Directory 2025</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 20px;
            background-color: #f0f8ff;
            color: #333;
        }

        h1 {
            text-align: center;
            color: #2c3e50;
            margin-bottom: 20px;
            animation: dynamicTitle 5s infinite alternate; /* Dynamic title animation */
            font-size: 2.5em; /* Larger title */
            font-weight: 700; /* Bold title */
        }

        @keyframes dynamicTitle {
            0% { color: #2c3e50; transform: scale(1); }
            25% { color: #3498db; transform: scale(1.05); }
            50% { color: #27ae60; transform: scale(1.1); }
            75% { color: #e74c3c; transform: scale(1.05); }
            100% { color: #2c3e50; transform: scale(1); }
        }

        form {
            background-color: #fff;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin-bottom: 25px;
            border: 1px solid #e0e0e0;
            transition: transform 0.3s ease;
        }

        form:hover {
            transform: translateY(-5px);
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }

        input[type="text"] {
            width: calc(100% - 22px);
            padding: 12px;
            margin-bottom: 20px;
            border: 1px solid #d1d1d1;
            border-radius: 6px;
            box-sizing: border-box;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }

        input[type="text"]:focus {
            border-color: #3498db;
        }

        button {
            background-color: #3498db;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            font-weight: 600;
            transition: background-color 0.3s ease, transform 0.2s ease;
        }

        button:hover {
            background-color: #2980b9;
            transform: scale(1.05);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border: 1px solid #e0e0e0;
            animation: slideIn 1s ease-out;
        }

        @keyframes slideIn {
            from { transform: translateX(-50px); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        th, td {
            border: 1px solid #e0e0e0;
            padding: 15px;
            text-align: left;
            font-size: 16px;
        }

        th {
            background-color: #ecf0f1;
            font-weight: 600;
            color: #333;
        }

        a {
            color: #3498db;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        a:hover {
            text-decoration: underline;
            color: #2980b9;
        }

    </style>
</head>
<body>
    <h1>Pursuit Social User Directory 2025</h1>

    <form id="userForm">
        <label for="name">Name:</label><br>
        <input type="text" id="name" name="name"><br><br>

        <label for="xProfileLink">X Profile Link:</label><br>
        <input type="text" id="xProfileLink" name="xProfileLink"><br><br>

        <label for="instagramProfile">Instagram Profile Link:</label><br>
        <input type="text" id="instagramProfile" name="instagramProfile"><br><br>

        <label for="linkedinProfile">LinkedIn Profile Link:</label><br>
        <input type="text" id="linkedinProfile" name="linkedinProfile"><br><br>

        <button type="button" onclick="addUser()">Add User</button>
    </form>

    <br>

    <table id="userTable">
        <thead>
            <tr>
                <th>Name</th>
                <th>X Profile Link</th>
                <th>Instagram</th>
                <th>LinkedIn</th>
            </tr>
        </thead>
        <tbody>
        </tbody>
    </table>

    <script>
        function addUser() {
            const name = document.getElementById("name").value;
            const xProfileLink = document.getElementById("xProfileLink").value;
            const instagramProfile = document.getElementById("instagramProfile").value;
            const linkedinProfile = document.getElementById("linkedinProfile").value;

            if (name && xProfileLink && instagramProfile && linkedinProfile) {
                const user = { name, xProfileLink, instagramProfile, linkedinProfile };
                let users = JSON.parse(localStorage.getItem("xUsers")) || [];
                users.push(user);
                localStorage.setItem("xUsers", JSON.stringify(users));
                displayUsers();
                document.getElementById("userForm").reset();
            } else {
                alert("Please fill in all fields.");
            }
        }

        function displayUsers() {
            const users = JSON.parse(localStorage.getItem("xUsers")) || [];
            const tableBody = document.getElementById("userTable").getElementsByTagName("tbody")[0];
            tableBody.innerHTML = "";

            users.forEach(user => {
                const row = tableBody.insertRow();
                const nameCell = row.insertCell(0);
                const xProfileLinkCell = row.insertCell(1);
                const instagramCell = row.insertCell(2);
                const linkedinCell = row.insertCell(3);

                nameCell.textContent = user.name;
                xProfileLinkCell.innerHTML = `<a href="${user.xProfileLink}" target="_blank">${user.xProfileLink}</a>`;
                instagramCell.innerHTML = `<a href="${user.instagramProfile}" target="_blank">${user.instagramProfile}</a>`;
                linkedinCell.innerHTML = `<a href="${user.linkedinProfile}" target="_blank">${user.linkedinProfile}</a>`;
            });
        }

        displayUsers();
    </script>
</body>
</html>
