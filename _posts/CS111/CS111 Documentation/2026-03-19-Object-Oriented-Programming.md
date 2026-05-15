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

# Object-Oriented Programming

OOP organizes code into **classes** — blueprints that bundle data and behavior together. In games, this means building reusable, layered objects like characters, enemies, and items.

---

```mermaid
classDiagram
    class GameObject {
        +position
        +draw()
    }
    class Character {
        +movement
        +gravity
        +update()
    }
    class Player {
        +handleKeyInput()
    }
    class Pirate {
        +isHostile = true
        +handleCollision()
        +checkProximity()
    }

    GameObject <|-- Character
    Character <|-- Player
    Character <|-- Pirate
```

---

## The Four Pillars

**Encapsulation** — bundle data and behavior into one unit
Each class owns its own properties and methods. Outside code can't accidentally break internal state.
```js
this.type = "Pirate";
this.isHostile = true;
```

---

**Inheritance** — child classes reuse parent logic
`Pirate extends Character` means Pirate gets position, sprite, movement, and physics for free — then adds its own behavior on top.
```js
class Pirate extends Character { ... }
```

---

**Polymorphism** — child classes override parent behavior
The parent defines `handleCollision()`, but Pirate replaces it with its own hostile logic. Same method name, different behavior.
```js
handleCollision(other, direction) {
    if (other instanceof Player) {
        if (this.distanceTo(other) < 50) {
            this.reaction("hostile");
        }
    }
}
```

---

**Abstraction** — hide complexity, expose only what's needed
`super.update()` runs all parent logic in one call — movement, animation, physics — without the Pirate needing to know how any of it works.
```js
update() {
    super.update();        // all parent logic runs here
    this.checkProximity(); // then add pirate-specific behavior
}
```

---

| Concept | Keyword | What it gives you |
|---------|---------|-------------------|
| Encapsulation | `this.` | Self-contained objects |
| Inheritance | `extends` | Reusable parent logic |
| Polymorphism | method override | Custom behavior per class |
| Abstraction | `super()` | Simplified interface to complex logic |

> **Pattern to remember:** call `super()` first to keep parent behavior, then add your own. Extend — don't replace.