<!DOCTYPE html>
<html>
<head>
    <title>Pursuit Social User Directory 2025</title>
    <style>
        /* ... (CSS styles remain the same) ... */
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
            animation: dynamicTitle 5s infinite alternate;
            font-size: 2.5em;
            font-weight: 700;
        }

        @keyframes dynamicTitle {
            0% { color: #2c3e50; transform: scale(1); }
            25% { color: #3498db; transform: scale(1.05); }
            50% { color: #27ae60; transform: scale(1.1); }
            75% { color: #e74c3c; transform: scale(1.05); }
            100% { color: #2c3e50; transform: scale(1); }
        }

        /* ... (Other CSS styles remain the same) ... */
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

        <button type="button" onclick="addUser()">Add User</button><br><br>
        <button type="button" onclick="deleteUser()">Delete My Info</button>
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
            // ... (addUser function remains the same) ...
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
            // ... (displayUsers function remains the same) ...
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

        function deleteUser() {
            const nameToDelete = prompt("Enter your name to delete your information:");

            if (nameToDelete) {
                let users = JSON.parse(localStorage.getItem("xUsers")) || [];
                users = users.filter(user => user.name !== nameToDelete);
                localStorage.setItem("xUsers", JSON.stringify(users));
                displayUsers();
            }
        }

        displayUsers();
    </script>
</body>
</html>
