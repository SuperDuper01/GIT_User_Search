# GitHub Account Finder App

This application allows users to search for GitHub accounts by entering a username or email. It utilizes the GitHub API to fetch user data based on the search query and displays the results in a user-friendly manner.

## Technologies Used:

- React
- JavaScript 
- GitHub API 

## Getting Started:

1. Clone the repository:
   ```bash
   git clone [repository-url]
   ```

2. Navigate to the project directory:
   ```bash
   cd [project-directory]
   ```

3. Install the required dependencies:
   ```bash
   npm install
   ```

4. Run the code:
   ```bash
   npm start
   ```

## Functionality Overview:

### State Management:

- `useState` is utilized to manage state variables for storing user input (`inputValue`) and API results (`results`).

### API Interaction:

- The application interacts with the GitHub API to search for user accounts based on the entered query.
- The API link used in this code: 
```bash 
https://api.github.com/search/users?q={query} 
```
### Fetching Data From The API
- The code used to fetch data from the API in javascript is :
```javascript
  const API_URL = "https://api.github.com";

  async function findGithubAccounts(query) {
    try {
      const response = await fetch(`${API_URL}/search/users?q=${query}`);
      const json = await response.json();
      return json.items || [];
    } catch (e) {
      throw new Error(e);
    }
  }
```
- The ```javascript 
`${query}`
``` is where we place the user name which is to be searched and send that request to the GIT API.
### Components:

#### `App.js`:

- The main application component that includes a search form and displays search results using the `UserCard` component.

#### `UserCard` Component:

- **Description**: A reusable component to display user details fetched from the GitHub API.
- **Attributes Used From The Data Received**:
  - `profileLink`: URL of the user's profile picture.
  - `accountLink`: URL of the user's GitHub account.
  - `username`: GitHub username of the user.
- **Usage**: Renders a user card with an image, username, and a link to the user's GitHub account.

```javascript
import './user-card.css'

export default function UserCard(props) {
    return (
        <div className="user">
            <img 
                src={props.profileLink} 
                alt="Profile" 
                width="50" 
                height="50" 
            />
            <a 
                href={props.accountLink} 
                target="_blank"
            > {props.username} </a>
            hi from user card ...
        </div>
    )
}
```

#### `index.js`:

- **Description**: The entry point of the React application where the root component (`App`) is rendered within a `StrictMode` wrapper to detect potential problems in an application.
- **Libraries/Modules**:
  - `ReactDOM`: Used to render React components into the DOM.

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App/>
  </React.StrictMode>
);

reportWebVitals();
```

## Usage:

1. Enter a username or email in the search input field.
2. Click the "Search" button to fetch and display GitHub accounts matching the entered query.
3. View the results displayed below the search form, where each user card provides a profile link, account link, and username.

## Contributions:

Contributions are welcome! Please feel free to submit a pull request or raise an issue if you encounter any bugs or have suggestions for improvements
