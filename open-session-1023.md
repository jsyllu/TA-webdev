# Open Session Q&A

Date: 10/15/2021

## React Conventions

+ To apply classes: use `className` instead of `class`

+ Inline CSS styling: use camelCased properties (e.g., `textDecoration`) instead of `text-decoration`

## Q: Warning: Each child in a list should have a unique key prop.

If you see this warning at your browser console...

```javascript
index.js:1 Warning: Each child in a list should have a unique "key" prop.
```

Modify your code:

```javascript
{posts.map((post, key) =>
	{
		return(
			<PostSummaryItem key={key} post={post}/>)
	})
}

// (post, key) means (objectYouWillUse, indexOfTheCurrentIteration)
```

Note: You don't have to use the iterating index (`key`), you may use **any unique value** that comes with the object (e.g., `object.id` if the object has an unique property of id).

## Q: Provide `alt` attribute to all `img` tags

If you see the following warning appears in the console of your IDE: 

```
Missing required 'alt' attribute
```

You should  add `alt` attribute to the `img` tag for the following reasons:

+ provide alternative information for an image if an user for some reasons cannot view it (e.g., due to slow connection or error in `src` attribute)
+ improve Accessibility of your website. 
  + Some users may have vision impairments and use screen readers (which reads everything out loud on the page) when visiting a website. As a developer, you need to ensure these groups of users can utilize as much functionality of your website as possible regardless of their ability.

Try to provide descriptive but not too wordy human-readable information for `alt` attribute.

In this example, we could place a variable (`who.userName`) in the `alt` text and format the text as `{who.userName}-avatar`.

````javascript
// given who = {userName: "java", avatarIcon: "./java.png"}

<img alt={`${who.userName}-avatar`} src={who.avatarIcon}/>

// if the image cannot be rendered correctly, it will show text "java-avatar"
````

## Q: Refactor Links to Previous Assignments

Follow the following steps to refactor the navigation links to previous assignments, and you will see assignment navigation links

+ ONLY appear at the entry point of your webapp which is `/` 
+ being removed from every other page

Note: You should NOT add any additional content in `index.html` unless you know what you're doing!

```javascript
// go to src/components/a6/HelloWorld.js -> This is the entry pooint of your app

import React from "react";
import A6 from "./index";
import History from "../../history";

const HelloWorld = () => {
  return (
      <div>
        <h1>Hello World!</h1>
        <A6/>
      	<hr />
        <History />
      </div>
  )
};

export default HelloWorld;
```

```javascript
// create a new file: src/components/a6/index.js
// This is to wrap all links related to A6

import React from "react";
import {Link} from "react-router-dom";

const A6 = () => {
  return (
      <>
        <h2>Assignment 6</h2>
        <Link to="/a6/practice">
          Practice
        </Link> | &nbsp;
        <Link to="/a6/twitter/explore">
          Build
        </Link> | &nbsp;
        <Link to="/a6/twitter/home">
          Challenge
        </Link>
      </>
  )
};

export default A6;
```

```javascript
// create a new file: src/components/history.js
// This is to wrap all links to your previous assignments

const History = () => {
  return (
      <div>
        <h2>Non React.js Assignments</h2>
        <h3>Assignment 2</h3>
        <ul>
          <li><a href="a2/practice/index.html">HTML Practice</a></li>
          <li><a href="a2/twitter/navigation.html">Twitter clone</a></li>
          <li><a href="a2/practice/iframe/index.html">Iframes</a></li>
        </ul>
        <h3>Assignment 3</h3>
        <ul>
          <li><a href="a3/practice/css/index.html">CSS Practice</a></li>
          <li><a href="a3/twitter/navigation.html">Twitter clone</a></li>
          <li><a href="a3/twitter/explore/explore.html">explore.html</a></li>
          <li><a href="a3/challenge/index.html">CSS Challenge</a></li>
        </ul>
<h3>Assignment 4</h3>
        <ul>
          <li><a href="a4/practice/bootstrap/index.html">Bootstrap Practice</a></li>
          <li><a href="a4/twitter/navigation.html">Twitter clone</a></li>
          <li><a href="a4/twitter/explore/explore.html">explore.html</a></li>
          <li><a href="a4/challenge/explore/explore.html">Boostrap Challenge</a></li>
        </ul>
        <h3>Assignment 5</h3>
        <ul>
          <li><a href="a5/practice/js/index.html">JavaScript & Console Practice</a></li>
          <li><a href="a5/practice/todos/index.html">ToDoList Practice</a></li>
          <li><a href="a5/build/ExploreScreen/explore.html">A5 Practice ExploreScreen</a></li>
          <li><a href="a5/a5Challenge/HomeScreen/index.html">A5 Challenge HomeScreen</a></li>
        </ul>
      </div>
  )
}

export default History;

```

```javascript
// go to public/index.html, replace the entire file with the following content
// if you added additional cnd resources, please keep that in head tag

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8"/>
  <link rel="icon" href="%PUBLIC_URL%/favicon.ico"/>
  <meta name="viewport" content="width=device-width, initial-scale=1"/>
  <meta name="theme-color" content="#000000"/>
  <meta
      name="description"
      content="Web site created using create-react-app"
  />
  <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png"/>
  <link rel="manifest" href="%PUBLIC_URL%/manifest.json"/>
  <script src="https://kit.fontawesome.com/3f86e119a7.js" crossorigin="anonymous"></script>
  <title>Twitter Clone</title>
</head>
<body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
</body>
</html>
```

