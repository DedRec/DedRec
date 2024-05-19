<h1>Hi there 👋, I'm Seif</h1>

<details>
  <summary>Click to see my GitHub stats and more!</summary>

  ![DedRec's GitHub stats](https://github-readme-stats.vercel.app/api?username=DedRec&show_icons=true&theme=radical)

  [![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=DedRec&layout=compact&theme=radical)](https://github.com/anuraghazra/github-readme-stats)

</details>

<!--
**DedRec/DedRec** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

 [![trophy](https://github-profile-trophy.vercel.app/?username=DedRec&theme=radical)](https://github.com/ryo-ma/github-profile-trophy)
-->

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My GitHub HTML Repositories</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .repo {
            border: 1px solid #ccc;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
        }
        .repo a {
            font-size: 1.2em;
            color: #0366d6;
            text-decoration: none;
        }
    </style>
</head>
<body>
    <h1>My GitHub HTML Repositories</h1>
    <div id="repos"></div>

    <script>
        const username = 'DedRec'; // Replace with your GitHub username
        const url = `https://api.github.com/users/${username}/repos`;

        fetch(url)
            .then(response => response.json())
            .then(repos => {
                const repoContainer = document.getElementById('repos');
                repos.forEach(repo => {
                    fetch(repo.languages_url)
                        .then(response => response.json())
                        .then(languages => {
                            if (languages.HTML) {
                                const repoDiv = document.createElement('div');
                                repoDiv.className = 'repo';
                                repoDiv.innerHTML = `
                                    <a href="${repo.html_url}" target="_blank">${repo.name}</a>
                                    <p>${repo.description || 'No description available'}</p>
                                    <p><strong>Languages:</strong> ${Object.keys(languages).join(', ')}</p>
                                `;
                                repoContainer.appendChild(repoDiv);
                            }
                        })
                        .catch(error => console.error('Error fetching languages:', error));
                });
            })
            .catch(error => console.error('Error fetching repositories:', error));
    </script>
</body>
</html>

