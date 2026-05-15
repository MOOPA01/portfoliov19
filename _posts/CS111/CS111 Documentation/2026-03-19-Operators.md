---
layout: post
codemirror: true
title: Operators
description: Operators - CS111 Review
permalink: /operators
---

| Back | Index | Next |
| ------- | ------ | ------ |
| [Data Types](https://moopa01.opencodingsociety.com/data) | [Index](https://moopa01.opencodingsociety.com/) | [Input/Output](https://moopa01.opencodingsociety.com/io) |

---

<div id="operators-app" style="font-family: 'Segoe UI', Arial, sans-serif; max-width: 650px; background: #1a1a1a; padding: 20px; border-radius: 8px; border: 1px solid #333; color: #e0e0e0;">
  <h2 style="margin-top: 0; color: #ffea04;">Operators</h2>
  <p style="color: #bbbbbb;">Click a category to see operators in action.</p>

  <div id="operators-list"></div>
</div>

<script>
// ----------------------
// OPERATORS DATA: Fixed Syntax
// ----------------------
const operatorCategories = [
  {
    name: "String Operations",
    description: `
      <strong style="color: #ffea04;">Concatenation:</strong> <code>"Hi " + name</code><br>
      <strong style="color: #ffea04;">Template Literals:</strong> <code>\`HP: \${hp}\`</code><br>
      <strong style="color: #ffea04;">Access:</strong> <code>"wolf"[0]</code> → "w"<br>
      <strong>Game Use:</strong> Building dynamic UI text, file paths, and NPC state labels.
    `
  },
  {
    name: "Mathematical Operations",
    description: `
      <strong style="color: #ffea04;">Basic:</strong> <code>+</code>, <code>-</code>, <code>*</code>, <code>/</code><br>
      <strong style="color: #ffea04;">Modulo:</strong> <code>frame % 60</code> (Great for timing!)<br>
      <strong>Game Use:</strong> Movement physics, damage calculations, and animation frame logic.
    `
  },
  {
    name: "Boolean Expressions",
    description: `
      <strong style="color: #ffea04;">Logic:</strong> <code>&&</code> (AND), <code>||</code> (OR), <code>!</code> (NOT)<br>
      <strong style="color: #ffea04;">Comparison:</strong> <code>===</code>, <code>></code>, <code><</code><br>
      <strong>Game Use:</strong> AI decision making, collision detection, and game state toggles.
    `
  }
]; // Array properly closed

// ----------------------
// RENDER: Neon Gold Dark Mode
// ----------------------
const opContainer = document.getElementById("operators-list");

operatorCategories.forEach((category, index) => {
  const wrapper = document.createElement("div");
  wrapper.style.marginBottom = "8px";

  // Styled Button
  const button = document.createElement("button");
  button.textContent = `${index + 1}. ${category.name}`;
  button.style.cssText = `
    width: 100%;
    padding: 12px;
    text-align: left;
    cursor: pointer;
    border: 1px solid #ffea04;
    border-radius: 4px;
    background: #1a1a1a;
    color: #ffea04;
    font-size: 16px;
    font-weight: bold;
    transition: all 0.2s ease;
  `;

  // Content Box
  const details = document.createElement("div");
  details.style.cssText = `
    display: none;
    padding: 15px;
    border: 1px solid #333;
    border-top: none;
    background: #222222;
    color: #dddddd;
    font-size: 14px;
    line-height: 1.6;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  `;
  details.innerHTML = category.description;

  // Hover and Click Logic
  button.onmouseover = () => {
    button.style.background = "#cfa530";
    button.style.color = "white";
  };
  button.onmouseout = () => {
    if (details.style.display !== "block") {
      button.style.background = "#1a1a1a";
      button.style.color = "#ffea04";
    }
  };

  button.addEventListener("click", () => {
    const isOpen = details.style.display === "block";
    details.style.display = isOpen ? "none" : "block";
    button.style.borderRadius = isOpen ? "4px" : "4px 4px 0 0";
    button.style.background = isOpen ? "#1a1a1a" : "#cfa530";
    button.style.color = isOpen ? "#ffea04" : "white";
  });

  wrapper.appendChild(button);
  wrapper.appendChild(details);
  opContainer.appendChild(wrapper);
}); // Loop properly closed
</script>

---

⭐ **Overview: Operators in Programming**

Operators are the tools that allow code to *do things* — combine values, compare them, transform them, or make decisions based on them. They’re the small symbols and expressions that power movement, logic, AI behavior, UI updates, and nearly every calculation inside a game.

Even though operators look simple, they’re essential for building dynamic, interactive systems. Understanding them helps you write cleaner logic, avoid bugs, and express ideas more clearly in code.

Below are the three major categories of operators you’re using: **string operations**, **mathematical operations**, and **boolean expressions**.

---

## 📝 **1. String Operations**
Strings represent text, but in game development they’re often used for *labels*, *states*, and *paths*. Operators let you combine and manipulate these strings to build dynamic messages or control game logic.

### **Common String Operations**
- **Concatenation:**  
  `"Player " + name` → `"Player Samag"`
- **Template literals:**  
  `` `Health: ${hp}` ``
- **Length:**  
  `"hostile".length` → `7`
- **Character access:**  
  `"wolf"[0]` → `"w"`

### **Where They Matter in Games**
- NPC states (`"idle"`, `"hostile"`, `"patrol"`)
- File paths for sprites and audio
- UI text and debug logs
- Dialogue systems

Strings help your game *describe* what’s happening.

---

## 🔢 **2. Mathematical Operations**
Math operators control movement, physics, timing, and any system that changes over time. They’re the backbone of gameplay mechanics.

### **Common Math Operators**
- **Addition:** `speed + 1`
- **Subtraction:** `health - 10`
- **Multiplication:** `velocity * 2`
- **Division:** `distance / time`
- **Modulo:** `frame % 60` (useful for timing events)

### **Where They Matter in Games**
- Movement and acceleration  
- Gravity and physics  
- Damage calculations  
- Animation timing  
- Cooldowns and timers  

If something moves, rotates, jumps, or ticks — math operators are behind it.

---

## ✔️ **3. Boolean Expressions**
Boolean expressions evaluate to **true** or **false**, making them essential for decision‑making. They determine whether an action should happen, whether a character should attack, or whether the game should pause.

### **Common Boolean Expressions**
- **Comparison:** `health > 0`
- **Equality:** `state === "hostile"`
- **Logical AND:** `isAlive && isVisible`
- **Logical OR:** `isPaused || isMenuOpen`
- **Negation:** `!isAttacking`

### **Where They Matter in Games**
- AI behavior  
- Collision detection  
- Game loop control  
- Input handling  
- Trigger zones and events  

Booleans are the switches that turn game logic on and off.

---

🎯 **Why Operators Matter**

Operators are the glue that connects your data and your logic. They allow your game to:

- React to player input  
- Update physics and movement  
- Make decisions through AI  
- Display dynamic text  
- Control timing and animation  
- Evaluate conditions and states  

Even though operators are small symbols, they shape how your entire game behaves. Mastering them gives you precise control over gameplay, performance, and the flow of your code.

---
