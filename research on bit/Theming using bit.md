Reference blog:
https://bit.dev/blog/theming-react-apps-with-styled-components-and-bit-l7epurug/

Takeaway
1) basically theme is manage in same way like any other components in bit.dev meaning just create node language component and export base composition

Example export for space:
```js
export function Spaces() {
    return (
        <div>
            Spaces:{'  '}
            {[10, 20, 30].map((space, index) => (
                <span style={{ marginRight: space }} key={index}>
                    {space}px
                </span>
            ))}
        </div>
    );
}
```


consumption in application:

```js
import React from 'react';
import { ThemeProvider } from 'styled-components';
import { baseTheme } from '@nitsan770/styled-components.themes.base-theme';

export const StyledComponentsThemeProvider = ({ children }) => (
  <ThemeProvider theme={baseTheme}>{children}</ThemeProvider>
);
```

How would you consume in components?
> we need to write a HOC such that it will become easy for importing above created composition


----
#bit