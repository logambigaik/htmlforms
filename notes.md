Regular Expressions
===================
Data submitted through forms are stored as strings. Strings are a fundamental data type in computer science representing a series of characters “strung” together. As humans, we can intuitively recognize patterns within strings, and this allows us to catch errors. Try to notice what’s wrong in the following examples:

ABCDEF2GHIJKLMNOPQRSTUVWXYZ
My zip code is 9021
The ct meowed
<h1> Hello, World! </h2>
In the first example, we had the letters of the alphabet presented in order but interrupted by an out of place 2. In the second, we left off the 5th digit of a famous zip code. In the third, we omitted the “a” from the word cat. In the final example, we wrote some HTML with an <h1> opening tag but an unmatching </h2> closing tag. If you picked up on these mistakes, it’s because your brain has been trained to expect patterns in certain types of data.

Unlike humans, who can get this training passively over time, computers have to be precisely programmed to recognize patterns. To specify patterns for the computer to recognize, we use a special language called regular expressions — also known as regex or regexp. A regular expression is a sequence of characters representing a pattern. We can use that pattern to match a string, match parts of a string, confirm that data is formatted acceptably, or even replace parts of strings with different characters.

Client-side Validation: HTML
============================
The first technique we can use to validate form data is to prevent problematic inputs from being submitted in the first place. This is called client-side validation. The client is the process interacting with the 
Preview: Docs Loading link description
server
 on behalf of a user—in the case of websites, the web browser is the client. The logic for validating the form is included with the code that displays the form on the user’s device. No interaction with the 
Preview: Docs The back-end serves data to the front-end from sources like a database.
back-end
 is required to perform client-side validations.

Since form validation is so common, modern HTML provides some of these validation features built-in. For example, we can use HTML to make parts of a form required and others optional. We can also use HTML to set minimum and maximum values for an input or minimum or maximum lengths for a text input. We can even necessitate that the input match a particular pattern, specified by a regular expression.

If any of the rules laid out in the HTML form validation aren’t followed, the user will not be able to submit their form, and they’ll receive an error message explaining why. With these checks in place, the back-end is less likely to be sent incorrect data. HTML form validation will also benefit the user—the client provides the user immediate feedback, without having to wait for time-consuming communication with the back-end.

Client-side Validation: JavaScript:
====================================
Client-side validation has two main advantages. First, it’s a better experience for the user to be alerted to problematic data immediately rather than having to wait for that information to come back from the server
 and have to fill out the form again. Second, catching mistakes earlier in the process saves the application time and resources as well. But not all issues can be handled with the built-in HTML validations.

In order to truly customize validation or to perform more complex validations, we can incorporate JavaScript form validations. We can do this by either writing the JavaScript ourselves or by incorporating a JavaScript library. If we have unique requirements for usernames on our site, for example, we’ll have to provide these systems of validation ourselves.

If we’re creating a relatively simple website, it makes sense to code the form validation ourselves or use a simple vanilla JavaScript library—just-validate, for example. But most basic validation libraries will involve directly accessing or manipulating the DOM. This can get tricky when working with a framework
 that relies on a virtual DOM—like React or Vue. In those situations, it might be best to incorporate a library that works well with your specific framework. For example, the formik library is a lightweight library that simplifies validating forms in a React app.


 Back-end Validation
 =====================
No matter how complete the 
Preview: Docs Loading link description
front-end
 validation of a website or application seems, validations must also be completed on the 
Preview: Docs Loading link description
back-end
 or server-side. Front-end validations are easy to bypass—a malicious user can simply turn off JavaScript on their browser, for example. There’s also the potential for middleman attacks in which data is changed after the request is submitted by a user but before it arrives at the 
Preview: Docs Loading link description
server
. As a rule, the back-end should never trust the data it receives.

As the developer, once data is in the back-end, we have complete control over it, luckily. Back-end validation has several advantages:

It enables us to use validation code often on machines with more computing power.
It allows us to write validation code that a user can’t see—if malicious users can’t see exactly how we validate the data, it’s much more difficult for them to find ways around it.
We can validate the information against other data the front-end doesn’t have access to—for example, we can check our 
Preview: Docs Loading link description
database
 to see if a given username is already in use.
There are two main ways to validate inputs on the server-side. The first takes place while the user is still inputting data into the form on the front-end. We can make asynchronous requests to the server with pieces of their data and send feedback directly to the user before they’ve submitted. This is slower than front-end validation and can be a design challenge from a user-experience perspective.

The second is once the form has been submitted. Back-end form validation is our application’s last defense against problematic data, and it’s essential to verify the validity and safety of data before adding it to a database. This is also an opportunity to “sanitize” the data: in order for our database to be useful, it’s important that all data within it is formatted consistently. This means that while we may want to be flexible about the formatting we require from a user, we likely want to transform inputs into a strict format before entering them in the database.


Review:
======

Modern websites require a lot of information from their users and they collect a lot of this information through HTML forms.
It’s essential to validate the data submitted through forms to keep websites secure and to make sure they function correctly.
Regular expressions are sequences of characters that define patterns to look for in text. They are an important tool used in validating input.
Modern HTML comes with useful built-in methods for form validation.
Custom and complicated client-side validation can be accomplished with JavaScript.
Asynchronous requests to the server can perform back-end validations before a form has been submitted.


How a Form Works
=================
We can think of the internet as a network of computers which send and receive information. Computers need an HTTP request to know how to communicate. The HTTP request instructs the receiving computer how to handle the incoming information. More information can be found in our article about HTTP requests.

The 
<form>
 element is a great tool for collecting information, but then we need to send that information somewhere else for processing. We need to supply the <form> element with both the location of where the <form>‘s information goes and what HTTP request to make. Take a look at the sample <form> below:

<form action="/example.html" method="POST">
</form>


In the above example, we’ve created the skeleton for a <form> that will send information to example.html as a POST request:

The action attribute determines where the information is sent.
The method attribute is assigned a HTTP verb that is included in the HTTP request.
Note: HTTP verbs like POST do not need to be capitalized for the request to work, but it’s done so out of convention. In the example above we could have written method="post" and it would still work.

The <form> element can also contain child elements. For instance, it would be helpful to provide a header so that users know what this <form> is about. We could also add a paragraph to provide even more detail. Let’s see an example of this in code:

<form action="/example.html" method="POST">
  <h1>Creating a form</h1>
  <p>Looks like you want to learn how to create an HTML form. Well, the best way to learn is to play around with it.</p>
</form>


The example above doesn’t collect any user input, but we’ll do that in the next exercise. For now, let’s practice making the foundation of an HTML <form>!


Text Input
==========
If we want to create an input field in our <form>, we’ll need the help of the <input> element.

The <input> element has a type attribute which determines how it renders on the web page and what kind of data it can accept.

The first value for the type attribute we’re going to explore is "text". When we create an <input> element with type="text", it renders a text field that users can type into. Note that the default value of type is "text". It’s also important that we include a name attribute for the <input> — without the name attribute, information in the <input> won’t be sent when the <form> is submitted. We’ll explain more about submissions and the submit button in a later exercise. For now, let’s examine the following code that produces a text input field:

<form action="/example.html" method="POST">
  <input type="text" name="first-text-field">
</form>


Here’s a screen shot of how the rendered form looks like on a web page for the Chrome browser (different browsers have different default rendering). When initially loaded, it will be an empty box:

rendered empty text field from input element type='text'
After users type into the <input> element, the value of the value attribute becomes what is typed into the text field. The value of the value attribute is paired with the value of the name attribute and sent as text when the form is submitted. For instance, if a user typed in “important details” in the text field created by our <input> element:

rendered filled text field which reads 'important details' 
When the form is submitted, the text: "first-text-field=important details" is sent to /example.html because the value of the name attribute is "first-text-field" and the value of value is "important details".

We could also assign a default value for the value attribute so that users have a pre-filled text field when they first see the rendered form like so:

<form action="/example.html" method="POST">
  <input type="text" name="first-text-field" value="already pre-filled">
</form>


ANother example:
================
<body>
    <section id="overlay">
      <img src="https://content.codecademy.com/courses/web-101/unit-6/htmlcss1-img_burger-logo.svg" alt="Davie's Burgers Logo" id="logo">
      <hr>
      <form>
				<h1>Login to start creating a burger!</h1>  
	      <!--Add your code below-->
				UserName: <input type=text name="username"/value="Davie">

      </form>
</body>


Adding a Label
==============
In the previous exercise we created an <input> element but we didn’t include anything to explain what the <input> is used for. For a user to properly identify an <input> we use the appropriately named <label> element.

The <label> element has an opening and closing tag and displays text that is written between the opening and closing tags. To associate a <label> and an <input>, the <input> needs an id attribute. We then assign the for attribute of the <label> element with the value of the id attribute of <input>, like so:

<form action="/example.html" method="POST">
  <label for="meal">What do you want to eat?</label>
  <br>
  <input type="text" name="food" id="meal">
</form>

Another example:
================
<form>
	<h1>Login to start creating a burger!</h1>
    <!--Add your code below-->
	<label for='username'>Enter your username:</label>
    <input type="text" name="username" id="username">
</form>

Password Input
==============
An <input type ="password"> element will replace input text with another character like an asterisk (*) or a dot (•). The code below provides an example of how to create a password field:
<form>
  <label for="user-password">Password: </label>
  <input type="password" id="user-password" name="user-password">
</form>

Another example:
===============
<form>
	<h1>Login to start creating a burger!</h1>
    <label for="username">Username:</label>
  	<input type="text" name="username" id="username">
    <br>
    <label for="user-pw">Password:</label>
    <!--Add your code below-->
	<input type="password" id="user-pw" name="user-pw">
</form>

Number Input
============
By setting type="number" for an <input> we can restrict what users type into the input field to just numbers (and a few special characters like -, +, and .). We can also provide a step attribute which creates arrows inside the input field to increase or decrease by the value of the step attribute. Below is the code needed to render an input field for numbers:

<form>
  <label for="years"> Years of experience: </label>
  <input id="years" name="years" type="number" step="1">
</form>


Another example:
===============
 <form>
    <h1>Create a burger!</h1>
	<section class="protein">
    <label for="patty">What type of protein would you like?</label>
    <input type="text" name="patty" id="patty" value="beef">
    </section>
    <hr>

    <section class="patties">
    <label for="amount">How many patties would you like?</label>
	<!--Add your code below-->
	<input type="number" id="amount" name="amount" step="10">
    </section>
</form>

Range Input
===========
To set the minimum and maximum values of the slider we assign values to the min and max attribute of the <input>. We could also control how smooth and fluid the slider works by assigning the step attribute a value. Smaller step values will make the slider 
move more fluidly, whereas larger step values will make the slider move more noticeably. 
Take a look at the code to create a slider:

<form>
  <label for="volume"> Volume Control</label>
  <input id="volume" name="volume" type="range" min="0" max="100" step="1">
</form>

Another example:
================
<form>
        <h1>Create a burger!</h1>
				<section class="protein">
          <label for="patty">What type of protein would you like?</label>
    			<input type="text" name="patty" id="patty">
        </section>
        <hr>
        <section class="patties">
          <label for="amount">How many patties would you like?</label>
          <input type="number" name="amount" id="amount">
        </section>
        <hr>
				
        <section class="cooked">
          <label for="doneness">How do you want your patty cooked</label>
          <br>
          <span>Rare</span>
		       <!--Add your code below-->
           <input type="range" id="doneness" name="doneness" min="0" max="5" step="0.5"> 
           <span>Well-Done</span>
        </section>
</form>

Checkbox Input
===============
n a <form> we would use the <input> element and set type="checkbox". Examine the code used to create multiple checkboxes:

<form>
  <p>Choose your pizza toppings:</p>
  <label for="cheese">Extra cheese</label>
  <input id="cheese" name="topping" type="checkbox" value="cheese">
  <br>
  <label for="pepperoni">Pepperoni</label>
  <input id="pepperoni" name="topping" type="checkbox" value="pepperoni">
  <br>
  <label for="anchovy">Anchovy</label>
  <input id="anchovy" name="topping" type="checkbox" value="anchovy">
</form>


Another example:
================
<section class="toppings">
          <span>What toppings would you like?</span>
          <br>
          <!--Add your code below for the first checkbox-->
          <input type="checkbox" id="lettuce" name="topping" value="lettuce">
					<label for="lettuce">Lettuce</label>
          <!--Add your code below for the second checkbox-->
         <input type="checkbox" id="tomato" name="topping" value="tomato">
          <label for="tomato">Tomato</label>
          <!--Add your code below for the third checkbox-->
          <input type="checkbox" id="onion" name="topping" value="onion">
          <label for="onion">Onion</label>
</section>

Radio Button Input
==================
if we want to present users with multiple options and let them choose one or more of the options. However, there are cases where we want to present multiple options and only allow for one selection — like asking users if they agree or disagree with the terms and conditions. Let’s look over the code used to create radio buttons:

<form>
  <p>What is sum of 1 + 1?</p>
  <input type="radio" id="two" name="answer" value="2">
  <label for="two">2</label>
  <br>
  <input type="radio" id="eleven" name="answer" value="11">
  <label for="eleven">11</label>
</form>

Another example:
===============
        <section class="cheesy">
          <span>Would you like to add cheese?</span>
          <br>
	        <!--Add your first radio button below-->
          <input type="radio" id="yes" name="cheese" value="yes">
          <label for="yes">Yes</label>
	        <!--Add your second radio button below-->
          <input type="radio" id="no" name="cheese" value="no">
          <label for="no">No</label>
        </section>

Dropdown list
=============

An alternative solution is to use a dropdown list to allow our users to choose one option from an organized list. 
Here’s the code to create a dropdown menu:

<form>
  <label for="lunch">What's for lunch?</label>
  <select id="lunch" name="lunch">
    <option value="pizza">Pizza</option>
    <option value="curry">Curry</option>
    <option value="salad">Salad</option>
    <option value="ramen">Ramen</option>
    <option value="tacos">Tacos</option>
  </select>
</form>

Another example:
===============
<section class="bun-type">
		<label for="bun">What type of bun would you like?</label>
        <!--Add your code below-->
		<select id="bun" name="bun">
            <option value="sesame">Sesame</option>
            <option value="potato">Potato</option>
            <option value="milk">Milk</option>
        </select>
</section>

Datalist Input
==============

The <datalist> is used with an <input type="text"> element. The <input> creates a text field that users can type into and filter options from the <datalist>. Let’s go over a concrete example:

<form>
  <label for="city">Ideal city to visit?</label>
  <input type="text" list="cities" id="city" name="city">

  <datalist id="cities">
    <option value="New York City"></option>
    <option value="Tokyo"></option>
    <option value="Barcelona"></option>
    <option value="Mexico City"></option>
    <option value="Melbourne"></option>
    <option value="Other"></option>  
  </datalist>
</form>


Another example:
================
<section class="sauce-selection">
	<label for="sauce">What type of sauce would you like?</label>
    <input type="text" list="sauces" id="sauce" name="sauce">
    <!--Add your code below-->
    <datalist id="sauces">
        <option value="ketchup"></option>
        <option value="mayo"></option>
        <option value="barbequee"></option>
    </datalist>
</section>

Textarea element
================
The <textarea> element is used to create a bigger text field for users to write more text. We can add the attributes rows and cols to determine the amount of rows and columns for the <textarea>. Take a look:

<form>
  <label for="blog">New Blog Post: </label>
  <br>
  <textarea id="blog" name="blog" rows="5" cols="30">
  </textarea>
</form>


Another example:
===============
<section class="extra-info">
    <label for="extra">Anything else you want to add?</label>
    <br>
    <!--Add your code below-->
	<textarea id="extra" name="extra" rows="3" cols="40">Hello</textarea>
</section>


Submit Form
===========
To make a submit button in a <form>, we’re going to use the reliable <input> element and set the type to "submit". For instance:

<form>
  <input type="submit" value="Send">
</form>

Another example:
================
 <section class="submission">
    <!--Add your code below-->
    <input type="submit" value="Submit">  
</section>


Requiring an Input
==================

we have fields in our <form>s which are not optional, i.e. there must be information provided before we can submit it. To enforce this rule, we can add the required attribute to an <input> element.

Take for example:

<form action="/example.html" method="POST">
  <label for="allergies">Do you have any dietary restrictions?</label>
  <br>
  <input id="allergies" name="allergies" type="text" required>
  <br>
  <input type="submit" value="Submit">
</form>


This renders a text box, and if we try to submit the <form> without filling it out we get this message:
"Please fill out this field"

Another example:
================
<h1>Guess the right number!</h1>
<form action="check.html" method="GET">
       <!--Add a required attribute to the input element-->
        <label for="guess">Enter a number between 1-10:</label>
        <br>
        <input type="number" name="guess" id="guess" required>
        <br>
        <input type="submit" id="submission" value="Submit">
</form>


Set a Minimum and Maximum
============================
Another built-in validation we can use is to assign a minimum or maximum value for a number field, e.g. <input type="number"> and <input type="range">. To set a minimum acceptable value, we use the min attribute and assign a value. On the flip side, to set a maximum acceptable value, we assign the max attribute a value. Let’s see this in code:

<form action="/example.html" method="POST">
  <label for="guests">Enter # of guests:</label>
  <input id="guests" name="guests" type="number" min="1" max="4">
  <input type="submit" value="Submit">
</form>

If you enter greater than 4 ====> Error msg ==>Value must be less than or equal to 4 
If you enter 0 ====> Error msg ==>Value must be greater than or equal to 0


Checking Text Length
=====================
To set a minimum number of characters for a text field, we add the minlength attribute and a value to set a minimum value. Similarly, to set the maximum number of characters for a text field, we use the maxlength attribute and set a maximum value. Let’s take a look at these attributes in code:

<form action="/example.html" method="POST">
  <label for="summary">Summarize your feelings in less than 250 characters</label>
  <input id="summary" name="summary" type="text" minlength="5" maxlength="250" required>
  <input type="submit" value="Submit">
</form>

If a user tries to submit the <form> with less than the set minimum, this message appears:
"Please lengthen this text to 5 characters or more [you are currently using 2 characters]"


Example:
=======

<form action="submission.html" method="GET">
        <!--Add the minlength and maxlength attributes to the input fields-->
        <label for="username">Username:</label>
        <br>
        <input id="username" name="username" type="text" minlength="3" maxlength="15" required>
        <br>
        <label for="pw">Password:</label>
        <br>
        <input id="pw" name="pw" type="password" minlength="8" maxlength="15" required>
        <br>
        <input type="submit" value="Submit">
</form>

Matching a Pattern
==================
In addition to checking the length of a text, we could also add a validation to check how the text was provided. For cases when we want user input to follow specific guidelines, we use the pattern attribute and assign it a regular expression, or regex. Regular expressions are a sequence of characters that make up a search pattern. If the input matches the regex, the form can be submitted.

Let’s say we wanted to check for a valid credit card number (a 14 to 16 digit number). We could use the regex: [0-9]{14,16} which checks that the user provided only numbers and that they entered at least 14 digits and at most 16 digits.

To add this to a form:

<form action="/example.html" method="POST">
  <label for="payment">Credit Card Number (no spaces):</label>
  <br>
  <input id="payment" name="payment" type="text" required pattern="[0-9]{14,16}">
  <input type="submit" value="Submit">
</form>

Another example:
================
<form action="submission.html" method="GET">
    <label for="username">Username:</label>
    <br>
		<!--Add the pattern attribute to the input below-->
		<input id="username" name="username" type="text" required minlength="3" maxlength="15" pattern="[a-zA-Z0-9]+">
    <br>
        <label for="pw">Password:</label>
    <br>
		<input id="pw" name="pw" type="password" required minlength="8" maxlength="15">
    <br>
        <input type="submit" value="Submit">
</form>

Review:
======

Client-side validations happen in the browser before information is sent to a server.
Adding the required attribute to an input related element will validate that the input field has information in it.
Assigning a value to the min attribute of a number input element will validate an acceptable minimum value.
Assigning a value to the max attribute of a number input element will validate an acceptable maximum value.
Assigning a value to the minlength attribute of a text input element will validate an acceptable minimum number of characters.
Assigning a value to the maxlength attribute of a text input element will validate an acceptable maximum number of characters.
Assigning a regex to pattern matches the input to the provided regex.
If validations on a <form> do not pass, the user gets a message explaining why and the <form> cannot be submitted.


Best Practices
================
New web design trends come and go, and many times they are aesthetically appealing, but they are not always the most usable or accessible.

You now know enough principles of accessibility and usability to be able to judge if these trends will create problems for your users. Let’s reason through a few examples.

Text Overlaid on Images
=======================
White text overlaid on an image is a popular design trend. However, it doesn’t adhere to standards as the contrast is often too low. Adding a dark transparent overlay on top of the image could increase the contrast and provide better legibility.

Removing Input Labels
======================
Another trend often seen in web design is the removal of labels above input fields, sometimes relying on placeholder text instead to identify the input field.

While this enhances the aesthetic quality of a design in some instances, it can hinder a user’s ability to identify which input they are attempting to fill out. This is particularly true for low vision users because the placeholder text is often light gray and low contrast. This also creates problems for users employing screen readers, because the form’s placeholder text is not always narrated.

Buttons and Links
==================
There has been a trend towards flat and minimal design in recent years. This trend has improved usability in some ways, as it has encouraged designers to remove visual effects that are not contributing to the usability of their site.

However, minimalism can go too far, especially if it obscures how users should navigate the site. Visual contrast is especially important for buttons and links because these are the tools our users employ to navigate. Color alone should not be used to indicate clickability, as this will cause challenges for low vision and color-blind users.

Taking into consideration color choices, contrast, and font legibility will help you evaluate new design trends, and reduce the chance of new designs introducing accessibility barriers.

Semantic HTML Elements
======================
The quickest way of improving accessibility for screen readers is to use the appropriate tags for a given task.

For example, developers should wrap a navigation bar in a <header> element. Although the navigation bar could be wrapped in a <div> element with a class="header", the native semantics of a <header> element allows someone using a screen reader to understand and navigate a web page more efficiently.

<div id="header">
  <!-- Header Elements -->
</div>

In the example above, header content is wrapped in a <div> element with id="header". While this is valid HTML, an individual using a screen reader will not understand the purpose of the <div> and will have to piece the web page together as child elements are read out loud to them.

Native semantics of an element describes the element’s intended purpose. For example, the <header> element is intended to contain introductory and navigational elements such as a logo, links, or a search bar.

<header>
  <!--Header Elements-->
</header>

semantic elements                                               non-semantic elements

<nav>                                                               <div>
<header>                                                            <span>    
<article>
<form>
<table>
<h1>...<h6>
<address>
<footer>


ARIA Role
=========
Text on a web page can communicate different types of information. Some text may make up the main content of the page, other text may describe navigation icons, still other text might describe input fields or menus. It can be challenging to place text in the context of a web page without knowing where it is positioned or the type of information it is meant to communicate.

Take a moment to think about how a screen reader would interpret the Codecademy web page you are looking at right now. It would be difficult for someone using a screen reader to understand the difference in significance between the 
Preview: Docs A code editor is a program designed for writing software and utilizing human-readable text to make code easier to parse and understand.
code editor
 to the right and what you are currently reading.

To help add context to web page information, ARIA provides an HTML attribute called role. The value of an element’s role changes how a screen reader communicates the element.

<div id="code-editor" role="complementary">
  ...
</div>


In the example above, imagine the ... represents an exercise’s code editor — the section of the page containing the files of code you edit in an exercise. The role for the div is set to complementary. Visually, it makes sense that the information in the code editor is related to the information in the narrative (what you are reading right now). A user who uses a screen reader does not receive that visual cue.

Instead, the role="complementary" attribute and value can help a screen reader user understand that the information in the code editor is complementary (or supporting) to the information you are reading right now. It helps users of screen readers identify the relationship between the two sections of the page.

This link has a list of acceptable ARIA roles, where you can read more about the complementary role and other roles as well.

Here are some common ARIA roles:

role="button":

Use this role when an element (like a div or span) acts as a button.
Example:
html
Copy
Edit
<div role="button" onclick="alert('Button clicked!')">Click me!</div>
role="link":

Use this role to indicate that an element functions like a link.
Example:
html
Copy
Edit
<div role="link" onclick="location.href='https://example.com';">Go to Example</div>
role="navigation":

Use this role to define a section of the page that serves as navigation, such as a menu or sidebar.
Example:
html
Copy
Edit
<nav role="navigation">
  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
role="dialog":

Use this role to define a dialog box or modal.
Example:
html
Copy
Edit
<div role="dialog" aria-labelledby="dialogTitle" aria-hidden="true">
  <h2 id="dialogTitle">Dialog Title</h2>
  <p>This is a modal dialog box.</p>
</div>
role="alert":

Use this role for any content that should be announced as an alert (usually for warnings or errors).
Example:
html
Copy
Edit
<div role="alert">There was an error processing your request.</div>
role="form":

Use this role for defining a form element when you are using a div or another non-form element to represent a form.
Example:
html
Copy
Edit
<div role="form">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name">
  <button type="submit">Submit</button>
</div>
role="list":

Use this role to represent a list of items when a semantic <ul> or <ol> element is not used.
Example:
html
Copy
Edit
<div role="list">
  <div role="listitem">Item 1</div>
  <div role="listitem">Item 2</div>
  <div role="listitem">Item 3</div>
</div>
role="tabpanel":

Use this role for tab panels, which are content areas associated with tab navigation.
Example:
html
Copy
Edit
<div role="tabpanel" aria-labelledby="tab1">
  <p>This is the content for Tab 1.</p>
</div>

Using ARIA in HTML
In addition to ARIA roles, you may also encounter ARIA attributes such as aria-labelledby, aria-describedby, and aria-hidden. These attributes enhance the meaning and function of an element for screen readers and other assistive devices.

Example with ARIA role and attribute:

html
Copy
Edit
<button role="button" aria-label="Close" onclick="closeWindow()">X</button>
Here, the role="button" specifies the button's function, and aria-label="Close" provides an accessible label for screen readers, telling them that the button's purpose is to "close."


Another example:
================
 <div id="early" class="container">
    <span class="aside" role="note">Ada Lovelace is the favorite programmer of the author of this web page!</span>

ARIA Role: Presentation
========================
When a screen reader navigates a page, however, it reads out to the user each element’s name as it encounters them. Therefore, reading “ol“ outloud will slow down visually impaired users.

We can instruct screen readers to skip reading unnecessary elements by setting the role attribute to presentation.

<ol role="presentation">
  <li>List Item 1</li>
  <li>List Item 2</li>
</ol>

<div id="container" role="presentation">
  <p>I'm content you want to hear!</p>
</div>

In the example above, the <ol> element is assigned a role of presentation, meaning a screen reader will not read the element’s name (“ordered list”). This is acceptable, as a user does not need to hear the element’s name (“ordered list”) to understand the content of a list.

The presentation role skips over elements and their necessary children. The <ol> and <ul> elements require <li> children. Therefore, adding role="presentation" to an <ol> tag will cause the screen reader to skip directly to the text between the <li> tags (it will not read the names of the <li> elements).

ARIA Properties
==============
ARIA properties are attributes that you can add to HTML elements. These attributes provide additional information about elements that might not be obvious to users of screen readers. Let’s explore a property called aria-label.

<img src="#" alt="A painting of the Shenandoah Valley"/>
<p>Armand Cabrera, 2010</p>

<img src="#" alt="A painting of the Shenandoah Valley"/>
<p aria-label="Artist">Armand Cabrera, 2010</p>

Alt Attribute
=============
The alt attribute is used to describe an image (or several other elements). A screen reader will read the value of the alt attribute out loud. However, if the element cannot be visually seen — whether it is because the user is visually impaired, an incorrect source is referenced, or the page is being accessed over a slow connection — the alt attribute will be displayed in its place.

On the other hand, the value of aria-label will never be displayed on the screen and is a better choice for elements that do not support the alt attribute.

<img src="#" alt="a kitten snuggling a puppy"/>


Using semantic HTML elements whenever possible (such as <header> instead of <div id="header">) will allow screen reader users to navigate your website more efficiently.
The role attribute is used to communicate information about the role of specific elements.
role="presentation" allows a screen reader to skip markup elements that don’t directly contain useful information.
aria-label and other ARIA properties can be used to help users perceive information that is communicated visually but not through text.
The alt attribute should be added to every image element (and all other elements that support it) instead of aria-label. When used, its value should be a useful description of the image.
