# Password-show-and-hide-with-vanilla-js
Hiding passwords visibility in forms helps protect from people looking over your shoulder and reading your password, but greatly increases in the likelihood that someone will enter the wrong one. Today, I want to show you how to implement a simple show/hide password toggle with vanilla JavaScript

# The Form  
Here’s a simple form with a username and password. I’ve also added a checkbox users can click to reveal or hide their password.
``` html
<label for="username">Username</label>
<input type="text" name="username" id="username">

<label for="password">Password</label>
<input type="password" name="password" id="password">

<label for="show_password">
	<input type="checkbox" name="show_password" id="show_password">
	Show Password
</label>
```
# The JavaScript
Listening for changes
We’ll use addEventListener to listen for click events on our show_password input. This will also detect changes submitted with a keyboard (as in, tabbing onto the checkbox and hitting the enter key).

We’ll listen for all clicks on the document, and check to see if the clicked element was our show_password checkbox—a technique called event delegation.

Whenever a click event happens, we’ll check to see if it has an ID of show_password. If not, we’ll bail.

``` js
<script>
      // Listen for click events
document.addEventListener('click', function (event) {

	// If the clicked element isn't our show password checkbox, bail
	if (event.target.id !== 'show_password') return;

	// Get the password field
	var password = document.querySelector('#password');
	if (!password) return;

	// Check if the password should be shown or hidden
	if (event.target.checked) {
		// Show the password
		password.type = 'text';
	} else {
		// Hide the password
		password.type = 'password';
	}

}, false);
    </script>
```       

# WORKING DEMO
[ LIVE (https://codexpress.w3spaces.com/password-show-hide-demo.html)]
