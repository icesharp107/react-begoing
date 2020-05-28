#### 快速开始

简单组件
render():接收输入的数据并返回需要展示的内容
this.props：通过它来传入数据给组件

```js
class HelloMessage extends React.Component{
    render(){
        return (
            <div> hello {this.props.name} </div>
        )
    }
}
ReactDOM.render(
    <HelloMessage name="TayLor" /> //hello TayLor
    document.getElementById('hello-example')
);
```
状态组件
```js
class Time extends React.Component(){
    constructor(props){ super(props); this.state = { seconds:0 } }
    tick(){ this.setState((state)=>{ seconds:state.seconds+1 }) }
    componentDidMount(){ this.initerval = setInterval(()=> this.tick(),1000);}
    componentWillUnmount(){ clearInterval(this.interval) }
    render(){
        return(
          <div> seconds {this.state.seconds} </div> //不断累加
        )
    }
}
```
应用
```js
class TodoApp extends React.Component(){
     constructor(props){
         super(props);
         this.state = { items:[],text:''};
         this.handleChange  =this.handleChange.bind(this);
         this.handleSubmit =this.handleSubmit.bind(this);
     }
     render(){
         return(
             <h3>TODO<h3/>
             <TodoList items={this.state.items}/>
             <form>
                <label htmlFor="new-todo">你需要什么</label>
                <input
                    id="new-todo"
                    onChange={this.handleChange}
                    value={this.state.text}
                />
                <button> Add # {this.state.items.length+1}</button>
             </form>
         )
     }
     handleChange(e){ this.setState( {text: e.target.value});}
     hangleSubmit(e){
         e.preventDefault();
         if(this.state.text.lenth === 0){ return;}
     }
}
class TodoList extends React.Component(){
    render(){
        <ul>
            {this.props.items.map(item=>(<li key={item.id}>{item.text}</li>))}
        <ul/>
    }
}
ReactDOM.render(
    <TodoApp />
    document.getElementById('todos-example')
)
```