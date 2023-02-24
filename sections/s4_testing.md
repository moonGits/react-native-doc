# Testing


<img src="../images/diagram_testing.svg"/>

### Static Analysis
    React Native comes with two such tools configured out of the box: ESLint for linting and TypeScript for type checking.
- ##### Linters
  analyze code to catch common errors such as unused code and to help avoid pitfalls, to flag style guide no-nos like using tabs instead of spaces (or vice versa, depending on your configuration).
- ##### Type checking 
  ensures that the construct you’re passing to a function matches what the function was designed to accept, preventing passing a string to a counting function that expects a number, for instance.

### Unit Tests
    Unit tests cover the smallest parts of code, like individual functions or classes.(jest)
  <img src="../images/p_tests-unit.svg"/>

### Mocking
  - Mock Return Values
  - Mocking Modules
  - Mocking Partials
  - Mock Implementations

### Integration Tests
    When writing larger software systems, individual pieces of it need to interact with each other. In unit testing, if your unit depends on another one, you’ll sometimes end up mocking the dependency, replacing it with a fake one.
    In integration testing, real individual units are combined (same as in your app) and tested together to ensure that their cooperation works as expected. 
  <img src="../images/p_tests-integration.svg"/>

### Component Tests
  <img src="../images/p_tests-component.svg"/>

  - ##### For testing React components, there are two things you may want to test:
    - Interaction: to ensure the component behaves correctly when interacted with by a user (eg. when user presses a button)
    - Rendering: to ensure the component render output used by React is correct (eg. the button's appearance and placement in the UI)

  - ##### There are several libraries that can help you testing these:
    - React’s Test Renderer, developed alongside its core, provides a React renderer that can be used to render React components to pure JavaScript objects, without depending on the DOM or a native mobile environment.
    - React Native Testing Library (Snapshot Testing) builds on top of React’s test renderer and adds fireEvent and query APIs described in the next paragraph.
    <img src="../images/p_tests-snapshot.svg"/>

### End-to-End Tests
      In end-to-end (E2E) tests, you verify your app is working as expected on a device (or a simulator / emulator) from the user perspective.

  <img src="../images/p_tests-e2e.svg"/>

  - ##### E2E tests give you the highest possible confidence that part of your app is working. The tradeoffs include:
    - writing them is more time consuming compared to the other types of tests
    - they are slower to run
    - they are more prone to flakiness (flaky test 不确定性测试结果。) 
  - ##### There are several E2E testing tools available: 
    - Detox
    - Appium