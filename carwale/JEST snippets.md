
```
// mock the useTest hook
const reference = jest.mock('react', () => ({
    ...jest.requireActual('react'),
    useState: jest.fn(),
}));
```