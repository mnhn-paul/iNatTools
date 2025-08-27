---
layout: default
title: iNaturalist Tool Library
---

<div id="tool-container"></div>

<script>
  const tools = [
    {
      name: "New Taxa Tool",
      file: "Tools/new-taxa-user.html",
      category: "Users specific tool",
      description: "A tool that helps a user to quickly identify if they observed species for the first time within a given time period."
    },
    {
      name: "ZPIN Tool",
      file: "Tools/ZPIN-user.html",
      category: "Users specific tool",
      description: "Tool that helps a user identify how many observations they have already contributed from ZPIN protected area in Luxembourg and which ones were not yet visited."
    },
    {
      name: "User TOD slider",
      file: "Tools/daily-user-map-timeline.html",
      category: "Users specific tool",
      description: "Check for issues in location via time."
    },
    {
      name: "Top users in Luxembourg",
      file: "Tools/top-users-lux.html",
      category: "Users specific tool",
      description: "Gives a simple list of the top users in Luxembourg."
    },
    {
      name: "Compare users species lists",
      file: "Tools/compare_species_user.html",
      category: "Users specific tool",
      description: "Tool to quickly compare the species lists of two users."
    },
    {
      name: "Yearly species observation histogram",
      file: "Tools/species-yearly-histogram.html",
      category: "Luxembourg specific tool",
      description: "Lookup a species name to generate yearly histograms of number of observations."
    },
    {
      name: "Yearly observation histogram Luxembourg",
      file: "Tools/inat-Lux-yearly-evolution.html",
      category: "Luxembourg specific tool",
      description: "Check the currently yearly evolution of observations share from Luxembourg on iNaturalist."
    },
    {
      name: "CNC 2025 user overview",
      file: "Tools/CNC2025-users.html",
      category: "CNC specific tool",
      description: "Get an overview of the CNC 2025 user activity."
    },
    {
      name: "CNC quick data overview",
      file: "Tools/CNC-data-overview.html",
      category: "CNC specific tool",
      description: "Get a quick overview of the CNC data."
    },
    {
      name: "Places",
      file: "Tools/places.html",
      category: "Other",
      description: "Testing tool."
    }
  ];

  const specialLinks = [
    {
      name: "Useful links",
      file: "pages/links.html",
      description: "Collection of useful links."
    }
  ];

  // Group tools by category
  const grouped = tools.reduce((acc, tool) => {
    if (!acc[tool.category]) acc[tool.category] = [];
    acc[tool.category].push(tool);
    return acc;
  }, {});

  const container = document.getElementById("tool-container");
  for (const category in grouped) {
    const section = document.createElement("div");
    section.className = "tool-category";
    const heading = document.createElement("h2");
    heading.textContent = category;
    section.appendChild(heading);
    grouped[category].forEach(tool => {
      const toolDiv = document.createElement("div");
      toolDiv.className = "tool";
      const link = document.createElement("a");
      link.href = tool.file;
      link.textContent = tool.name;
      const desc = document.createElement("div");
      desc.className = "description";
      desc.textContent = tool.description;
      toolDiv.appendChild(link);
      toolDiv.appendChild(desc);
      section.appendChild(toolDiv);
    });
    container.appendChild(section);
  }

  // Add separate section for useful links
  const linksSection = document.createElement("div");
  linksSection.className = "tool-category special-links";
  const linksHeading = document.createElement("h2");
  linksHeading.textContent = "Useful Resources";
  linksSection.appendChild(linksHeading);
  specialLinks.forEach(linkObj => {
    const linkDiv = document.createElement("div");
    linkDiv.className = "tool special";
    const link = document.createElement("a");
    link.href = linkObj.file;
    link.textContent = linkObj.name;
    const desc = document.createElement("div");
    desc.className = "description";
    desc.textContent = linkObj.description;
    linkDiv.appendChild(link);
    linkDiv.appendChild(desc);
    linksSection.appendChild(linkDiv);
  });
  container.appendChild(linksSection);
</script>

<style>
  .special-links {
    background-color: #f5f5e5;
    border-left: 5px solid #d4af37;
    padding: 1em;
    margin-top: 2em;
  }
  .tool.special a {
    color: #8a4b08;
    font-weight: bold;
  }
  .tool-category {
    margin-bottom: 2em;
  }
  .tool {
    margin-bottom: 1em;
  }
  .tool a {
    display: block;
    font-size: 1.2em;
    color: #0066cc;
    text-decoration: none;
  }
  .description {
    font-size: 0.9em;
    color: #333;
  }
</style>
