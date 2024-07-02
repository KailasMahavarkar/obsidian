
Observation:
1) materialUI
materialUI is using forwardRef to pass data from parent to child this allows them to focus into child element from parent element itself, in my observation i did not find any reference of useState in input component

reference: [input in material ui](https://github.com/mui/material-ui/blob/master/packages/mui-material/src/Input/Input.js)

```js

const Input = React.forwardRef(function Input(inProps, ref) {
  return (
    <InputBase
      ref={ref}
      {...other}
    />
  );
});

// note: This is skeletion version of same component its an abstract overview
```

2) chakraUI

```js

export const Input = forwardRef<InputProps, "input">(function Input(
  props,
  ref,
) {
  const { htmlSize, ...rest } = props
  const styles = useMultiStyleConfig("Input", rest)
  const ownProps = omitThemingProps(rest)
  const input = useFormControl<HTMLInputElement>(ownProps)

  return (
    <chakra.input
      {...input}
      ref={ref}
    />
  )
})

// note: This is skeletion version of same component its an abstract overview

```

reference: [charka input](https://github.com/chakra-ui/chakra-ui/blob/main/packages/components/input/src/input.tsx)


3) React Bootstrap

```js

const FormText: BsPrefixRefForwardingComponent<'small', FormTextProps> =
  React.forwardRef<HTMLElement, FormTextProps>(({ ...props },ref) => {
      bsPrefix = useBootstrapPrefix(bsPrefix, 'form-text');

      return (
        <Component
          {...props}
          ref={ref}
          className={classNames(className, bsPrefix, muted && 'text-muted')}
        />
      );
    },
  );
```

reference: [react bootstrap input](https://github.com/react-bootstrap/react-bootstrap/blob/master/src/FormText.tsx)

4) Ant Design

```js
const Password = React.forwardRef<InputRef, PasswordProps>((props, ref) => {
  const inputRef = useRef<InputRef>(null);
  // some omitted code in between
  return <Input ref={ref} {...props} />;
});
```


Conclusion:
reference is the way others are handling input component same pattern can be observed in grommet UI and others

### reference: [ant design password input](https://github.com/ant-design/ant-design/blob/master/components/input/Password.tsx)