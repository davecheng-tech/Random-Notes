# P5.js Programming Style & Documentation Guide

Writing clean, readable code is part of being a good programmer. These are the style and documentation rules we use in this class. You will be marked on these!

<!-- vscode-markdown-toc -->
1. [Main Program Documentation](#MainProgramDocumentation)
2. [Custom Function Documentation](#CustomFunctionDocumentation)
3. [Code Organization](#CodeOrganization)
4. [Inline Comments](#InlineComments)
5. [Variable and Function Naming](#VariableandFunctionNaming)
6. [Indentation and Layout](#IndentationandLayout)
7. [Whitespace](#Whitespace)
8. [Use of Semicolons](#UseofSemicolons)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->



##  1. <a name='MainProgramDocumentation'></a>Main Program Documentation

At the very top of your `.js` file, describe what your program does using a block comment like this:

```javascript
/**
 * This program animates a cat walking across a city skyline at night.
 * The background changes color based on the time of day.
 * @author: First Last
 */
```


##  2. <a name='CustomFunctionDocumentation'></a>Custom Function Documentation

Every custom function should start with a descriptive header comment using this format:

```javascript
/**
 * Draws the cat on the screen at its current position.
 */
function drawCat() {
    // code here
}
```



##  3. <a name='CodeOrganization'></a>Code Organization

Structure your program like this:

1. `setup()` function
2. `draw()` function
3. All other built-in or custom functions

Break complex tasks into helper functions like `drawBackground()`, `drawCat()`, and `animateCat()` instead of writing all the logic inside `draw()`.

### <a name='DONT'></a>❌ DON’T

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

### <a name='DO'></a>✅ DO

```javascript
function draw() {
    drawBackground();
    drawBall();
    animateBall();
}
```



##  4. <a name='InlineComments'></a>Inline Comments

Use `//` for short comments where needed. Don't explain the obvious — explain *why*, not *what*.

### <a name='DO-1'></a>✅ DO

```javascript
// Reset ball to left side if it goes offscreen
if (x > width) {
    x = 0;
}
```

### <a name='DONT-1'></a>❌ DON’T

```javascript
x = 0; // Set x to 0
```



##  5. <a name='VariableandFunctionNaming'></a>Variable and Function Naming

- Use **descriptive names** that reflect what the variable or function does.
- Use **camelCase**: lowercase first word, uppercase for each next word.

### <a name='DO-1'></a>✅ DO

```javascript
let centerX = 300;
function drawBunny(x, y, color) { ... }
```

### <a name='DONT-1'></a>❌ DON'T

```javascript
let cx = 300;
function db(x, y, c) { ... }
```



##  6. <a name='IndentationandLayout'></a>Indentation and Layout

- Use **consistent indentation** (usually 4 spaces or a tab).
- Line up opening and closing brackets.
- Break code into logical blocks with blank lines separating them.

### <a name='DO-1'></a>✅ DO

```javascript
function draw() {
    drawBunny(100, 100, "white");
    drawEggSushi(150, 100);
}
```

### <a name='DONT-1'></a>❌ DON'T

```javascript
function draw(){
drawBunny(100,100,"white");
drawEggSushi(150,100);}
```



##  7. <a name='Whitespace'></a>Whitespace

- Add spaces after commas and around operators (`=`, `+`, etc.).
- Don’t cram everything together.

###  <a name='DO-1'></a>✅ DO

```javascript
let x = 100;
circle(x + 50, 200, 25);
```

###  <a name='DONT-1'></a>❌ DON'T

```javascript
let x=100;
circle(x+50,200,25);
```



##  8. <a name='UseofSemicolons'></a>Use of Semicolons

JavaScript doesn’t require semicolons, but **you should always use them** to avoid weird bugs and keep your style consistent.

###  <a name='DO-1'></a>✅ DO

```javascript
let x = 100;
fill("blue");
circle(x, 200, 50);
```

###  <a name='DONT-1'></a>❌ DON'T

```javascript
let x = 100
fill("blue")
circle(x, 200, 50)
```