# Open Session Q&A

Date: 10/29/2021

## Q: How insert html string from a JSON file into React component (.JS file)?

<img src="C:\Users\jessi\AppData\Roaming\Typora\typora-user-images\image-20211029145917569.png" alt="Q1-effect" style="width:85%;"/>

```javascript
// post.json

posts = [
	{"comment": "Amazing show about <a href='#' style='color: lightblue;' class='wd-no-decor wd-bluetxt'>@Inspiration4x</a> mission!"}
]
```

```javascript
// PostItem.js
// iterating over posts, current => post

<span dangerouslySetInnerHTML={{__html:post["comment"]}}></span>
```



