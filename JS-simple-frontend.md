
# Setting up a minimal frontend web app
[Makers link](https://github.com/makersacademy/javascript-web-applications/blob/main/pills/setup_minimal_frontend_webapp.md#4-add-the-build-script-to-packagejson)

npm - Software registry to share and borrow packages.

## Quick setup

1. Ensure global parts are installed (see below)
2. Create project directory
3. Initialise git: `git init`
4. Create package.json file without questions: `npm init -y`
5. Install jest: `npm install jest-environment-jsdom`
6. Add build script to package.json, under `test`: `,"build": "esbuild index.js --bundle  --outfile=bundle.js --watch"`
8. Create `index.html` and `index.js`
9. add `<script src="bundle.js"></script>` to `index.html` body
10. Run jest fetch mock install: `npm install --save jest-fetch-mock`
11. Run builder: `npm run build`

**If using existing directory:**  
Install dependencies: `npm install`

## Testing

fs allows CRUD of non-JS files within jest
Top of test file:
```js
/**
 * @jest-environment jsdom
 */

const fs = require('fs');

 ```
Start of each test: 
```js
document.body.innerHTML = fs.readFileSync('./index.html');
```


### Mocking fetch:

```js
require('jest-fetch-mock').enableMocks()

describe('Client class', () => {
    beforeEach(() => {
    fetch.resetMocks();
  });

  it('calls fetch and loads data', (done) => {
    const client = new Client();
    fetch.mockResponseOnce(JSON.stringify({
      name: "Some value",
      id: 123
    }));

    client.loadData((returnedDataFromApi) => {
      expect(returnedDataFromApi.name).toBe("Some value");
      expect(returnedDataFromApi.id).toBe(123);
      done();
    });
  });
});
```

```js
expect(fetch).toHaveBeenCalledTimes(1)
expect(fetch).toHaveBeenCalledWith('url')
```
## From scratch

```bash
nvm use node
npm install -g jest esbuild
```
from within project directory:
```bash
npm init -y
npm install jest-environment-jsdom
```


## Build tool - [esbuild](https://esbuild.github.io/getting-started/)   

Install (globally) using npm:
```bash
$ npm install -g esbuild
```

Run:
```bash
npm run build
```
**Troubleshooting**  
`missing script: build` - make sure  `package.json`  is configured (below)


## Configuring `package.json` 

In package.json add:
```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    // add this line:
    "build": "esbuild index.js --bundle  --outfile=bundle.js --watch"
```
This executes the command when we run `npm run build`
The path for index.js may need to change depending on directory structure


## Project structure

```bash
- my_todo_list_project
  - src/
    - views/
      - todoView.js
      - todoView.test.js
    - models/
      - todoModel.js
      - todoModel.test.js
    - index.js
  - index.html
  - package.json
  - (other files...)
  ```

  In case you have any other (non JavaScript) resources, such as CSS files, images, etc, they can probably be put into a different directory (usually called assets, static or resources, or something similar).