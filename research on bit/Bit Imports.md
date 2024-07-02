
### How imports are resolved

assuming we created one components using bit
@cw-kailas.learning/button

assuming we created two versions for same
1. 0.0.1
2. 0.0.2

### how to consume specific version?

command to import specific version of button
```
bit import "cw-kailas.learning/button@0.0.2"
```

Note:
You have to understand bit cli only has single reference when resolving components independent of the version

Meaning we cannot use different version in same application since bit will just override previous version 