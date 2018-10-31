# component-base
vue 父子组件传值基础


父组件给子组件传值

    1.父组件调用子组件的时候 绑定动态属性
        <v-header :title="title"></v-header>

    2、在子组件里面通过 props接收父组件传过来的数据
        props:['title']



        props:{

            'title':String      
        }

    3.直接在子组件里面使用



父组件主动获取子组件的数据和方法：

    1.调用子组件的时候定义一个ref

        <v-header ref="header"></v-header>

    2.在父组件里面通过

        this.$refs.header.属性

        this.$refs.header.方法





子组件主动获取父组件的数据和方法：  


        this.$parent.数据

        this.$parent.方法

