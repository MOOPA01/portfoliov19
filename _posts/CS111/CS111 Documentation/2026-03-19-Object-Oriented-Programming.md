---
layout: post
codemirror: true
title: Object Oriented Programming
description: Object Oriented Programming- CS111 Review
permalink: /OOP
---

| Back | Index | Next |
| ------- | ------ | ------ |
| [Testing & Verification](https://moopa01.opencodingsociety.com/testVerify) | [Index](https://moopa01.opencodingsociety.com/) | [Control Structures](https://moopa01.opencodingsociety.com/controlStructures) |

---


<div id="oop-app" style="font-family: 'Segoe UI', Arial, sans-serif; max-width: 650px; background: #f9f9f9; padding: 20px; border-radius: 8px; border: 1px solid #ddd;">
  <h2 style="margin-top: 0; color: #333;">Object-Oriented Programming</h2>
  <p style="color: #666;">Click a concept to expand details.</p>

  <div id="oop-list"></div>
</div>

<script>
// ----------------------
// SHORTENED OOP DATA
// ----------------------
const oopConcepts = [
  {
    name: "Encapsulation",
    description: "Bundles data (properties) and methods (logic) into one unit. It hides internal state to protect data from outside interference."
  },
  {
    name: "Inheritance",
    description: "Allows a 'child' class to reuse code from a 'parent' class. It creates a hierarchy and eliminates redundant code."
  },
  {
    name: "Polymorphism",
    description: "The ability for different classes to be treated as instances of the same general class through the same interface (e.g., overriding methods)."
  },
  {
    name: "Abstraction",
    description: "Hiding complex background details and only showing the essential features of an object to the user."
  }
];

// ----------------------
// RENDER OOP VIEWER
// ----------------------
const oopContainer = document.getElementById("oop-list");

oopConcepts.forEach((concept, index) => {
  const item = document.createElement("div");
  item.style.marginBottom = "8px";

  // Styled Button
  const button = document.createElement("button");
  button.textContent = `${index + 1}. ${concept.name}`;
  button.style.cssText = `
    width: 100%;
    padding: 12px;
    text-align: left;
    cursor: pointer;
    border: none;
    border-radius: 4px;
    background: #cc6516;
    color: white;
    font-size: 16px;
    font-weight: bold;
    transition: background 0.2s ease;
  `;

  // Content Box (Fixed white-on-white)
  const details = document.createElement("div");
  details.style.cssText = `
    display: none;
    padding: 15px;
    border: 1px solid #cc6516;
    border-top: none;
    background: #ffffff;
    color: #222222;
    font-size: 14px;
    line-height: 1.5;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  `;
  details.textContent = concept.description;

  // Hover and Click Logic
  button.onmouseover = () => button.style.background = "#e67e22";
  button.onmouseout = () => button.style.background = "#cc6516";
  
  button.addEventListener("click", () => {
    const isOpen = details.style.display === "block";
    details.style.display = isOpen ? "none" : "block";
    button.style.borderRadius = isOpen ? "4px" : "4px 4px 0 0";
  });

  item.appendChild(button);
  item.appendChild(details);
  oopContainer.appendChild(item);
});
</script>

### Inheritance Hierarchy
```text
GameObject        ← Level 1: shared position and draw logic
  └── Character   ← Level 2: adds movement and gravity
        ├── Player  ← Level 3: handles user keyboard input
        └── Pirate    ← Level 3: handles hostile logic
```
### Used In Code!

```javascript
class Pirate extends Character {
    constructor(data, gameEnv) {
        super(data, gameEnv);  // passes setup data to parent class
        this.type = "Pirate";
        this.isHostile = true; // boolean flag
    }

    handleCollision(other, direction) { // 2 parameters
        if (other instanceof Player) {       // condition
            if (this.distanceTo(other) < 50) { // nested condition
                this.reaction("hostile");
            }
        }
    }

    update() {
        super.update(); // calls parent update, then adds wolf behavior
        this.checkProximity();
    }
}
```

---

# 🏴‍☠️ ## Explanation of the Pirate Class

---

## 🔷 **1. Class Declaration**

```js
class Pirate extends Character {
```

- `Pirate` is a new class.
- It **extends** `Character`, meaning it inherits all the properties and methods from the `Character` class.
- This is **inheritance**, one of the core pillars of OOP.

---

## 🔷 **2. Constructor**

```js
constructor(data, gameEnv) {
    super(data, gameEnv);  // passes setup data to parent class
    this.type = "Pirate";
    this.isHostile = true; // boolean flag
}
```

### What happens here:

- The constructor runs when a new Pirate is created.
- `super(data, gameEnv)` calls the parent `Character` constructor so the Pirate gets:
  - position  
  - sprite  
  - movement logic  
  - collision setup  
  - any other shared character features  

### Then you add Pirate‑specific properties:

- `this.type = "Pirate"`  
  Helps identify the object in the game.

- `this.isHostile = true`  
  Marks this character as an enemy.

This is **encapsulation** — the Pirate stores its own data and behavior.

---

## 🔷 **3. Collision Handling**

```js
handleCollision(other, direction) {
    if (other instanceof Player) {       // condition
        if (this.distanceTo(other) < 50) { // nested condition
            this.reaction("hostile");
        }
    }
}
```

### What this does:

1. This method runs whenever the Pirate collides with something.
2. `other instanceof Player`  
   Checks if the Pirate collided with the player.
3. `this.distanceTo(other) < 50`  
   Makes sure the player is close enough to trigger aggression.
4. `this.reaction("hostile")`  
   Tells the Pirate to react aggressively — maybe an animation, sound, or attack.

This is **polymorphism** — the Pirate overrides the parent’s collision behavior with its own.

---

## 🔷 **4. Update Loop**

```js
update() {
    super.update(); // calls parent update, then adds pirate behavior
    this.checkProximity();
}
```

### What this does:

- `super.update()`  
  Runs the normal character update logic (movement, animation, physics).
- `this.checkProximity()`  
  Adds Pirate‑specific behavior each frame — likely checking if the player is near.

This is a common OOP pattern:  
**extend the parent behavior without replacing it.**

---

# 🧠 **In Summary**

| Feature | What It Demonstrates |
|--------|------------------------|
| `extends Character` | Inheritance |
| `super()` | Using parent class setup |
| `handleCollision()` override | Polymorphism |
| Pirate‑specific properties | Encapsulation |
| `update()` override | Custom behavior layered on top of parent logic |


---
