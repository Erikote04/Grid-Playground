# Grid Layout Playground

## Getting Started

1. Clone the repository: `git clone https://github.com/Erikote04/Grid-Playground.git`

2. Open the `index.html` file in a web browser.

3. Follow the steps down below and become a master in Grid Layout

### Container
```css
.container {
	/* grid template */
	grid-template-rows: ;
	grid-template-columns: ;
	grid-template-areas: ;

	/* grid gap */
	grid-row-gap: ;
	grid-column-gap: ;

	/* items and content */
	justify-items: ;
	align-items: ;
	justify-content: ;
	align-content: ;

	/* implicit grid */
	grid-auto-rows: ;
	grid-auto-columns: ;
	grid-auto-flow: ;
}
```

### Item
```css
.item {
	/* grid area */
		/* grid row */
		grid-row-start: ;
		grid-row-end: ;
		/* grid column */
		grid-column-start: ;
		grid-column-end: ;

	/* item */
	justify-self: ;
	align-self: ;

	/* order */
	order: ;
}
```

### Roadmap

#### `grid-template-rows & grid-template-columns`
```css
.container {
    grid-template-rows: 150px 150px;
    grid-template-columns: 150px 150px 150px;
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 21.28.21.png>)

#### `grid-row-gap & grid-column-gap`
```css
.container {
	grid-gap: 30px;
	/*
    grid-row-gap: 30px;
    grid-column-gap: 30px;
    */
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 21.30.58.png>)

#### `repeat()`
```css
.container {
	grid-template-rows: repeat(2, 150px);
    grid-template-columns: repeat(2, 150px) 300px;
	grid-gap: 30px;
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 21.43.15.png>)

#### `fr`
```css
.container {
	grid-template-rows: repeat(2, 150px);
    grid-template-columns: repeat(2, 150px) 1fr; 
	grid-gap: 30px;
}
/* expands to all the space that it can occuppy */
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 21.45.55.png>)

```css
.container {
	grid-template-rows: repeat(2, 150px);
    grid-template-columns: repeat(3, 1fr); 
	grid-gap: 30px;
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 21.57.01.png>)

```css
.container {
	grid-template-rows: repeat(2, 150px);
    grid-template-columns: 1fr 2fr 1fr; 
	grid-gap: 30px;
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 21.58.37.png>)

#### `%`
```css
.container {
	grid-template-rows: repeat(2, 150px);
    grid-template-columns: 50% 2fr 1fr; 
	grid-gap: 30px;
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 22.01.46.png>)

#### `grid-row-start, grid-row-end, grid-column-start & grid-column-end`
```css
.i1 {
	grid-row-start: 2;
    grid-row-end: 3;
    grid-column-start: 2;
    grid-column-end: 3;
}
```

#### `grid-row & grid-column`
```css
.i1 {
	grid-row: 2 / 3;
	grid-column: 2 / 3;
}
```

#### `grid-area`
```css
.i1 {
	grid-area: 2 / 3 / 2 / 3;
}
```

![alt text](<img/Captura de pantalla 2024-02-04 a las 22.11.11.png>)

#### `span`
```css
.i1 {
	grid-row: 2 / 3;
	grid-column: 2 / span 2;
}
```

```css
.i1 {
	grid-row: 2 / 3;
	grid-column: 2 / -1; /* expands all the way until the end */
}
```

![alt text](<img/Captura de pantalla 2024-02-05 a las 13.07.23.png>)

#### overlay case
```css
.i1 {
	grid-row: 2 / 3;
	grid-column: 2 / 3;
}

.i6 {
	grid-row: 2 / 3;
	grid-column: 1 / 3;
}
```

![alt text](<img/Captura de pantalla 2024-02-05 a las 13.17.13.png>)

```css
.i1 {
	grid-row: 2 / 3;
	grid-column: 2 / 3;
	z-index: 10;
}

.i6 {
	grid-row: 2 / 3;
	grid-column: 1 / 3;
}
```

![alt text](<img/Captura de pantalla 2024-02-05 a las 13.21.25.png>)

#### Challenge
```html
<div class="challenge">
    <div class="header">Header</div>
    <div class="small-box-1">Small Box</div>
    <div class="small-box-2">Small Box</div>
    <div class="small-box-3">Small Box</div>
    <div class="sidebar">Sidebar</div>
    <div class="main-content">Main content</div>
    <div class="footer">Footer</div>
</div>
```

##### Method 1: Line Numbers
```css
.challenge {
    width: 1000px;
    margin: 40px auto;

	display: grid;
	grid-gap: 30px;
	grid-template-rows: 100px 200px 400px 100px;
    grid-template-columns: repeat(3, 1fr) 200px;
}

div > div {
    color: white;
    background-color: red;
    padding: 20px;
    font-size: 30px;
    font-family: sans-serif;
}

.header {
	grid-column: 1 / -1;
}

.sidebar {
    grid-row: 2 / span 2;
    grid-column: 4 / 5;
}

.main-content {
    grid-column: 1 / span 3;
}

.footer {
	grid-column: 1 / -1;
}
```

##### Method 2: Line Names
```css
.challenge {
	grid-template-rows: [header-start] 100px 
						[header-end box-start] 200px 
						[box-end main-start] 400px 
						[main-end footer-start] 100px
						[footer-end];
    grid-template-columns: repeat(3, [col-start] 1fr [col-end]) 200px [grid-end];
}

.header {
	grid-column: col-start 1 / grid-end;
}

.sidebar {
    grid-row: box-start / main-end;
    grid-column: col-end 3 / grid-end;
}

.main-content {
    grid-column: col-start 1 / col-end 3;
}

.footer {
	grid-column: col-start 1 / grid-end;
}
```

##### Method 3: Area Names
```css
.challenge {
	grid-template-rows: 100px 200px 400px 100px;
    grid-template-columns: repeat(3, 1fr) 200px;
    grid-template-areas: "head head head head" 
						 "boxy boxy boxy side" 
						 "main main main side" 
						 "foot foot foot foot";
}

.header {
	grid-area: head;
}

.sidebar {
    grid-area: side;
}

.main-content {
    grid-area: main;
}

.footer {
	grid-area: foot;
}
/* To leave an empty cell you put a "." instead of a name */
```

![alt text](<img/Captura de pantalla 2024-02-05 a las 13.43.11.png>)

#### Implicit Grid vs Explicit Grid
```html
<div class="container">
    <div class="item i1">Modern</div>
    <div class="item i2">CSS</div>
    <div class="item i3">with</div>
    <div class="item i4">Flexbox</div>
    <div class="item i5">and</div>
    <div class="item i6">Grid</div>
    <div class="item i7">is</div>
    <div class="item i8">Great</div>
</div>
```

```css
.container {
    width: 1000px;
    margin: 40px auto;
    background-color: #eee;

	display: grid;
	grid-gap: 30px;
    grid-template-rows: repeat(2, 150px);
    grid-template-columns: repeat(2, 1fr);
}

.item {
    padding: 20px;
    font-size: 30px;
    font-family: sans-serif;
    color: white;
    background-color: red;
}
/* We've only defined 4 cells, but we have 8, so the last 4 go to the Implicit grid */
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 9.57.28.png>)

##### `grid-auto-rows`
```css
.container {
	grid-auto-rows: 100px;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.04.00.png>)

##### `grid-auto-flow & grid-auto-columns`
```css
.container {
	grid-auto-flow: column;
	grid-auto-columns: .5fr;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.08.19.png>)

#### Aligning grid items with grid areas 
```css
.i4 {
    background-color: crimson;
    grid-row: 2 / span 3
}

.i7 {
    background-color: palevioletred;
    grid-column: 1 / -1;
}
```

Before alignment
![alt text](<img/Captura de pantalla 2024-02-06 a las 10.20.47.png>)

##### `align-items: center`
```css
.container {
	align-items: center;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.24.03.png>)

##### `align-items: start`
```css
.container {
	align-items: start;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.26.27.png>)

##### `align-items: end`
```css
.container {
	align-items: end;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.27.12.png>)

##### `justify-items: center`
```css
.container {
	align-items: center; /* vertical */
	justify-items: center; /* horizontal */
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.29.37.png>)

##### `justify-items: start`
```css
.container {
	justify-items: start;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.34.02.png>)

##### `justify-items: end`
```css
.container {
	justify-items: end;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.34.37.png>)

#### `align-self & justify-self`
```css
.container {
	align-items: center; 
	justify-items: center; 
}

.i4 {
	align-self: start;
	justify-self: start;
}
/* The item value overrides the container value. This properties have the same values as align-items and justify-items */
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.38.50.png>)

#### Align grid tracks to grid container

##### `justify-content & align-content`
```css
.container {
    width: 1000px;
    height: 900px;

    grid-template-rows: repeat(2, 100px);
    grid-template-columns: repeat(2, 200px);

	justify-content: center; /* flex-start | flex-end | space-between | space-around | space-evenly *//* horizontal */
	align-content: center; /* stretch | flex-start | flex-end | baseline *//* vertical */
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 10.52.26.png>)

##### dense
```css
.i4 {
    background-color: crimson;
    grid-row: 2 / span 3
}

.i6 {
    background-color: lightcoral;
    grid-row: 2 / span 2;
}

.i7 {
    background-color: palevioletred;
    grid-column: 1 / -1;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 11.02.06.png>)

> We don't want that hole in there, so in the `grid-auto-flow` property, after `row` or `column` value, we put `dense`.

```css
.container {
	grid-auto-flow: row dense;
}
```

![alt text](<img/Captura de pantalla 2024-02-06 a las 11.06.36.png>)

#### `max-content`
```css
.container {
    display: grid;
    grid-template-rows: repeat(2, 150px);
    grid-template-columns: max-content 1fr 1fr max-content;
}
/* Adjust the width of the column to te content (text) */
```

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.11.46.png>)

#### `min-content`
```css
.container {
    display: grid;
    grid-template-rows: repeat(2, 150px);
    grid-template-columns: max-content 1fr 1fr min-content;
}
/* Minimum width the column has to have without overflowing */
```

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.14.00.png>)

#### `minmax()`
```css
.container {
    display: grid;
    grid-template-rows: repeat(2, minmax(150px, min-content));
    grid-template-columns: max-content 1fr 1fr min-content;
}
/* At least 150px and maximum min-content */
```

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.19.33.png>)

#### `auto-fill`
```css
.container {
    display: grid;
    grid-template-rows: repeat(2, minmax(150px, min-content));
    grid-template-columns: repeat(auto-fill, 100px);
}
/* Creates all the columns that can fit */
```

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.29.18.png>)

#### `auto-fit`
```css
.container {
    display: grid;
    grid-template-rows: repeat(2, minmax(150px, min-content));
    grid-template-columns: repeat(auto-fit, 100px);
}
/* Creates all the columns that can fit and collapses empty cells */
```

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.30.42.png>)

```css
.container {
	width: 90%
    display: grid;
    grid-template-rows: repeat(2, minmax(150px, min-content));
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-auto-rows: 150px;
}
/* Automatic responsive desing */
```

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.38.02.png>)

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.39.25.png>)

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.40.08.png>)

![alt text](<img/Captura de pantalla 2024-02-09 a las 10.40.58.png>)
