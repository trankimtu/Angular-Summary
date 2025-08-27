# VS Code Package
Auto Import

# Node Package Manager
```
sudo apt install npm
```

# Node js
https://nodejs.org/en/download/

# Install Typescript
```
npm install -g typescript
```

# Angular CLI
```
npm install -g @angular/cli
```

# Check version
```
ng version
ng --version
npm --version / npm -v / npm -version
tsc -v / tsc --version
```

# Update
Only update that project, not global
```
ng update @angular/cli
```

# Install all package from exist project
```
npm install
```

# Run
```
Node <file.js>
tsc.ts | node main.js
ng serve

```

# Create new project
```
ng new <Project Name> // --dry-run no changes were made
```
# Create project npm error - No matching version found for ...
```
  npm cache clean --force
```
# Create new module
Inside app folder
```
ng g m <Module Name>
```
# Create new component
```
ng g c <Component Name>
```

# Create new service
```
ng g s <Service Name>
```

# Create new pipe 
```
ng g p <pipe-name>
```

# Create new directive
```
ng g d <directive name>
```

# Create new interface
```
ng g i <interface name>
```
  
# Install bootstrap
```
npm install bootstrap --save 
```

src/style.css
```
@import "~bootstrap/dist/css/bootstrap.css";
```

# Install bootstrap icon
```
npm i bootstrap-icons
or
npm i bootstrap-icons --save
```
src/style.css
```
@import "~bootstrap-icons/font/bootstrap-icons.css";

```
## Bootstrap icons
https://icons.getbootstrap.com/


# Install JSON Server
```
  npm install -g json-server  
```
Create a database file in the project (right outside src folder) name <fileName.json> <br>
Make the database
{
  "todos": [
    {
      "id": 1,
      "task": "first todo",
      "complete": true
    },
    {
      "id": 1,
      "task": "first todo",
      "complete": true
    }
  ]
}

```
json-server <path of json file with fileName.json> --watch
ex: json-server db.json --watch
url: localhost:3000/todos
```

```
https://www.npmjs.com/package/json-server

JSON Server is a tool that allows you to quickly set up a mock REST API server for your web development projects. It's commonly used during the development phase of applications when the actual backend server is not yet available, or for testing purposes. JSON Server simplifies the process of creating a simple RESTful API with minimal effort.

Here's what JSON Server does:

1. **Mock RESTful API:** JSON Server allows you to define a data file (usually in JSON format) that represents your API's data. This data file can contain objects, arrays, and data relationships. JSON Server then serves this data over HTTP as if it were coming from a real API.

2. **CRUD Operations:** JSON Server supports standard CRUD (Create, Read, Update, Delete) operations for the data in your JSON file. You can send HTTP requests like GET, POST, PUT, and DELETE to interact with the data.

3. **Dynamic Data:** You can easily add, modify, or delete data in your JSON file, and JSON Server will reflect those changes in the API responses. This allows you to simulate a dynamic backend without the complexity of a real server.

4. **Filters and Sorting:** JSON Server provides query parameters for filtering and sorting data. You can request specific subsets of data, sort it, and paginate results.

5. **Routes:** You can define custom routes to simulate more complex API behavior. For example, you can create routes for searching, filtering, or aggregating data.

6. **Middleware:** JSON Server supports custom middleware, allowing you to add additional logic or authentication to your mock API.

7. **CORS Support:** JSON Server can be configured to support Cross-Origin Resource Sharing (CORS), which is important if you're developing a frontend application that communicates with the API from a different domain.

JSON Server is a valuable tool for front-end developers because it allows them to work on the client-side of an application independently of the backend development. It's a convenient way to prototype, develop, and test frontend code with a realistic data source even before the actual backend is fully developed or available.
```
