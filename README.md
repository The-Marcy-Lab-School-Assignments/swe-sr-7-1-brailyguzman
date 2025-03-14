# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

In your own words, explain why React is a popular choice for building user interfaces. Make sure to mention at least one benefit, such as how it simplifies development, supports reusable components, or helps optimize performance. Feel free to include any specific features you find particularly helpful.

### Response 1

React is a popular choice for building UIs because it allows you to split the UI into small reusable components that can share the same functionality. React also allows you to keep state (data) in sync on each component, showing real-time state of the application, something that using the DOM would be a nightmare to do for a larger application.

## Prompt 2

Explain how the useState hook is used in React to manage state within functional components. In your response, include an example of how useState might be used in a simple application and why managing state is important in building interactive user interfaces.

### Response 2

## Prompt 3

Describe the different ways the useEffect hook can be triggered in a React component. Include an explanation of how the dependency array influences its behavior. If possible, provide a code example for each scenario to illustrate your explanation.

### Response 3

The useEffect hook can be triggered in two ways:

1. No dependencies - Every time the component re-renders, the useEffect runs.

```jsx
const App = () => {
  const [date, setDate] = useState(null);

  useEffect(() => {
    setDate(new Date());
    // No dependencies causes it to only run once, which is on render or re-render.
  }, []);

  return (
    <div id="app">
      <p id="date">{date}</p>
    </div>
  );
};
```

2. Dependencies - If any dependency inside the array get updated, the useEffect runs every time. Think of this as a side effect that happens when data gets updated in order to keep it in sync with the UI.

```jsx
const App = () => {
  const [username, setUsername] = useState(null);

  useEffect(() => {
    console.log(username);
    // Every time we update we update the username input, we are going to log the current username to the console.
  }, [username]);

  return (
    <div id="app">
      <input
        id="username"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
    </div>
  );
};
```

## Prompt 4

The component below makes a mistake when using useEffect. When running this code, we will get an error from React! Please fix this code.

```js
const DogDisplay = () => {
  const [imgSrc, setImgSrc] = useState(
    'https://images.dog.ceo/breeds/hound-english/n02089973_612.jpg'
  );

  useEffect(async () => {
    try {
      const response = await fetch('https://dog.ceo/api/breeds/image/random');
      if (!response.ok) throw new Error(`Error: ${response.status}`);
      const data = await response.json();
      setImgSrc(data.message);
    } catch (error) {
      console.error(error);
    }
  }, []);

  return <img src={imgSrc} />;
};
```

After fixing the code provide and explanation to what you fixed and why it needed to be fixed.

### Response 4
