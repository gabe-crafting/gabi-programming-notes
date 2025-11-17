---
links: []
navigation:
  icon: i-bxl-css3
---

# Cheetsheet

::card-group{.w-full}
  :::card
  ## Flex
  
  - **1D:** Aligning items in a single direction (horizontal or vertical)
  - Automatic spacing (gap)
  - Flexible resizing across one axis
  - **uses:** Navigation bars, Center content

  ### Parent (container)
  ```css
  display: flex;           /* enable flexbox */
  flex-direction: row;     /* row | row-reverse | column | column-reverse */
  flex-wrap: wrap;         /* wrap content */
  justify-content: center; /* horizontal alignment */
  align-items: center;     /* vertical alignment */
  gap: 10px;               /* spacing */
  ```

  ### Children (items)
  ```css
  flex-grow: 1;  /* item expands to fill space */
  flex-shrink: 0; /* prevent shrinking */
  flex-basis: 200px; /* initial width */
  align-self: flex-start; /* override alignment */
  order: 2; /* change item order */
  ```
  :::

  :::card
  ## GRID
  
  - Full page layouts, Dashboards, card layouts
  - Complex two-dimensional designs
  - Defining **explicit** rows + columns
  - Overlapping elements
  - True responsive layout systems
  ### Parent (container)
  ```css
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
  grid-template-rows: auto 200px;
  gap: 20px;

  /* Responsive magic */
  grid-auto-rows: minmax(100px, auto);
  grid-auto-flow: dense; /* pack items tightly */
  ```
  ### Children (items)
  ```css
  grid-column: 1 / 3; /* spans column 1 to 2 */
  grid-row: 2 / 4;    /* spans row 2 to 3 */
  grid-area: 2 / 1 / 4 / 3; /* row-start / col-start / row-end / col-end */
  ```
  :::
::
