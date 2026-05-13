# Interview

| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 |
|----------|----------|----------|----------|----------|
|[Structure of HTML Document](#structure-of-HTML-document)|[HTML and HTML5](#html-and-html5)|
|[```<meta>```](#meta)|[Semantic tags and Non-semantic tags](#semantic-tags-and-non-semantic-tags)|[]()|[]()|[]()|
|[```<div>``` and ```<span>```](#div-and-span)|[Inline and Block elements](#inline-and-block-elements)|
|[CSS styling in HTML](#css-styling-in-html)|[```<strong>``` and ```<b>``` tage](#strong-and-b-tage)|
|[```<section>```, ```<article>```, ```<div>```](#section-article-div)||

## Structure of HTML Document
1. ```<!DOCTYPE html>``` -> Tells the browser that this document uses HTML5.
2. ```<html lang="en">``` -> Root element of the HTML document. Inside define ```lang="en"``` language as English.
3. ```<head>``` -> Stores metadata and settings of webpage. ```<metadata>,<title>```.
4. ```<meta charset="UTF-8">``` -> Supports all characters and symbols.UTF-8 allows browser to display different languages and special characters properly.
5. ```<title>``` -> Shows title in browser tab.
6. ```<link>``` -> Link tag is used to connect external resources like CSS files.
7. ```<style>``` -> Used for internal CSS.
8. ```<script>``` -> Used to write JavaScript.
9. ```<body>``` -> Body tag contains all the visible elements shown to the user.

[⬆ Back to Top](#Interview)

## HTML and HTML5
```HTML```
- ```HTML``` stands for ```HyperText Markup Language```. It is used to create the structure of web pages.
- Headings, Paragraphs, Forms, Tables, Images, Links, Buttons

```HTML5```
- HTML5 is the latest version of HTML.
- It introduced-> Semantic tags, Audio & video support, Canvas, Local storage, Better form controls, Improved performance and mobile support.

[⬆ Back to Top](#Interview)


## ```<strong>``` and ```<b>``` tage
- ```<strong>``` tag indicate important content
- ```<b>``` tag only for visual bold styling

## Semantic tags and Non-semantic tags
- ```Semantic tags``` are HTML tags that clearly describe the meaning of the content inside.They make code Easy to read.
Like that -> ```<header>, <nav>, <section>, <article>, <aside>, <footer>```

- ``` Non-semantic tags``` are HTML tags that do not describe the meaning of content. They are mainly used for Styling, Layout.
Like that-> ```<div>, <span>```

[⬆ Back to Top](#Interview)

## ```<div>``` and ```<span>```
- ```<div>``` is a block-level element that takes full width and starts on a new line they are used for Page-Section, Layouts, Containers.

- ```<span>``` is inline element that takes only required  width and stays in the same line they are used for Styling-Small-Text, Higlighting words.

[⬆ Back to Top](#Interview)

## inline and block elements
- ```inline elements``` take only required width and stay in the same line. like that ```<span>, <a>, <strong>```
- ```block elements``` take full width and start from a new line. like that ```<div>, <p>, <section>, <h1>```

[⬆ Back to Top](#Interview)

## ```<meta>```
- ```<meta>``` The meta tag provides metadata about the webpage, such as character encoding, responsive settings, description, and keywords. It is placed inside the head tag. 

## CSS styling in HTML
CSS styling in three ways:->
**1. Inline CSS** Apply styles directly to an element using the style attribute.
**2. Internal CSS** Place CSS inside a ```<style>``` tag within the ```<head>``` section.
**3. External CSS** Link an external .css file using the ```<link>``` tag.

```html

// Inline CSS : 
<p style="color: blue; font-size: 16px;">Hello!</p>

// Internal CSS : 
<head>
  <style>
    p { color: blue; font-size: 16px; }
  </style>
</head>

// External CSS
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

## ```<section>```, ```<article>```, ```<div>```
- ```<section>``` Used to divide webpage into different sections.
  - Example: About section, Contact section, Services section 
- ```<article>``` Used for independent content that can stand alone.
  - Example: Blog post, News article
- ```<div>``` General-purpose container.
  - Example: Styling, Layout 
