<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Customize Your Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }
        h1 {
            color: #333;
        }
        .repository {
            margin-bottom: 10px;
        }
        .repository a {
            display: inline-block;
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            text-decoration: none;
            border-radius: 5px;
        }
        .repository a:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Daniel Grimut</h1>
        <p>Hello there! I am a soon-to-be graduate (Dec 2024) Software Developer based in Montreal. I am very passionate about AI and I am proficient in Java, JavaScript, C++, Python, and SQL, as well as possess field experience with React, NodeJS, and Maven. Feel free to check out some of my favorite projects below!</p>
        <h2>Projects 🛠️</h2>
        <div id="repositories"></div>
    </div>

    <script>
        // Fetch your pinned repositories from GitHub API
        fetch('https://api.github.com/users/<your-username>/repos?type=owner&sort=updated&direction=desc')
            .then(response => response.json())
            .then(repos => {
                const repositoriesContainer = document.getElementById('repositories');
                repos.slice(0, 6).forEach(repo => {
                    const repoLink = document.createElement('a');
                    repoLink.href = repo.html_url;
                    repoLink.textContent = repo.name;
                    repoLink.className = 'repository';
                    repositoriesContainer.appendChild(repoLink);
                    repositoriesContainer.appendChild(document.createElement('br'));
                });
            });
    </script>
</body>
</html>
