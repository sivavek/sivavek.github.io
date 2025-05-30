---
layout: default
---

# Welcome

Hi, I’m building a clean portfolio using the Architect theme on GitHub Pages!


<h2>My Projects</h2>
<div id="repo-list">Loading repositories...</div>

<script>
  const username = "sivavek";
  fetch(`https://api.github.com/users/${username}/repos?sort=updated`)
    .then(response => response.json())
    .then(repos => {
      const container = document.getElementById("repo-list");
      container.innerHTML = "";
      repos.forEach(repo => {
        const project = document.createElement("div");
        project.style = "margin-bottom: 1em; padding: 1em; border: 1px solid #ddd; border-radius: 5px;";
        project.innerHTML = `
          <h3><a href="${repo.html_url}" target="_blank">${repo.name}</a></h3>
          <p>${repo.description || "No description provided."}</p>
          <p><strong>Language:</strong> ${repo.language || "N/A"} | ⭐ ${repo.stargazers_count}</p>
        `;
        container.appendChild(project);
      });
    })
    .catch(error => {
      document.getElementById("repo-list").innerText = "Failed to load repositories.";
      console.error(error);
    });
</script>

