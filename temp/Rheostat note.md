
conversion to functional component
```js

it('should fire onSliderDragStart event', function() {
    const component = mount(
        <Rheostat
            min={BUDGET_FILTER_OBJ.min}
            max={BUDGET_FILTER_OBJ.max}
            values={[BUDGET_FILTER_OBJ.min]}
            snapPoints={BUDGET_FILTER_OBJ.snapPoints}
            onSliderDragStart={mockFn}
        />
    );

    act(() => {
        component.setProps({ value: [BUDGET_FILTER_OBJ.max] });
        component.instance().startSlide();
        component.instance().getNextState();
    });
    expect(mockFn).toHaveBeenCalled();
});

```

after component is mounted... currently its a class based component so we can directly use component.setProps but for functional we cannot

testcases:
1. need to figure out a way to convert state level testcases 
---
#react-native 