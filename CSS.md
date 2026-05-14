# Interview

| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 |
|----------|----------|----------|----------|----------|
|[CSS3](#css3)|[Selector](#selector)|[Box Model](#box-model)|
|[Pseudo-Class, Pseudo-Elements](#pseudo-class-pseudo-elements)|[`!important`](#important)|[Opacity](#opacity)|
|[z-index](#z-index)|[gird and flex-box](#gird-and-flex-box)|
|[Adaptive and Responsive design](#adaptive-design-and-responsive-design)|
## CSS3
- CSS3 is the advanced version of CSS that provides modern styling features like
  - Border Radius
  - Box Shadow
  - Animation -> Used for movement and effects.
  - Transition -> Creates smooth effects.
  - Media Query
  - Flexbox
  - Grid
  - Supports responsive design @medic query 

## Selector
A CSS selector is used to target HTML elements and apply styles.

type of selector:
| Selector           | Example  | Purpose                     |
| ------------------ | -------- | --------------------------- |
| **Universal Selector** | `*{}`      | Selects all elements        |
| **Element Selector**   | `p{}`      | Selects HTML tags           |
| **Class Selector**     | `.box{}`   | Selects elements with class |
| **ID Selector**        | `#title{}` | Selects element with id     |
| **Group Selector**     | `h1, p{}`  | Selects multiple elements   |
| **Descendant Selector**|  `div p`   | Selects nested elements     |
| **Child Selector**     |  `div>p`   | Selects direct child        |
| **Attribute Selector** |`input[type="text"]`|Selects by attribute |

## Box Model
Box Model describes how every HTML element is represented.
1. Content
2. Padding
3. Border
4. Margin

## Pseudo-Class, Pseudo-Elements
- `Pseudo-Class` define a special state of an element. like `:hover`,`:focus`
- `Pseudo-Elements` style a specific part of an element. like `::before`, `::after`

## `!important`
- !important is used to give a CSS property the highest priority and override other styles.

## Opacity
- Opacity is used to control the transparency level of an HTML element.

## z-index
- Z-index controls which overlapping element appears in front or behind.
- z-index works only with positioned elements: `position: relative`

## grid and flex-box
- Grid is used for two-dimensional layouts with rows and columns.
- Flexbox is used for one-dimensional layouts row and columns.

## Adaptive and Responsive design 
- `Adaptive design` 
  - Multiple Fixed layout designed for specific screen sizes.
  - Requires creating and maintaining multiple versions of the design.
- `Responsive design`
  - Single fluid layout that adjusts dynamically using css media queries.
  - Easier to maintain, as it uses one codebase for all devices.
