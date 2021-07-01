---
title: React Hook
date: 2021-4-1 12:00:00
categories: 
    - web前端开发
    - JavaScript
tags: 
    - JavaScript
    - 前端开发
mp3: http://music.163.com/song/media/outer/url?id=493093412.mp3
cover: https://img1.baidu.com/it/u=3097890609,3437789999&fm=26&fmt=auto&gp=0.jpg
---

Hook 是React 16.8的新增特性。它可以让你在不编写 class的情况下使用 state 以及其他的 React特性。
   Hook是一些可以让你在函数组件里“钩入” React state 及生命周期等特性的函数
   Hook 不能在 class 组件中使用
   `const [state, setState] = useState(initialState)`
   返回一个 state,以及更新 state 的函数
   当 state 为引用类型，修改时注意要合并其他值，不然会发生错误
   多个 state 最好分开写
   setState 也可以接收一个函数

   ```  //useState
        function Home(){
            const [count, setCount] = useState(0)
            //也可以在state里写对象
            const [person, setPerson] = useState({
                name:'言崽',
                age:'18',
                sex:'男'
            })
            const [num,setNum] = useState(100)
            return (
                <div>
                    我是todolist
                    count:{count}
                    <button onClick={()=>{setCount(count+1)}}>加+</button>
                    {/* setCount和class组件setState是一样的都是修改state的状态的*/}
                    <div>
                        name:{person.name}
                        age:{person.age}
                        sex:{person.sex}
                        <button onClick={()=>{setPerson({age:19})}}>言崽</button>
                        {/* 这里当我们点击了按钮调用setState，只修改了age,虽然年龄变成了19，但是其他属性都为空了，所以说
                            在调用setState时，如果它是个引用类型时我们要它另外值合并一下
                            onClick={()=>{setPerson({age:19,name:person.name,sex:person.sex})}}
                            这样写就没问题了
                        */}
                    </div>
                    <div>
                        计数：{num}
                        <button onClick={()=>{setNum((oval)=>{console.log(oval);return oval+1})}}></button>
                        {/* setState还可以接收一个函数 */}
                    </div>
                </div>
            )
        }
        export default Home
   ```
# useEffect
```
        useEffect(()=>{//参数是个函数：也叫副作用函数
             return ()=>{}//返回函数 返回的函数式可选的  可以不写返回函数
         },[])//这里的数组是依赖参数   依赖也是可选的
        作用函数：
         1.当useEffect ,没有依赖参数时，副作用函数，会在组件挂载完成及组件更新完成时执行
         2.当有依赖参数副作用函数，会在组件挂载完成及改依赖参数修改，引起的组件更新完成之后执行
         3.当依赖参数为空数组时，会在组件挂载完成之后执行
         4.返回函数在组件更新完成，或即将写在执行，一般返回函数用在即将卸载时
         useEffect(()=>{//当没有依赖参数和返回函数的时候，现在就相当于class组件的componentDidMount、componentUpdate生命周期
        console.log(1,'useEffect')//一直触发btn，一直在打印
    })
    useEffect(()=>{//当依赖参数为空和没有返回函数时，只执行了一次，后面在触发btn时，不在执行.相当于componentDidMount
        console.log(2,'useEffect')
    },[])
    useEffect(()=>{
        console.log(3,'useEffect')
    },[name])//在有依赖参数时，组件挂载完会执行一次，在后面触发btn时，如果依赖参数没有发生改变，不会再打印
    useEffect(()=>{
        return ()=>{
            console.log(4,'useEffect')
        }//当没有依赖，有返回函数的时候，初次挂载完返回函数不会执行，但是当触发btn时，就是组件发生改变，它就会执行返回函数的代码
    },)//如果此处有依赖，但不空，那就当依赖的参数发生改变的时候，返回函数内的代码也会执行
    useEffect(()=>{
        return ()=>{
            console.log('更新或者卸载')
        }
    },[count])//也可以有依赖参数并且会更新用返回函数进行卸载或更新
    //缺点：挂载前和更新前的生命周期要用到别的方法来配合使用useEffect。这里更多的是挂载完和更新完
```
# useLayoutEffect
其函数签名与useEffect相同，但它会在所有的DOM变更之后同步调用effect。可以使用它来读取DOM布局并同步触发重渲染，在浏览器执行绘制之前，useLayoutEffect内部的更新计划将不同步刷新
# useContext
```
一个简单的传参案例基本就能明白useContext是在干神马。
import React,{createContext, useContext} from 'react'
const DemoContext = createContext({data:'hello'})
function A (){
    return (
        <DemoContext.Provider value={{data:value}}>
            <B></B>
        </DemoContext.Provider>
    )
}
function B(){
    return (
        <div>
            儿子组件
            <C></C>
        </div>
    )
}
function C(){
    const text = useContext(DemoContext)
    return (
        <div>
            孙子组件
            {
                text.data
            }
        </div>
    )
}
export default A
```
# useReducer
```
在我们的需要处理的数据足够简单时，用useState就能完成。如果数据比较复杂了那么就可以考虑用useReducer
这个先说下useReducer跟Store没关系，他只是借用了store的那套思想
直接上案例
import React, { useState, useEffect, useReducer, useRef } from 'react'
import { withRouter } from 'react-router-dom'
import { connect } from 'react-redux'
import s from './index.module.scss'
let init = { list: [{
    id:1,
    name:'海底捞',
    open:1
}] }
function reducer(state, action) {
    switch (action.type) {
        case 'add':
            let arr = JSON.parse(JSON.stringify(state.list)) 
            arr.push({
                id: state.list.length > 0 ? state.list[state.list.length-1].id + 1 : 1,
                name: action.name,
                open: 1,
            })
            return {list:arr}
        case 'close':
           for(let i=0;i<state.list.length;i++){
               if(state.list[i].id==action.id){
                   state.list[i].open=2
               }
           }
           return JSON.parse(JSON.stringify(state))
        case 'open':
           for(let i=0;i<state.list.length;i++){
               if(state.list[i].id==action.id){
                   state.list[i].open=1
               }
           }
           return JSON.parse(JSON.stringify(state))
        case 'set':
           for(let i=0;i<state.list.length;i++){
               if(state.list[i].id==action.id){
                   state.list[i].open=3
               }
           }
           return JSON.parse(JSON.stringify(state))
        case 'del':
           for(let i=0;i<state.list.length;i++){
               if(state.list[i].id==action.id){
                   state.list.splice(i,1)
               }
           }
           return JSON.parse(JSON.stringify(state))
        default:
            return state
    }
}
function Homet(props) {
    const inp = useRef(null)
    const [state, dispatch] = useReducer(reducer, init)
    function btn() {
        if (!inp.current.value) {
            alert('输入不能为空')
        } else {
            dispatch({
                type: 'add',
                name: inp.current.value,
            })
            inp.current.value=null
        }
    }
    return (
        <div className={s.homet}>
            <div className={s.head}>
                <span>Todo后台管理</span>
                <div className={s.inpBox}>
                    <input ref={inp} placeholder='请输入内容' />
                    <button onClick={() => btn()} className={s.btn}>添加</button>
                </div>
            </div>
            <div className={s.cont}>
                {
                    state.list.length > 0 ? state.list.map((item, i) => <div className={s.item} key={i}>
                        <img />
                        <div className={s.all}>
                            <span className={s.name}>{item.name}</span>
                            <span>{item.open == 1 ? '营业中' : item.open == 2 ? '已打烊' : '装修中'}</span>
                        </div>
                        <div className={s.del}>
                            {
                                item.open == 1 ? <div className={s.btnBox}>
                                    <button onClick={()=>dispatch({type:'close',id:item.id})} className={s.margin}>打烊</button>
                                    <button onClick={()=>dispatch({type:'set',id:item.id})}>装修</button>
                                </div> : item.open == 2 ? <div className={s.btnBox}>
                                    <button onClick={()=>dispatch({type:'open',id:item.id})} className={s.margin}>营业</button>
                                    <button onClick={()=>dispatch({type:'set',id:item.id})}>装修</button>
                                </div> : <div className={s.btnBox}>
                                            <button onClick={()=>dispatch({type:'open',id:item.id})} className={s.margin}>营业</button>
                                            <button>待完成</button>
                                        </div>
                            }
                            <button onClick={()=>dispatch({type:'del',id:item.id})} className={s.shan}>删除</button>
                        </div>
                    </div>) : <span className={s.no}>暂无数据</span>
                }
            </div>
        </div>
    )
}
let mapStateToProps = (state) => {
    console.log(state)
    return {
        list: state.list.list
    }
}
let mapDispatchToProps = (dispatch) => {
    return {

    }
}
Homet = withRouter(Homet)
export default connect(mapStateToProps, mapDispatchToProps)(Homet)
```
