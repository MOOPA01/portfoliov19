---
layout: post
codemirror: true
title: Data Types
description: Data Types - CS111 Review
permalink: /data
---

| Back | Index | Next |
| ------- | ------ | ------ |
| [Control Structures](https://moopa01.opencodingsociety.com/controlStructures) | [Index](https://moopa01.opencodingsociety.com/) | [Operators](https://moopa01.opencodingsociety.com/operators) |


---


<div id="datatype-app" style="font-family: 'Segoe UI', Arial, sans-serif; max-width: 650px; background: #1a1a1a; padding: 20px; border-radius: 8px; border: 1px solid #333; color: #e0e0e0;">
  <h2 style="margin-top: 0; color: #f700ff;">Data Types</h2>
  <p style="color: #bbbbbb;">Click a type to see how it's used in game logic.</p>

  <div id="datatype-list"></div>
</div>

<script>
// ----------------------
// DATA TYPES: Fixed Syntax
// ----------------------
const dataTypes = [
  {
    type: "Number",
    example: "velocity: 3",
    usage: "Handling physics, health points, and movement speed."
  },
  {
    type: "String",
    example: '"hostile"',
    usage: "Defining NPC states, sprite file paths, and UI text."
  },
  {
    type: "Boolean",
    example: "isPaused: true",
    usage: "Binary flags for game logic (e.g., isJumping, isAlive)."
  },
  {
    type: "Array",
    example: "gameObjects[]",
    usage: "Storing lists of enemies, bullets, or inventory items."
  },
  {
    type: "JSON Object",
    example: '{ hitbox: { width: 40 } }',
    usage: "Complex configurations for NPCs or level settings."
  }
]; // Array properly closed

// ----------------------
// RENDER: Neon Dark Mode
// ----------------------
const dtContainer = document.getElementById("datatype-list");

dataTypes.forEach((item, index) => {
  const wrapper = document.createElement("div");
  wrapper.style.marginBottom = "8px";

  // Styled Button
  const button = document.createElement("button");
  button.textContent = `${index + 1}. ${item.type}`;
  button.style.cssText = `
    width: 100%;
    padding: 12px;
    text-align: left;
    cursor: pointer;
    border: 1px solid #f700ff;
    border-radius: 4px;
    background: #1a1a1a;
    color: #f700ff;
    font-size: 16px;
    font-weight: bold;
    transition: all 0.2s ease;
  `;

  // Content Box (Fixed visibility)
  const details = document.createElement("div");
  details.style.display = "none";
  details.style.padding = "10px";
  details.style.border = "1px solid #ddd";
  details.style.borderTop = "none";
  details.style.background = "#fff";
  details.style.lineHeight = "1.6";

  details.innerHTML = `
    <p><strong>Example:</strong> <code>${item.example}</code></p>
    <p><strong>Where Used:</strong> ${item.usage}</p>
  `;

  // Hover and Click Logic
  button.onmouseover = () => {
    button.style.background = "#c020a0";
    button.style.color = "white";
  };
  button.onmouseout = () => {
    if (details.style.display !== "block") {
      button.style.background = "#1a1a1a";
      button.style.color = "#f700ff";
    }
  };

  button.addEventListener("click", () => {
    const isOpen = details.style.display === "block";
    details.style.display = isOpen ? "none" : "block";
    button.style.borderRadius = isOpen ? "4px" : "4px 4px 0 0";
    button.style.background = isOpen ? "#1a1a1a" : "#c020a0";
    button.style.color = isOpen ? "#f700ff" : "white";
  });

  wrapper.appendChild(button);
  wrapper.appendChild(details);
  dtContainer.appendChild(wrapper);
}); // Loop properly closed
</script>

---

⭐ **Overview: Data Types in Game Development**

Data types are the fundamental building blocks of all programming. They define *what kind of information* your code is working with and determine how that information behaves. In game development, choosing the right data type isn’t just a technical detail — it affects performance, clarity, and how easily systems interact with each other.

Below is a deeper look at the core data types you’re using, along with how they appear in real game systems.

---

## 🔢 **1. Number**
Numbers represent any kind of numeric value: speed, health, position, timers, damage, and more.

### **Example**
`velocity: 3`

### **Where It’s Used**
- Physics calculations  
- Movement speed  
- Animation timing  
- Hit detection  
- Cooldowns and timers  

Numbers are the backbone of anything that changes over time. If something moves, rotates, jumps, or counts down, a number is behind it.

---

## 📝 **2. String**
Strings store text — but in games, they’re often used for *labels*, *states*, and *paths* rather than long sentences.

### **Example**
`"hostile"`

### **Where It’s Used**
- NPC states (`"idle"`, `"patrol"`, `"hostile"`)  
- File paths for sprites or audio  
- Dialogue or UI text  
- Identifiers for items, quests, or events  

Strings help your game understand *what something is* or *what mode it’s in*.

---

## ✔️ **3. Boolean**
Booleans represent true/false values — simple but incredibly powerful for controlling game logic.

### **Example**
`isPaused: true`

### **Where It’s Used**
- Game loop control  
- Collision toggles  
- AI behavior flags  
- Visibility or invincibility states  
- Input handling  

Booleans act like switches that turn features or behaviors on and off.

---

## 📦 **4. Array**
Arrays store lists of related items. In games, they’re essential for managing groups of objects.

### **Example**
`gameObjects[]`

### **Where It’s Used**
- All active sprites in the scene  
- Lists of enemies, bullets, particles, or items  
- Pathfinding nodes  
- Inventory systems  
- Level data  

Arrays let you loop through many objects and update them efficiently each frame.

---

## 🧩 **5. JSON Object**
JSON objects store structured data — perfect for configuration, settings, and anything with multiple properties.

### **Example**
`{ hitbox: { width: 40 } }`

### **Where It’s Used**
- NPC configuration (speed, health, hitbox, AI settings)  
- Level definitions  
- Save files  
- Dialogue trees  
- Game settings  

JSON objects let you group related information together in a clean, readable format.

---

🎯 **Why Data Types Matter**

Understanding data types helps you:

- Write cleaner, more predictable code  
- Avoid bugs caused by mismatched values  
- Structure game systems more effectively  
- Communicate intent to other developers  
- Build scalable features that won’t break later  

In game development, data types aren’t just technical details — they shape how your entire game behaves. Mastering them gives you control over movement, AI, physics, UI, and every system that makes your game come alive.

---

