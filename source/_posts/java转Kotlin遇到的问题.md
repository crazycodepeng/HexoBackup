---
title: java转Kotlin遇到的问题
date: 2017-05-26 16:51:36
tags: [Kotlin,Java,Android]

---

1. 针对Context

 我们之前都是直接用 `Activity.this`,现在这么些不行了，
 解决方式：直接用`this`

2. 针对方法

 - 无参数无返回值方法：
    ``` kotlin
    fun init() {

           //button 点击事件
           hello.onClick { toast("点击了button") }
       }
    ```
 - 带参数无返回值方法：
    ``` kotlin
     fun showOne(a: Int,b: Int){

            toast(a+b)
        }

    ```
 - 带参数带返回值方法

    ``` kotlin
    fun showTwo(a: Int, b: Int): Int {
            return a + b
        }

    ```
3. Bean类的写法

 ``` kotlin

    data class UserBean(
            var name: String,
            var sex: String,
            var age: Int
    )

 ```

4. id直接赋值的写法添加anko的依赖

 ```
     compile 'org.jetbrains.anko:anko-sdk25:0.10.0-beta-1'// sdk15, sdk19, sdk21, sdk23 are also available
     compile 'org.jetbrains.anko:anko-appcompat-v7:0.10.0-beta-1'
     compile 'org.jetbrains.anko:anko-design:0.9.1'
     compile 'org.jetbrains.anko:anko-recyclerview-v7:0.9.1'
 ```

5. mainActivity代码

 ``` kotlin
 class MainActivity : AppCompatActivity() {

     private var aa = "33"
     public var bb = 33
     var cc = 'd'

     override fun onCreate(savedInstanceState: Bundle?) {
         super.onCreate(savedInstanceState)
         setContentView(R.layout.activity_main)

         //TextView 赋值
         text2.text = "我的text2"

         //无参数无返回值方法
         init()

         //带参数无返回值方法
         showOne(3, 2)

         //带参数返回值方法
         val one = showTwo(3, 2)
         toast(one)

         //bean
         showUser()
     }

     fun init() {
         //button 点击事件
         hello.onClick { toast("点击了button") }
     }

     fun showOne(a: Int,b: Int){
         toast(a+b)
     }

     fun showTwo(a: Int, b: Int): Int {
         return a + b
     }

     fun showUser(){
         UserBean("xm","man",16)

     }

 }


 ```
 Kotlin里边省去了java代码里每行结尾的 `;`

> 写到一半发现我重复造轮子了，<a href="https://github.com/MindorksOpenSource/from-java-to-kotlin/blob/master/README-ZH.md">前人造好的轮子</a>