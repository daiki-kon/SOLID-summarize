## ðcontext
propsããã±ããªã¬ã¼ã§æ¸¡ãã®ã§ã¯ãªããã³ã³ãã¼ãã³ãéã§å¤ã
å±æããããã®ãã®ãªãã¸ã§ã¯ãã \
Reactã®ä¸æ©è½ã \
https://ja.reactjs.org/docs/context.html

### ðcreateContext()
ã³ã³ãã­ã¹ããªãã¸ã§ã¯ããä½æããã \
å¼æ°ã¯ã³ã³ãã­ã¹ãã®åæå¤ã

```tsx
const MyContext = React.createContext(defaultValue);
```

https://ja.reactjs.org/docs/context.html#reactcreatecontext

### ðContext.Provider
ãã®ã³ã³ãã¼ãã³ãéä¸ã«ããå ´åContextã«ã¢ã¯ã»ã¹å¯è½ã \
`value`ã®å¤ãå­å­«ã«æ¸¡ãããã

```tsx
<MyContext.Provider value={/* ä½ããã®å¤ */}>
```

https://ja.reactjs.org/docs/context.html#reactcreatecontext

## ðuseContext
`React.createContext`ããã®æ»ãå¤ãå¼æ°ã¨ãã
ãã®contextã®ç¾å¨ã®ãªãã¸ã§ã¯ããåå¾ãããã®ã

> ã³ã³ãã¯ã¹ãã®ç¾å¨å¤ã¯ãããªã¼åã§ãã®ããã¯ãå¼ãã ã³ã³ãã¼ãã³ãã®ç´è¿ã«ãã <MyContext.Provider> ã® value ã®å¤ã«ãã£ã¦æ±ºå®ããã¾ãã


â» ç´è¿ã® <MyContext.Provider> ãæ´æ°ãããå ´åããã®ããã¯ã¯ãã® MyContext ãã­ãã¤ãã«æ¸¡ãããææ°ã® value ã®å¤ãä½¿ã£ã¦åã¬ã³ãã¼ãçºçããã¾ãã

```tsx
const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};

const ThemeContext = React.createContext(themes.light); ðåæå¤ãè¨­å®ãã¦contextãä½æ

function App() {
  return (
    <ThemeContext.Provider value={themes.dark}> ðããã®valueã§æ±ºã¾ãã¨ããæå³,ä¸ã§åæåãã¦ããã¾ãæå³ã¯ãªããã
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </button>
  );

```

## ð§contextã¯ãã¼ã¿ãå­å­«ã®ã³ã³ãã¼ãã³ãããã¢ã¯ã»ã¹ã§ããããã«ãã
![image](https://user-images.githubusercontent.com/61902151/114731150-763ac280-9d7c-11eb-86a8-9480d69538ed.png)


## ðuseReducer
ç¶æç®¡çãè¡ãããã®ãã®ã \
æ©è½ã¨ãã¦ã¯åãã ããè¤æ°éå±¤ã«ã¾ããã£ã¦ç¶æç®¡çãå¯è½ã

```tsx
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

## çµã¿åãããã¨

```tsx
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```


## ðãã¼ã¿ã®æµã 
