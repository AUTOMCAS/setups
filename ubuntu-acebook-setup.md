## Quick use

### MongoDB
Start MongoDB in single terminal:
```
; sudo systemctl start mongod
```
To stop MongoDB:
```
; sudo systemctl stop mongod
```
### Start backend and frontend in a terminals
```
; cd api
; JWT_SECRET=SUPER_SECRET npm start
```
```
; cd frontend
; npm start
```
### Testing
#### The Backend (API)
Start the server in test mode (so that it connects to the test DB)
```
; cd api
; JWT_SECRET=SUPER_SECRET npm run start:test
```

Then run the tests in a new terminal session

```
; cd api
; JWT_SECRET=SUPER_SECRET npm run test
```

#### The frontend (React)

 Start the server in test mode (so that it connects to the test DB)

  ```
  ; cd api
  ; JWT_SECRET=SUPER_SECRET npm run start:test
  ```

  Then start the front end in a new terminal session

  ```
  ; cd frontend
  ; JWT_SECRET=SUPER_SECRET npm start
  ```

  Then run the tests in a new terminal session

  ```
  ; cd frontend
  ; JWT_SECRET=SUPER_SECRET npm run test
  ```



## Ubuntu acebook project set up

1. Fork this repository
2. Rename your fork to `acebook-<team name>`
3. Clone your fork to your local machine
4. Install Node.js dependencies for both FE and BE (API)
   ```
   ; cd api
   ; npm install
   ; cd ../frontend
   ; npm install
   ```
5. Install an ESLint plugin for your editor. For example: [linter-eslint](https://github.com/AtomLinter/linter-eslint) for Atom.
6. Install MongoDB version 4.4 for Ubuntu [here](https://www.mongodb.com/docs/v4.4/tutorial/install-mongodb-on-ubuntu/). Versions above 4.4 give errors that I could not solve.
7. open `frontend/package.json` and ensure build/start to tare as the below:
    ```bash
    scripts": {
    "build": "react-scripts build",
    "start": "react-scripts start",
    ```

8. Start MongoDB  
   ```
   sudo systemctl start mongod
   ```
     Verify MongoDB is running
  
    ```  
    sudo systemctl status mongod
    ```
      To stop MongoDB

    ```  
    sudo systemctl stop mongod
    ```
