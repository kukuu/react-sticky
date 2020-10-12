# react-sticky

A Sticky header/footer component for React

The main component's src file is in `src/Sticky.jsx`

To use it, use a `<Sticky>` component and pass the sticky header/footer/sidebar's contents as children.




## Usage

### `<Sticky sides={{ top?, bottom?, left?, right? }} scrollTarget={elementRef?} >{children}</Sticky>`

```jsx
import React, {Component} from 'react';
import Sticky from './Sticky.jsx';
import classnames from 'classnames';

const sides = {
  top: 0, // Sticks when it scrolls past the top edge
  bottom: 0, // Sticks when it scrolls past the bottom edge
  left: 10, // Sticks 10px from the left edge
  right: -20, // Sticks 20px past the right edge (useful for content that should stick only when it's fully out of the frame)
};

function MyComponent() {
  return (
    <div>
      <div>Lorem ipsum...</div>
      {/** Without a scrollTarget, Sticky will watch the window for scroll events. */}
      <Sticky sides={sides}>
        {/** Content will be called with an additional "modifiers" prop */}
        <Content />
      </Sticky>
      <div>Lorem ipsum...</div>
    </div>
  );
};

```

#### Properties

- `props.children`

  Must be one or more React node. Each child will get an extra prop called `modifiers` when the `<Sticky />` component is scrolled within a set distance from the edge of the scroll area.

  The `modifiers` prop is an array of one or more of these strings: `'stuck-top'`, `'stuck-bottom'`, `'stuck-left'`, `'stuck-right'`

- `props.sides`

  An object in the form

  ```js
  sides = {
    top: 1,
    bottom: 2,
    left: 3,
    right: 4,
  };
  ```

  `sides` controls how far the `<Sticky />` component should be from each edge of the scroll area before it receives the corresponding modifier string.

- `props.scrollTarget`

  By default, `<Sticky />` watches for scroll events on the window, and measures side offsets from the window's edge.
  
  If you want to stick something to the edge of an internally scrolling DOM element (a `<div/>` that uses `overflow: scroll` or `overflow: auto`, for instance), you can optionally pass a React ref to your scrolling area. Then `<Sticky />` will watch that element and measure side offsets from it.

## Disclaimer

I'm providing this code free under an open source license. This is my personal repository, and the code is provided by me, not my employer.
