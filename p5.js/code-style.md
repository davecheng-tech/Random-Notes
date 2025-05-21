# P5.js Programming Style & Documentation Guide

Writing clean, readable code is part of being a good programmer. These are the style and documentation rules we use in this class. You will be marked on these!

## Main Program Documentation

At the very top of your `.js` file, describe what your program does using a block comment like this:

```javascript
/**
 * This program animates a cat walking across a city skyline at night.
 * The background changes color based on the time of day.
 * @author: First Last
 */
```


## Custom Function Documentation

Every custom function should start with a descriptive header comment using this format:

```javascript
/**
 * Draws the cat on the screen at its current position.
 */
function drawCat() {
    // code here
}
```



## Code Organization

Structure your program like this:

1. `setup()` function
2. `draw()` function
3. All other built-in or custom functions

Break complex tasks into helper functions like `drawBackground()`, `drawCat()`, and `animateCat()` instead of writing all the logic inside `draw()`.

### ❌ DON’T

```javascript
function draw() {
    background(0);
    fill(255, 0, 0);
    ellipse(x, y, 50, 50);
    x += 2;
    if (x > width) {
        x = 0;
    }
}
```

### ✅ DO

```javascript
function draw() {
    drawBackground();
    drawBall();
    animateBall();
}
```



## Inline Comments

Use `//` for short comments where needed. Don't explain the obvious — explain *why*, not *what*.

### ✅ DO

```javascript
// Reset ball to left side if it goes offscreen
if (x > width) {
    x = 0;
}
```

### ❌ DON’T

```javascript
x = 0; // Set x to 0
```



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



## Indentation and Layout

- Use **consistent indentation** (usually 4 spaces or a tab).
- Line up opening and closing brackets.
- Break code into logical blocks with blank lines separating them.

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



## Whitespace

- Add spaces after commas and around operators (`=`, `+`, etc.).
- Don’t cram everything together.

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



## Use of Semicolons

JavaScript doesn’t require semicolons, but **you should always use them** to avoid weird bugs and keep your style consistent.

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



## Final Step: Beautify Before Submitting

Before submitting, run your code through [https://beautifier.io/](https://beautifier.io/) to clean up your formatting.



Clean code is readable code. Write it like someone else will have to read and understand it — because they will.