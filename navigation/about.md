---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Here are some places I have lived in/visited.

<comment>
Flags sourced from Wikipedia images
</comment>

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Born in California", "description": "California"},
        {"flag": "0/09/Flag_of_South_Korea.svg", "greeting": "Korean", "description": "South Korea"}
    ];
    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>

<h2>Favorite Games</h2>
<div class="grid-container" id="grid_container2">
    <!-- second grid content will be added here by JavaScript -->
</div>

<script>
    // safe connection for second grid
    let container2 = document.getElementById("grid_container2");
    const http_source2 = "https://upload.wikimedia.org/wikipedia/commons/";
    const visited_places = [
        {"flag": "f/fc/Valorant_logo_-_pink_color_version.svg", "description": "Valorant","description": "My Favorite Game"},
        {"flag": "8/8d/Subnautica_logo.png","description": "Subnautica","description": "Fun, but time-consuming"},
        {"flag": "f/fd/Geometry_Dash.svg","description": "Geometry Dash","description": "Better if you have the paid version"},
        {"flag": "6/6a/Minecraft_Trails_and_Tales_Art.png","description": "Minecraft","description": "Fun with friends, and solo"}
    ];

    if (container2) {
        for (const place of visited_places) {
            const gridItem = document.createElement("div");
            gridItem.className = "grid-item";
            const img = document.createElement("img");
            img.src = http_source2 + place.flag;
            img.alt = place.description + " Flag";
            const description = document.createElement("p");
            description.textContent = place.description;
            const greeting = document.createElement("p");
            greeting.textContent = place.greeting;
            gridItem.appendChild(img);
            gridItem.appendChild(description);
            container2.appendChild(gridItem);
        }
    }
</script>

### Journey through Life

My life thus far:

- 🏫 Attended Turtleback Elementary School
- 🏫 Attended Oak Valley Middle School '22-'25
- 🎓 Currently attending Del Norte High School, class of 2029
- Robotics for 4+ years, Made it to FLL State Championships
- Sports include: Swimming, Cross-country, Taekwondo, and Soccer

### Culture, Family, and Fun

Everything for me, as for many others, revolves around family.

- I am Korean
- I have 2 pets, one dog and one cat.
- Below are some pictures:

<comment>
Gallery of Pictures( Couldn't find a picture of me or my family)
</comment>
<div class="image-gallery">
  <img src="{{site.baseurl}}/images/about/cat.jpg" alt="Image 1">
  <img src="{{site.baseurl}}/images/about/dog.jpg" alt="Image 2">
</div>