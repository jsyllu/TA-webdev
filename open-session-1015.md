# Open Session Q&A

Date: 10/15/2021

❓ How to get your questions answered in this session? 

❗ Drop your questions on the weekly open-session piazza post! Be clear and concise! Make sure you read existing questions carefully to avoid repetition of questions. If you have questions about coding, come to the session and send over your related code snippet, we'll do live coding together.

**Note**: All questions answered will be documented in a markdown file which will be public after the session on https://github.com/jsyllu/TA-webdev/.

### Q: My stylesheets are not applying to html within the functions in my .js files.  I have my stylesheet listed after bootstrap in my explore.html. Is there something else I need to do?

A: Need to see the file structure. Check if you imported the right file (file path, file name).

### Q: Could you talk something about how you design a web when you are doing an assignment, I found myself spending much time on details. And the different usage of `` in JavaScript and the {} in React and how to rewrite each other. Thank you so much for holding this session for us!

A: 

#### Good Practices for designing a webpage: 

Top-down approach

1. starting from layout
2. make things work first, and then refactor your code and group them by smaller components
3. Assemble the smaller components to form larger components -> Your code is more reusable and organized!

#### Comparison: HTML String vs React Function vs React Component

`` is a html string which should contain regular html tags. If you're using variables inside of a html string, you need to use ${} to wrap the variables. In react, there's no need to use ${}, since it's a javascript file already, instead, we only need to use {} to wrap variables inside of html tags. 

##### HTML String Example:

```javascript
// paragraph: string = "hello world"

const htmlStr = `<div><p>${paragraph}</p></div>`

// add the above string to on the browser: hello world
```

##### React Function Call Example:

```javascript
// in App.js
// paragraph: string = "hello world"

const para = (paragraph) => {
 return (
  <div>
   <p>{paragraph}</p>
  </div>
 )
}

// add this line to call the para function:
{para("hello world")}

// on the browser: hello world
```

##### React Component Call Example:

Note: for React component, capitalize the component name.

```javascript
// in App.js
// paragraph: string = "hello world"

const paraComponent = ({paragraph}) => {
 return (
  <div>
   <p>{paragraph}</p>
  </div>
 )
}

// add this line to call the para function:
<paraComponent paragraph="hello world" />

// on the browser: hello world
```

### Q: I am trying to get the TODO practice working on assignment 5 and have been having issues. When I try the code as-is in the document, I get an error in my console `Origin null is not allowed by Access-Control-Allow-Origin.` and nothing shows on the page. When I remove `type="module"` from the `<script>` tag loading index.js, it looks like it at least starts to load, but then it says `SyntaxError: Unexpected identifier 'TodoList'. import call expects exactly one argument.` I'm assuming this means I have to get it working with `type="module"`, how do I do this?

A: stackoverflow.

### Q: A5-challenge - Parameterize the NavigationSidebar component: how to dynamically assign "active" to links?

A: 

```javascript
// Note: If you're returning html content as a string wrapped in backticks ``, you won't need more layers of ``.
// For code reference, please see the next code code block.

const activeLink = path.getpath(); //  = explore.html

// good practice to have this data structure to store all navlinks
// separate data from html & js code
const navlinks = [
    {text: "Home", link: "home.html", iconClass: "fas fa-hashtag"},
    {text: "Explore", link: "explore.html", iconClass: "fas fa-home d-inline-block"}
]

const NavSideBar = ({link}) => {
    return (
        <div>
            {navlinks.map(navlink => 
                    <a class=`list-group-item list-group-item-action ${link === navlink.link? "active" : ""}` href=${navlink.link}>
                     <i class=${navlink.iconClass}></i>
                        <div class="d-inline-block">
                            <div class="d-sm-none d-xl-block">${navlink.text}</div>
                        </div>
                    </a>
                )
            }
		</div>
	)
}
```

```javascript
// Only apply this syntax when you're returning html content as a string

const NavSideBar = ({link}) => {
    return (`
		<div>
            {navlinks.map(navlink => 
                    <a class="list-group-item list-group-item-action ${link === navlink.link? "active" : ""}" href=${navlink.link}>
                     <i class=${navlink.iconClass}></i>
                        <div class="d-inline-block">
                            <div class="d-sm-none d-xl-block">${navlink.text}</div>
                        </div>
                    </a>
                )
            }
		</div>
	`)
}
```

### Q: How to conditionally show a div?

A:

```javascript
// This is in React

const post = {content: "n", image: "some url", title: "The Title", paragraph: "some paragraph", link: "www.google.com"}

<div class="col-11 wd-post1-row2-right">
	<img class=`wd-post1-row2-image ${post.content === "n" ? "round-image" : ""}` src={post.image} />
    <!— if post.content === 'n', class="wd-post1-row2-image  round-image", else, class="wd-post1-row2-image " ->
          
  	{post.content === 'n' ? 
   		<></> :
    	<div class="wd-post1-row2-content">
      		{post.title !== null && post.title !== '' ? 
     			<p class="wd-post1-row2-content-title mt-1 ms-2">{post.title}</p> : <></>}
			{posts.paragraph !== null && post.paragraph !== '' ? 
                <p class="wd-post1-row2-content-paragraph mt-1 ms-2">{posts.paragraph}</p> : <></>}
			{post.link !== null && post.link !== '' ? 
                <a href="#"> <i class="fas fa-link wd-post1-row2-content-link mt-1 ms-2">{post.link}</i> </a> : <></>}
		</div>
	}
</div>

```

