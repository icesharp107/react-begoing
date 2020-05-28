
```js
ReactDom.render(
    <h1>hello world!</h1>
    document.getElementById('root')
)
```
* jsx 语法扩展
    * 嵌入式(变量、表达式)
    * 表达式、特点属性
```js
const name = 'Josh Perez';
const element = <h1>hello {name}!</h1>;

ReactDom.render(
    element,
    document.getElementById('root')
);
//嵌入式表达式
function BBB(user){ return user.a+''+user.b}
const user = {a:'123',b:'456'};
const e = {<h1>hello {BBB(user)}!</h1>;}
//表达式
function AAA(user){
    if(user){ return <h1>hello {BBB(user)}!</h1>;}
    return <h1>hello ssss!</h1>;
}
```

* 
```
```
