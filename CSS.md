# Interview

| Column 1 | Column 2 | Column 3 | Column 4 | Column 5 |
|----------|----------|----------|----------|----------|
|[CSS3](#css3)|[Selector](#selector)|[Box Model](#box-model)|
|[Pseudo-Class, Pseudo-Elements](#pseudo-class-pseudo-elements)|[`!important`](#important)|[Opacity](#opacity)|
|[z-index](#z-index)|[gird and flex-box](#grid-and-flex-box)|[positin property](#positin-property)|
|[Adaptive and Responsive design](#adaptive-and-responsive-design)|[`vh` and `vw`](#vh-and-vw)|
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

[⬆ Back to Top](#Interview)

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

[⬆ Back to Top](#Interview)

## Box Model
Box Model describes how every HTML element is represented.
1. Content
2. Padding
3. Border
4. Margin

[⬆ Back to Top](#Interview)

## Pseudo-Class, Pseudo-Elements
- `Pseudo-Class` define a special state of an element. like `:hover`,`:focus`
- `Pseudo-Elements` style a specific part of an element. like `::before`, `::after`

[⬆ Back to Top](#Interview)

## `!important`
- !important is used to give a CSS property the highest priority and override other styles.

[⬆ Back to Top](#Interview)

## Opacity
- Opacity is used to control the transparency level of an HTML element.

[⬆ Back to Top](#Interview)

## z-index
- Z-index controls which overlapping element appears in front or behind.
- z-index works only with positioned elements: `position: relative`

[⬆ Back to Top](#Interview)

## grid and flex-box
- Grid is used for two-dimensional layouts with rows and columns.
- Flexbox is used for one-dimensional layouts row and columns.

[⬆ Back to Top](#Interview)

## Adaptive and Responsive design 
- `Adaptive design` 
  - Multiple Fixed layout designed for specific screen sizes.
  - Requires creating and maintaining multiple versions of the design.
- `Responsive design`
  - Single fluid layout that adjusts dynamically using css media queries.
  - Easier to maintain, as it uses one codebase for all devices.

[⬆ Back to Top](#Interview)

## `vh` and `vw`
- `vh` Viewport Height 1VH=10px
- `vw` Viewport Width 1VW=10px

[⬆ Back to Top](#Interview)

## positin property
`static`
  - follow the normal document flow.

`relative`
  - Relative position to it-self. It is nomal position using top, down,right, left.     

`absolute`
  - Absolute position is actually set relative to the elements parent. If no parent is available then the relative place to the page it-self.

`fixed`
  - Positioned relative to the viewport does not move on scroll.

`sticky`
  - Sticky positioning behaves like relative initially and becomes fixed when scrolling.

[⬆ Back to Top](#Interview)
