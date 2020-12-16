### 如何用typescript的方式写一个react组件

```typescript
/* eslint-disable @typescript-eslint/no-unused-vars */
import React,{useState} from "react";
import { Dispatch,connect } from "umi";
import styles from './style.less'
import {Button, Table,Modal, Divider} from "antd";

interface antd_table{
    dataSource:Array<Object>,
    columns:Array<Object>,
    bordered:boolean
};
const dataSource:Array<Object> = [
    {
        key:1,
        name:'wyh',
        age:23,
        action:0
    },
    {
        key:2,
        name:'wyh',
        age:23,
        action:1,
    },
];
// typescript写一个函数
const columns=function(setDisplay:Function):Array<Object>{
    return [
        {
            title:'姓名',
            align:'center',
            dataIndex:'name',
            render:(record:any,row:Object,index:any)=>{
            return <p>{record}</p>
            }
        },
        {
            title:'年龄',
            align:'center',
            dataIndex:'age',
        },
        {
            title:'操作',
            align:'center',
            dataIndex:'action',
            render:(record:Number)=>{
                return <><Button type='primary' danger>删除</Button><Divider type='vertical' /><Button type='primary' onClick={()=>setDisplay(true)}>修改</Button></>
            }
        }
    ];
}

const NewTable:React.FC<antd_table>=()=>{
    const [display,setDisplay] = useState(false);
    return <div>
        <Table className={styles.wrapper} dataSource={dataSource} columns={columns(setDisplay)} bordered={true}/>
        <Modal visible={display} onOk={()=>setDisplay(false)} onCancel={()=>setDisplay(false)}/>
    </div>
}
export default NewTable;

```



### 如何更改antdpro脚手架的样式

```less
.wrapper{
    :global(.ant-table-thead> tr > th){
            background-color: blue !important; 
    }
}
```



### 如何配置全局主题色

antdUI提供的一些默认的组件的样式是跟着主题走的，在config文件夹里配置defaultSettings.ts文件里配置

```typescript
import { Settings as ProSettings } from '@ant-design/pro-layout';

type DefaultSettings = ProSettings & {
  pwa: boolean;
};

const proSettings: DefaultSettings = {
  navTheme: 'light',
  primaryColor: '#722ED1',//更改这个参数即可
  layout: 'sidemenu',
  contentWidth: 'Fluid',
  fixedHeader: false,
  fixSiderbar: false,
  colorWeak: false,
  menu: {
    locale: true,
  },
  title: '****',
  pwa: false,
  iconfontUrl: '',
};

export type { DefaultSettings };

export default proSettings;
```

### 如何在typescript+antdpro脚手架里进行服务端数据交互

model文件夹,注意两点即可：首先需要定义一个数据类型接口，用于限制model里的state数据结构，接着定义model的数据结构，model的数据结构定义要引用到umi里的Reducer和Effect分别限制reducers和effects的数据结构

```typescript
import {Reducer,Effect} from 'umi';
import {getServerData} from '../service';
// 这里声明的变量类型应该是model里state下面的数据类型
export interface TestStateType{
    data:Object;
}

export interface TestModelType{
    namespace:string;
    state:TestStateType;
    effects:{
        getData:Effect;
    };
    reducers:{
        saveData:Reducer<TestStateType>;//注意这里的接口跟state接口一致
    };
}

const Model:TestModelType={
    namespace:'testmodel',
    state:{
        data:{}
    },
    effects:{
        *getData({payload,callback},{call,put}){
            const res = yield call(getServerData,payload);
            console.log(res);
        }
    },
    reducers:{
        saveData(state,{payload}){
            return {
                ...state,
                data:payload
            }
        }, 
    }

}


```

service文件夹

```typescript
import request from '@/utils/request';
export async function getServerData(params: any) {
   return await new Promise((resolve, reject) => {
        fetch(`http://localhost:3000/test1`,
            { method: 'POST' },
            function (res) {
            })
            .then(res => {
                if (res.status == 200) {
                    resolve(res.json());
                } else {
                    reject(new Error('错误!'))
                }
            });
    });

};
```

