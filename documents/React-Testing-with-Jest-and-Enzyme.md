# React Testing with Jest an Enzyme

Tests should be easy to maintain.  
Failing tests should be easy to diagnose.
Do test behavior, e.g. what the app should do.  
Do not test implementation, e.g. how the app works.

## Links

- [Jest Dcoumentation](https://jestjs.io/docs/en/getting-started)
- [Enzyme Documentation](https://enzymejs.github.io/enzyme/)

## Jest

Jest is a JavaScript testing framework designed to ensure correctness of any JavaScript codebase. Create React App ships with Jest, it works out of the box, config free.

## Enzyme

Enzyme is a JavaScript Testing utility for React that makes it easier to test your React Components' output. You can also manipulate, traverse, and in some ways simulate runtime given the output. It creates a virtual DOM for testing.

### Enzyme Installation

> `yarn add -D enzyme jest-enzyme @wojtekmaj/enzyme-adapter-react-17`

### Enzyme Setup

Enzyme setup can be extracted to file setupTests.js. If using Create React App setupTests.js is created by default in the srv folder.

> `import Enzyme, { shallow } from 'enzyme';`  
> `import EnzymeAdapter from '@wojtekmaj/enzyme-adapter-react-17';`  
> ` `  
> `Enzyme.configure({ adapter: new EnzymeAdapter() });`

### Remove data-test attributes for production

- Install babel plugin  
  `yarn add -D babel-plugin-react-remove-properties`

- Get full control over the configuration files  
  `yarn eject`

- Update Babel configuration .babelrc  
  ` "env": {"production": {"plugins": [ ["react-remove-properties", {"properties": ["data-test"]}]]}}`

- Crete production build  
  `yarn build`

### Check PropTypes

- Install prop-types  
  `yarn add prop-types`

- Install check-prop-types  
  `yarn add -D check-prop-types`

## Test Examples

### Helper functions

- Helper function for wrapper setup  
  `const setup = (props = {}) => { return shallow(<App {...props} />); };`

- Helper function for finding component by attribute  
  `const findByTestAttr = (wrapper, val) => { return wrapper.find(`[data-test="${val}"]`); };`

- Helper function for checking propTypes  
  `const checkProps = (component, conformingProps) => {`  
   `const propError = checkPropTypes(component.propTypes, conformingProps, 'prop', component.name); `  
   `expect(propError).toBeUndefined(); }; `

### Test component renders without error

App.js:

> `const App = (props) => {`  
> ` return (<div data-test="component-app">Hello world!</div>);`  
> `} ;`

App.test.js

> `test('renders without error', () => { const wrapper = setup(); const component = findByTestAttr(wrapper, 'component-congrats'); expect(component.length).toBe(1); });`
