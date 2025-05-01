# P5.js Programming Style Guide

Writing clean, readable code is part of being a good programmer. These are the style rules we use in this class. You will be marked on these!

<br>

## Variable and Function Naming

- Use **descriptive names** that reflect what the variable or function does.
- Use **camelCase**: lowercase first word, uppercase for each next word.

### ✅ DO
```javascript
let centerX = 300;
function drawBunny(x, y, color) { ... }
```

### ❌ DON'T
```javascript
let cx = 300;
function db(x, y, c) { ... }
```

<br>

## Comments

- Use comments to **explain what your code is doing**, especially in `draw()` or inside complex functions.
- Use `//` for short comments and `/** */` for function documentation.

### ✅ DO
```javascript
// Draws a row of bunnies and sushi
drawBunny(100, 100, "white");

/**
 * Draws a bunny at (x, y) with the given color.
 */
function drawBunny(x, y, color) { ... }
```

### ❌ DON'T
```javascript
drawBunny(100, 100, "white"); // bunny
function drawBunny(x, y, color) { ... } // draws bunny
```

<br>

## Indentation and Layout

- Use **consistent indentation** (usually 4 spaces or a tab).
- Line up opening and closing brackets.
- Break code into logical blocks with blank lines separating.

### ✅ DO
```javascript
function draw() {
    drawBunny(100, 100, "white");
    drawEggSushi(150, 100);
}
```

### ❌ DON'T
```javascript
function draw(){
drawBunny(100,100,"white");
drawEggSushi(150,100);}
```

<br>

## Whitespace

- Add spaces after commas and around operators (`=`, `+`, etc.).
- Don't cram everything together.

### ✅ DO
```javascript
let x = 100;
circle(x + 50, 200, 25);
```

### ❌ DON'T
```javascript
let x=100;
circle(x+50,200,25);
```

<br>

## Use of Semicolons

- JavaScript doesn’t require semicolons, but **you should always use them** to avoid weird bugs and keep your style consistent.

### ✅ DO
```javascript
let x = 100;
fill("blue");
circle(x, 200, 50);
```

### ❌ DON'T
```javascript
let x = 100
fill("blue")
circle(x, 200, 50)
```
