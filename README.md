# Form Inputs

## Steps

1. **Start with a form**
```html
<form></form>
```
2. Add a `name` attribute. Important because we are gonna access in the future to elements to get the value.
```diff
+ <form name="login"></form>
```
3. Write both inputs, the _username_ and _password_.
```html
<input type="text" name="username" placeholder="Username" />
<input type="text" name="password" placeholder="Password" />
```

_Show the result_, and tell them that you are adding a `div` because you want the _input elements_ with a block style.

4. Add `div` to separate _input elements_.
```diff
+ <div>
    <input type="text" name="username" placeholder="Username" />
+ </div>

+ <div>
    <input type="text" name="password" placeholder="Password" />
+ </div>
```

5. Now, add the `select` element.
```html
<select name="userType"></select>
```

6. Add options to show in the list.
```diff
<select name="userType">
+  <option value="admin">Admin</option>
+  <option value="guest">Guest</option>
</select>
```

7. Put the `select` inside a `div` to display in block visual way.
```diff
+ <div>
    <select name="userType">
      <option value="admin">Admin</option>
      <option value="guest">Guest</option>
    </select>
+ </div>
```

8. Add a _submit_ button to the form. Add it to the final.
```html
<button type="submit">Log in</button>
```

**Show the complete form.**


### Second Part, JavaScript

**Announce that you’ll write JavaScript to code the event and access the value from input elements.**

1. Save the form in a variable.
```js
const form = document.forms.login
```

2. Add the event listener.
```js
form.addEventListener("submit", function() {})
```

3. Cancel the submit event.
```diff
+ form.addEventListener("submit", function(e) {
+   e.preventDefault()
})
```

4. Create two variables to save **username** and **password**.
```js
let username
let password
```

5. Assign value from input to each variable.
```js
username = form.elements.username.value
password = form.elements.password.value
```

**Test the values in the console**

6. Get the value from `select` element.
```js
let userType = form.elements.userType
```

7. Obtain the value from any `option`.
```js
userType.options[userType.selectedIndex].textContent
```

### Third part

**Add the validation code to verify if inputs are empty.**

1. Start with the `if`
```js
if () {}
```

2. Check if `username` input is empty.
```diff
+ if (username === "") {
+   alert("It’s empty! Not allowed.")
+ }
```

3. Create a `div` to save errors.
```js
<div class='errors'></div>
```

4. Now, change the alert and show a message error in the HTML.
```diff
if (username === "") {
+ document.querySelector(".errors").textContent = "Please, provide a username. This field can not be empty."
}
```

**Test the code.**

5. Add better styles to display the message error.
```css
.errors {
  color: red;
  font-family: sans-serif;
  font-size: 11px;
  font-weight: bold;
  text-transform: uppercase;
}
```

**Test again the code.**

6. Add a second validation for _password input_.
```diff
if (username === "") {
  document.querySelector(".errors").textContent = "Please, provide a username. This field can not be empty."
+ } else if (password === "") {
+   document.querySelector(".errors").textContent = "Please, provide a password. This field can not be empty."
+ }
```

**Test the form, again.**

7. Add an alert to show that the form was "sent".
```js
alert("All information was sent.")
```

**Test the form, again.**
**See how the information was sent but the form it’s dirty. Clean the inputs.**

8. Clean the inputs.
```diff
+ else {
+   document.querySelector('#errors').textContent = ''
+   form.elements.username.value = ''
+   form.elements.password.value = ''
+   alert("Your report has been sent! Check you email.")
+ }
```

# Second Example

## Show an extra div if the user selected is "Admin"

**Use the same code, but in another pen.*

1. In the HTML, add a new section that contains a label and a new input.
```html
<div>
  <label for="">CODE:</label>
  <input type="text" placeholder="Enter your secret code" />  
</div>
```

2. Add a class to the new div. We’ll use it to control the display.
```diff
+ <div class="onlyAdmin">
  <label for="">CODE:</label>
  <input type="text" placeholder="Enter your secret code" />  
</div>
```

3. Hide by default that container.
```css
.onlyAdmin {
  display: none;
}
```

4. Now, create a class that help us to show the container.
```css
.onlyAdmin.show {
  display: block;
}
```

**Test manually the class.**

#### Obtain the option selected from `select` element.

1. Save in a variable the `select` element. This should be outside callback function from `form` event listener.
```js
const userType = document.querySelector("select")
```

2. Add an event to listen when the select change.
```js
userType.addEventListener("change", function() {})
```

**Test with a `console.log` to see what it’s happening.**

```diff
userType.addEventListener("change", function() {
+ console.log("it’s changing...")
})
```

**Test in the browser**

3. Get the content from the selected option.
```js
const selected = userType.options[userType.selectedIndex].textContent;
```

4. Ask if option is equal to "Admin"
```js
if (selected === "Admin") {}
```

5. Show the box if the condition is true.
```diff
if (selected === "Admin") {
+ document.querySelector(".onlyAdmin").classList.add("show")
}
```

**Test the box, select Admin and see what happend. Now select Guest. Fix the error. **

6. Hide the box if the option selected is "Guest"
```diff
+ else {
+ document.querySelector(".onlyAdmin").classList.remove("show")
}
```
