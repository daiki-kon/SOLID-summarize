## 👉context
propsをバケツリレーで渡すのではなく、コンポーネント間で値を
共有するためのものオブジェクト。 \
Reactの一機能。 \
https://ja.reactjs.org/docs/context.html

### 🌞createContext()
コンテキストオブジェクトを作成する。 \
引数はコンテキストの初期値。

```tsx
const MyContext = React.createContext(defaultValue);
```

https://ja.reactjs.org/docs/context.html#reactcreatecontext

### 🌞Context.Provider
このコンポーネント配下にいる場合Contextにアクセス可能。 \
`value`の値が子孫に渡される。

```tsx
<MyContext.Provider value={/* 何らかの値 */}>
```

https://ja.reactjs.org/docs/context.html#reactcreatecontext

## 👉useContext
`React.createContext`からの戻り値を引数とし、
そのcontextの現在のオブジェクトを取得するもの。

> コンテクストの現在値は、ツリー内でこのフックを呼んだコンポーネントの直近にある <MyContext.Provider> の value の値によって決定されます。


※ 直近の <MyContext.Provider> が更新された場合、このフックはその MyContext プロバイダに渡された最新の value の値を使って再レンダーを発生させます。

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

const ThemeContext = React.createContext(themes.light); 👈初期値を設定してcontextを作成

function App() {
  return (
    <ThemeContext.Provider value={themes.dark}> 👈ここのvalueで決まるという意味,上で初期化してもあまり意味はなさそう
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

## 🧚contextはデータを子孫のコンポーネントからアクセスできるようにする
![image](https://user-images.githubusercontent.com/61902151/114731150-763ac280-9d7c-11eb-86a8-9480d69538ed.png)


## 👉useReducer
状態管理を行うためのもの。 \
機能としては同じだが、複数階層にまたがって状態管理が可能。

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

## 組み合わせると

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


## 👁データの流れ 
