```
// _oxygen-theme.scss
$CURSOR: (
    'pointer': pointer,
    'not-allowed': not-allowed,
);


// cursor.scss
@each $name, $value in $CURSOR {
    .cursor-#{$name} {
        cursor: $value;
    }
}

----- code generated ------
.cursor-pointer {
	cursor: pointer;
}

.cursor-not-allowed {
	cursor: not-allowed
}

```


sample token:
```
const token = `
	cursor-pointer
	cursor-not-allowed
`
```


Process of generating valid css from sample token:
1) break docstring token into single subtoken
	- cursor-pointer
	- cursor-not-allowed
2) after code generation phase we have generate list of property names which will always be valid since we generated these properties from list

## how do you reverse process of tokenization to generate valid css?

### Method 1 (build a hashmap of all properties) with respect to child->parent relation

```
hmap = {
	"cursor-pointer": "cursor",
	"cursor-not-allowed": "cursor"
}
``` 

