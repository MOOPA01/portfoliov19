---
layout: post
codemirror: true
title: Control Structures
description: Control Structures - CS111 Review
permalink: /controlStructures
---

| Back | Index | Next |
| ------- | ------ | ------ |
| [OOP](https://moopa01.opencodingsociety.com/OOP) | [Index](https://moopa01.opencodingsociety.com/) | [Data Types](https://moopa01.opencodingsociety.com/data) |


---

<div id="control-app" style="font-family: 'Segoe UI', Arial, sans-serif; max-width: 650px; background: #1a1a1a; padding: 20px; border-radius: 8px; border: 1px solid #333; color: #e0e0e0;">
  <h2 style="margin-top: 0; color: #00ddff;">Control Structures</h2>
  <p style="color: #bbbbbb;">Click a category to see examples and game use cases.</p>

  <div id="control-list"></div>
</div>

<script>
// ----------------------
// DATA: Fixed Brackets & Braces
// ----------------------
const controlStructures = [
  {
    name: "Iteration (Loops)",
    description: `
      <strong style="color: #00ddff;">How it works:</strong> Repeats code while a condition is met.<br>
      <code style="background: #2a2a2a; color: #f8f8f2; padding: 2px 4px;">for (let i = 0; i < 5; i++)</code> <br>
      <strong>Game Use:</strong> Updating all 60 sprites every frame or checking collisions in a list.
    `
  },
  {
    name: "Conditions (If / Else)",
    description: `
      <strong style="color: #00ddff;">How it works:</strong> Branches logic based on true/false checks.<br>
      <code style="background: #2a2a2a; color: #f8f8f2; padding: 2px 4px;">if (health <= 0) { die(); }</code> <br>
      <strong>Game Use:</strong> Triggering a 'Game Over' screen or handling keyboard input.
    `
  },
  {
    name: "Nested Conditions",
    description: `
      <strong style="color: #00ddff;">How it works:</strong> Places checks inside checks for complex logic.<br>
      <pre style="background:#2a2a2a; color: #f8f8f2; padding:8px; margin-top:5px; border-radius:4px; font-size:12px; border: 1px solid #444;">if (enemy.isHostile) {
  if (distance < 50) {
    enemy.attack();
  }
}</pre>
      <strong>Game Use:</strong> Advanced AI (e.g., "If enemy is alert AND player is in range").
    `
  }
]; // Array properly closed

// ----------------------
// RENDER: Clean Dark Logic
// ----------------------
const controlContainer = document.getElementById("control-list");

controlStructures.forEach((item, index) => {
  const wrapper = document.createElement("div");
  wrapper.style.marginBottom = "8px";

  const button = document.createElement("button");
  button.textContent = `${index + 1}. ${item.name}`;
  button.style.cssText = `
    width: 100%;
    padding: 12px;
    text-align: left;
    cursor: pointer;
    border: 1px solid #00ddff;
    border-radius: 4px;
    background: #1a1a1a;
    color: #00ddff;
    font-size: 16px;
    font-weight: bold;
    transition: all 0.2s ease;
  `;

  const details = document.createElement("div");
  details.style.cssText = `
    display: none;
    padding: 15px;
    border: 1px solid #333;
    border-top: none;
    background: #222222;
    color: #dddddd;
    font-size: 14px;
    line-height: 1.5;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  `;
  details.innerHTML = item.description;

  // Hover and Click Logic
  button.onmouseover = () => {
    button.style.background = "#4692a7";
    button.style.color = "white";
  };
  button.onmouseout = () => {
    if (details.style.display !== "block") {
        button.style.background = "#1a1a1a";
        button.style.color = "#00ddff";
    }
  };

  button.addEventListener("click", () => {
    const isOpen = details.style.display === "block";
    details.style.display = isOpen ? "none" : "block";
    button.style.borderRadius = isOpen ? "4px" : "4px 4px 0 0";
    button.style.background = isOpen ? "#1a1a1a" : "#4692a7";
    button.style.color = isOpen ? "#00ddff" : "white";
  });

  wrapper.appendChild(button);
  wrapper.appendChild(details);
  controlContainer.appendChild(wrapper);
}); // Loop properly closed
</script>

---

⭐ **Overview: Control Structures in Programming**

Control structures are the decision‑making and flow‑controlling tools of programming. They determine **how**, **when**, and **how many times** code runs. Without them, a program would simply execute line‑by‑line with no ability to react, repeat, or branch — which would make games, AI, physics, and interactive systems impossible.

In game development especially, control structures shape everything from enemy behavior to movement loops to UI logic. They allow your code to respond dynamically to the player and the game world.

Below are the three core control structures you’re working with: **iteration**, **conditions**, and **nested conditions**.

---

## 🔁 **1. Iteration (Loops)**  
Iteration allows code to repeat actions multiple times. Instead of writing the same line of code over and over, loops let you automate repetition — essential in a game that updates dozens of objects every frame.

### **Common Loop Types**
- **For loop:** Runs a set number of times  
  `for (let i = 0; i < 5; i++)`
- **While loop:** Runs as long as a condition is true  
  `while (enemy.health > 0)`
- **For...of loop:** Iterates through arrays  
  `for (const obj of gameObjects)`

### **Where It Matters in Games**
- Updating all sprites each frame  
- Checking collisions across many objects  
- Running AI logic  
- Animating sequences  
- Processing inventory or level data  

Iteration is the engine that keeps your game world moving.

---

## 🔍 **2. Conditions (If / Else)**  
Conditions allow your code to make decisions. They check whether something is true or false and choose what to do next. This is the foundation of game logic — everything from health checks to AI reactions relies on conditions.

### **Common Condition Patterns**
- **Basic check:**  
  `if (health <= 0)`
- **If / else:**  
  `if (isPaused) { ... } else { ... }`
- **Else if:**  
  `else if (state === "hostile")`

### **Where It Matters in Games**
- Game state transitions (menu, pause, combat)  
- AI behavior (attack, flee, patrol)  
- Input handling  
- Trigger zones and events  
- Health, damage, and win/lose conditions  

Conditions give your game the ability to *react*.

---

## 🧠 **3. Nested Conditions**  
Nested conditions are conditions *inside* other conditions. They allow for more complex decision‑making — the kind of layered logic that real gameplay requires.

### **Example**
```js
if (enemy.isHostile) {
    if (distance < 50) {
        enemy.attack();
    }
}
```

### **Where It Matters in Games**
- AI decision trees  
- Proximity checks  
- Multi‑step logic (e.g., “if the player is close AND the enemy is hostile…”)  
- Handling multiple states at once  
- Complex interactions between objects  

Nested conditions let your game make smarter, more nuanced decisions.

---

🎯 **Why Control Structures Matter**

Control structures are the backbone of dynamic, interactive programming. They allow your game to:

- Repeat actions efficiently  
- Respond to player input  
- Make decisions based on game state  
- Handle complex AI behavior  
- Update dozens of objects every frame  
- Create branching logic and varied outcomes  

Without control structures, your game would be static and predictable. With them, you can build systems that feel alive, responsive, and intelligent.

---
