---
layout: post
codemirror: true
title: Input/Output
description: Input/Output - CS111 Review
permalink: /io
---

| Back | Index | Next |
| ------- | ------ | ------ |
| [Operators](https://moopa01.opencodingsociety.com/operators) | [Index](https://moopa01.opencodingsociety.com/) | [Documentation](https://moopa01.opencodingsociety.com/doc) |


---


<div id="io-app" style="font-family: 'Segoe UI', Arial, sans-serif; max-width: 650px; background: #1a1a1a; padding: 20px; border-radius: 8px; border: 1px solid #333; color: #e0e0e0;">
  <h2 style="margin-top: 0; color: #8c00ff;">Input / Output</h2>
  <p style="color: #bbbbbb;">Click a category to see how the game communicates.</p>

  <div id="io-list"></div>
</div>

<script>
// ----------------------
// INPUT / OUTPUT DATA: Fixed Syntax
// ----------------------
const ioCategories = [
  {
    name: "Canvas Rendering (Output)",
    description: `
      <strong style="color: #8c00ff;">Visual Layer:</strong> Draws what the player sees every frame.<br>
      <pre style="background:#2a2a2a; color: #f8f8f2; padding:8px; margin-top:5px; border-radius:4px; font-size:12px; border: 1px solid #444;">ctx.fillRect(x, y, w, h);
ctx.drawImage(sprite, x, y);</pre>
      <strong>Game Use:</strong> Rendering sprites, backgrounds, and UI animations.
    `
  },
  {
    name: "Keyboard Events (Input)",
    description: `
      <strong style="color: #8c00ff;">User Control:</strong> Listens for physical key presses.<br>
      <pre style="background:#2a2a2a; color: #f8f8f2; padding:8px; margin-top:5px; border-radius:4px; font-size:12px; border: 1px solid #444;">window.addEventListener("keydown", (e) => {
  if (e.key === " ") player.jump();
});</pre>
      <strong>Game Use:</strong> Movement, jumping, and menu navigation.
    `
  },
  {
    name: "GameEnv Config (Input)",
    description: `
      <strong style="color: #8c00ff;">World Rules:</strong> Sets the global physics and environment.<br>
      <pre style="background:#2a2a2a; color: #f8f8f2; padding:8px; margin-top:5px; border-radius:4px; font-size:12px; border: 1px solid #444;">const gameEnv = {
  gravity: 0.4,
  debug: false
};</pre>
      <strong>Game Use:</strong> Defining world size, gravity, and difficulty settings.
    `
  },
  {
    name: "API Calls (I/O)",
    description: `
      <strong style="color: #8c00ff;">External Data:</strong> Communicates with servers.<br>
      <pre style="background:#2a2a2a; color: #f8f8f2; padding:8px; margin-top:5px; border-radius:4px; font-size:12px; border: 1px solid #444;">fetch("/api/score")
  .then(res => res.json())
  .then(data => show(data));</pre>
      <strong>Game Use:</strong> Leaderboards, cloud saves, and dynamic AI behavior.
    `
  }
]; // Array properly closed

// ----------------------
// RENDER: Purple Neon Dark Mode
// ----------------------
const ioContainer = document.getElementById("io-list");

ioCategories.forEach((item, index) => {
  const wrapper = document.createElement("div");
  wrapper.style.marginBottom = "8px";

  const button = document.createElement("button");
  button.textContent = `${index + 1}. ${item.name}`;
  button.style.cssText = `
    width: 100%;
    padding: 12px;
    text-align: left;
    cursor: pointer;
    border: 1px solid #8c00ff;
    border-radius: 4px;
    background: #1a1a1a;
    color: #8c00ff;
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
    button.style.background = "#57197d";
    button.style.color = "white";
  };
  button.onmouseout = () => {
    if (details.style.display !== "block") {
      button.style.background = "#1a1a1a";
      button.style.color = "#8c00ff";
    }
  };

  button.addEventListener("click", () => {
    const isOpen = details.style.display === "block";
    details.style.display = isOpen ? "none" : "block";
    button.style.borderRadius = isOpen ? "4px" : "4px 4px 0 0";
    button.style.background = isOpen ? "#1a1a1a" : "#57197d";
    button.style.color = isOpen ? "#8c00ff" : "white";
  });

  wrapper.appendChild(button);
  wrapper.appendChild(details);
  ioContainer.appendChild(wrapper);
}); // Loop properly closed
</script>

---

⭐ **Overview: Input / Output in Game Development**

Input/Output (I/O) is the communication layer of your game — the bridge between the player, the game world, and external systems. It determines **how your game receives information** (input) and **how it displays or sends information** (output). Without I/O, your game wouldn’t move, react, draw, or communicate.

In practice, I/O covers everything from rendering graphics to handling keyboard input to loading configuration files to making API calls. Below is a deeper look at the four major I/O systems you’re working with.

---

## 🎨 **1. Canvas Rendering (Output)**  
Canvas rendering is how your game draws everything the player sees. It’s the visual output layer responsible for:

- Sprites  
- Backgrounds  
- UI elements  
- Animations  
- Effects (particles, flashes, shadows)  

### **How It Works**
The game uses a rendering context (usually `ctx`) to draw shapes, images, and text onto the canvas every frame.

Examples include:

- `ctx.fillRect(x, y, width, height)`  
- `ctx.drawImage(sprite, x, y)`  

### **Why It Matters**
Canvas rendering is the heartbeat of your game’s visuals. Every frame, it outputs the current state of the world — positions, animations, effects — giving the player a smooth, responsive experience.

---

## ⌨️ **2. Keyboard Event Handlers (Input)**  
Keyboard events are how the player communicates with your game. They provide real‑time input that drives movement, actions, and UI navigation.

### **How It Works**
JavaScript listens for events like:

- `keydown` — when a key is pressed  
- `keyup` — when a key is released  

These events trigger functions that update the player’s state:

- Jumping  
- Moving left/right  
- Attacking  
- Pausing  
- Opening menus  

### **Why It Matters**
Without keyboard input, your game wouldn’t be interactive. Event handlers translate physical key presses into in‑game actions, making the player feel connected to the world.

---

## ⚙️ **3. GameEnv Configuration (Input)**  
GameEnv configuration is the structured input that defines how your game world behaves. It’s not player input — it’s *system input* that sets the rules of the environment.

### **What It Controls**
- Canvas size  
- Gravity  
- Debug mode  
- Physics settings  
- Difficulty  
- Asset paths  
- NPC defaults  

### **Why It Matters**
GameEnv acts as the blueprint for your game world. It ensures consistency, makes tuning easier, and allows you to adjust global behavior without rewriting code. It’s the foundation that everything else builds on.

---

## 🌐 **4. API Calls (Input + Output)**  
API calls allow your game to communicate with external systems — sending data out and receiving data back. This is where your game becomes connected, dynamic, and scalable.

### **Common Uses**
- **Leaderboards:** Fetching top scores  
- **NPC AI:** Requesting behavior profiles  
- **Cloud saves:** Storing player progress  
- **Remote configuration:** Updating difficulty or events  
- **Multiplayer:** Syncing player states  

### **Why It Matters**
API calls extend your game beyond the local machine. They enable online features, dynamic content, and smarter AI. They turn your game into a living system that can evolve over time.

---

🎯 **Why Input/Output Matters**

Input/Output is what makes your game *interactive*, *visual*, and *connected*. It allows your game to:

- Receive player actions  
- Render the world every frame  
- Load configuration and assets  
- Communicate with servers  
- Update dynamically based on external data  

Without I/O, your game would be a static script. With it, you get movement, visuals, AI, UI, and online features — everything that makes a game feel alive.

---

