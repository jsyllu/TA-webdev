# Open Session Q&A

Date: 11/19/2021

### Q: Separate Front-end and Back-end 

According to the assignment requirement, there should be 2 git repositories for frontend and backend each. You also need to:

+ Deploy your React App on Netlify.

+ Deploy your Node Server on Heroku.

### Q: Netlify vs Heroku

First of all, they are all **Platform as a Service (PaaS)** but with different focus and provide different functionalities.

**Netlify** is a fit-to-purpose solution <u>specifically for website deployment</u> and hosting. It provides contiguous integration tools (push code to git repo and auto-deploy), which allow frontend developers to quickly deploy websites. 

**Heroku** is a more <u>general platform</u> to host various types of deployment including website deployment. It gears more towards backend which allows hosting entire application including database on a cloud environment. (Note: Heroku apps using free dynos will sleep after 1 hour of inactivity. This is why it might take a while for your app to wake up.)

### Q: How does Netlify React App communicate with Heroku Node App?

Go to React App, change all url where you use `fetch(someUrl)` (usually in someServices.js)

```javascript
const movieApi = "https://some-name.herokuapp.com"

// change all url in fetch()
// this function is for demonstration purpose, you need to compelete the function
const createMovie = () =>
	fetch(movieApi, {method: "POST"}).then()

const deleteMovie = (movieId) =>
	fetch(`${movieApi}/${movieId}`, {method: "DELETE"}).then()
```

### Q: Heroku Deploy Troubleshoot: Build Success but still Application Error

```javascript
// check your server.js
// make sure your app listen to this...

app.listen(process.env.PORT || 4000, ...);
```

### Q: What is `useEffect` in React and How to use it?

Syntax : `useEffect( ()=>{} , [dependencies] )`.

`useEffect` runs **after** the rendering/re-rendering of the component but only if any of the dependencies is changed.

In the following example, we set up initial state `[]` for `movies` (*NOTE1*) and initial state `[]` in `useEffect` hook, which will send a `GET` request to fetch all movies data and assign it to variable  `movies` as we mount the `Movies` component (*NOTE2*).

If `movies` is empty, we can render some messages indicating the data is not fetched yet (*NOTE3*).

````javascript
const Movies = () => {
    // NOTE1
    const [movies, setMovies] = useState([]);
    
    // NOTE2
    useEffect(() => {
        fetchMovies().then(movies => setMovies(movies));
    }, []);
    
    // NOTE3
    if (!movies) return (
        <div>Loading data...</div>
    ); 
    
	return (
    	<ul>
        {movies.map(movie => (
         	<li>{movie.title}</li>
         ))}
        </ul>
    )
}
````





