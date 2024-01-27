# React + TypeScript + Vite

### Setting up test setup

- jest
  test runner

- @testing-library/react
  utilities for react component testing

- ts-jest 
  helps jest understand tests in ts file

- @types/jest
  is a package that provides TypeScript type definitions for Jest.

- @testing-library/jest-dom
   provides matchers for assertion on  DOM in ts files, with react testing library

- jest-environment-jsdom
  DOM simulation based on jsdom for jest

- ts-node
  run ts files without compiling to js

- identity-obj-proxy
  mock css and image imports in jest

- npm install jest  ts-node identity-obj-proxy @testing-library/react @testing-library/jest-dom jest-environment-jsdom ts-jest @types/jest --save-dev



### Configuring Jest Config

   ```
     export default {
      preset: "test-jest",
      testEnvironment: "jest-environment-jsdom",
      transform: {
        "^.+\\.tsx?$": "ts-jest",
      },
      moduleNameMapper: {
        "\\.(gif|ttf|eot|svg|png)$": "<rootDir>/src/__test__/__mocks__/fileMock.js",
        "\\.(css)$": "identity-obj-proxy",
      },
    }
   ```
  Jest config includes vital configs, most of them are self explainatory
    
### Adding mock file defined in moduleNameMapper
    
  ```
   // src/__test__/__mocks__/fileMock.js 
    create the folder structure and add the following code, this help us mock images.

   // eslint-disable-next-line no-undef
    module.exports = {
      __esModule: true,
      default: "test-file-stub",
    };
  ```

  ### Adding a sample test
  ```
    // src/__test__/App.test.tsx
    
    import '@testing-library/jest-dom'
    import { render } from "@testing-library/react"
    import App from "../App"

    test('demo', () => {
      expect(true).toBe(true)
    })

    test("Renders the main page", () => {
     render(<App />)
     expect(true).toBeTruthy()
    });
  ```
    
  ### Add run script in package.json
  ```
    // package.json

    "scripts" {
      ...,
      "test": "jest"
    }
  ```
  If everything is inplace running the test will make it pass, now you have a working test setup, which can be extended for complex automation tests.