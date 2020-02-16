# 常用的生命周期
```js
import React, { Component } from 'react'
import './style.styl'
export default class Test extends Component {
    state = {
        num:0
    }
    // 初始化阶段，不能使用setState
    constructor(props){
        super(props);
        console.log("1.constructor","只会执行一次");
    }
    // 1.每次渲染之前，都会执行该生命周期
    // 2.该生命周期函数可接受两个参数，分别为props和state
    // 3.当props和state任意一个发生改变时，就会执行该函数
    // 4.该函数有返回值
    // 5.由于该函数是静态的，所以里面无法使用this
    static getDerivedStateFromProps(props,state){
        console.log("2.getDerivedStateFromProps");
        return 1;
    }
    // 性能优化点
    // 接受两个参数
    // 第一次渲染时不执行
    shouldComponentUpdate(preProps,preState){
        console.log("3.shouldComponentUpdate",preProps,preState);
        return true;
    }

    componentDidMount(){
        console.log("5.componentDidMount")
    }
    render() {
        console.log("4.render")
        return (
            <div>
                <h1>test测试</h1>
                <button onClick={()=>{
                    this.setState({
                        num:this.state.num + 1
                    })
                }}>改变内部状态</button>
            </div>
        )
    }
}

```