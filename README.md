# SOLID-summarize

# インターフェース分離の原則 (ISP)

## ISPとは
> (247)

すごい簡単にいうと、利用するものだけ実装する。(インターフェースはシンプルに保つ)
[参考](https://note.com/erukiti/n/n3daa55541bc8)

例を出すと…　[参考](https://qiita.com/yui_mop/items/93fef037a787318e7067)
```.ts
interface Animal {
  run: () => void;
  eat: () => void;
  fly: () => void;
}

interface Bird implements Animal {
  function run(){
    ...
  }
  
  function eat(){
    ...
  }
  
  function fly(){
    ...
  }
}

interface Human implements Animal {
  function run(){
    ...
  }
  
  function eat(){
    ...
  }
  
  function fly(){
    ...
  }
}

```

インターフェースと言うだけに基本的にはオブジェクト指向でのルールっぽい。

Reactを関数コンポーネントで作成している場合はデータ型の定義がイメージとして近いかも

```.ts
type User {
  name: string;
  phoneNumber: string;
  address: string;
}

```

## 依存関係逆転の原則 (DIP)

> 実装しているコードをimportするのではなく抽象的なものをimportする
 
 ### 依存しているとは
 
 Hoge.tsx
```hoge.tsx
export const register = (item: any): boolean => {
  // 登録... 
}
```

Fuga.tsx
```Fuga.tsx
import { register } from a.tsx

const Fuga: FC = () => {
  const registerUser = () => {
    // 処理...
    register();
  }
  
  return(
    <label>ユーザ登録</label>
    <button onClick={registerUser}>登録</butotn>
  )
}
```

このとき`Fuga`は`Hoge`に依存している -> `Hoge`を変更すると`Fuga`にも影響が出てしまう。

### DIPの前提

抽象的なインターフェース -> 安定
具体的に実装されているもの -> 不安定

インターフェースが修正 -> 実装も修正
実装を修正 ->　インターフェースは修正しなくても良い

イメージとしてはAPIのSwagger?
インターフェース（クエリパラメータ等)が定められており、APIで修正したからと言ってフロントエンドも修正する必要はない。

関数コンポーネントをベースに考えるのは難しい。。。

