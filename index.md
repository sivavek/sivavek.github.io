---
layout: default
---

# Welcome

Hi, I’m building a clean portfolio using the Architect theme on GitHub Pages!


<h2>Featured Projects</h2>
<div id="repo-list">Loading portfolio projects...</div>

<script>
  fetch('repos.json')
    .then(response => response.json())
    .then(repos => {
      const container = document.getElementById("repo-list");
      container.innerHTML = "";
      repos.forEach(repo => {
        const project = document.createElement("div");
        project.style = "margin-bottom: 1em; padding: 1em; border: 1px solid #ddd; border-radius: 5px;";
        project.innerHTML = `
          <h3><a href="${repo.url}" target="_blank">${repo.name}</a></h3>
          <p>${repo.description}</p>
          <p><strong>Language:</strong> ${repo.language} | ⭐ ${repo.stars}</p>
        `;
        container.appendChild(project);
      });
    })
    .catch(error => {
      document.getElementById("repo-list").innerText = "Failed to load projects.";
      console.error(error);
    });
</script>
