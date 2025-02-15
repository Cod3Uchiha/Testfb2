**index.html**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Firebase Login Page</title>
    <link rel="stylesheet" href="style.css" />
  </head>

  <body>
    <div class="container">
      <h1>Firebase Login</h1>
      <form id="login-form">
        <label for="email">Email:</label>
        <input type="email" name="email" id="email" required />

        <label for="password">Password:</label>
        <input type="password" name="password" id="password" required />

        <button type="submit">Log In</button>
      </form>
    </div>

    <script src="script.js"></script>
  </body>
</html>
```

**style.css**

```css
body {
  font-family: Arial, sans-serif;
}

.container {
  width: 300px;
  margin: 0 auto;
}

form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

label {
  margin-bottom: 5px;
}

input {
  width: 250px;
  padding: 5px;
}

button {
  background-color: #008CBA;
  color: white;
  padding: 5px 10px;
  border: none;
  cursor: pointer;
}
```

**script.js**

```javascript
const loginForm = document.getElementById("login-form");

loginForm.addEventListener("submit", (e) => {
  e.preventDefault();

  const email = document.getElementById("email").value;
  const password = document.getElementById("password").value;

  // Add your Firebase login code here
  firebase
    .auth()
    .signInWithEmailAndPassword(email, password)
    .then(() => {
      // Redirect to the home page
      window.location.href = "home.html";
    })
    .catch((error) => {
      // Handle the error
      alert(error.message);
    });
});
```

**Documentation**

To use this login page, you will need to include the following Firebase SDK in your HTML:

```html
<script src="https://www.gstatic.com/firebasejs/ui/4.6.1/firebase-ui-auth.js"></script>
```

You will also need to initialize Firebase with your project's configuration. Replace the values in the following code with your own:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID",
};

firebase.initializeApp(firebaseConfig);
```

**Implementation Details**

1. The `index.html` file contains the HTML structure of the login page.
2. The `style.css` file contains the CSS styles for the login page.
3. The `script.js` file contains the JavaScript code for the login page.
4. The `initializeFirebase()` function initializes Firebase with the project's configuration.
5. The `loginForm` variable references the login form element in the DOM.
6. The `loginForm.addEventListener()` method listens for the `submit` event on the login form.
7. When the `submit` event is triggered, the `e.preventDefault()` method prevents the form from submitting and reloading the page.
8. The `email` and `password` variables retrieve the values from the email and password input fields, respectively.
9. The `firebase.auth().signInWithEmailAndPassword()` method attempts to sign in the user with the specified email and password.
10. If the sign-in is successful, the `then()` method redirects the user to the `home.html` page.
11. If the sign-in fails, the `catch()` method displays an error message to the user.