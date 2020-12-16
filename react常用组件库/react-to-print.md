## 业务背景:
     需要在ant design pro的脚手架里进行在线打印操作，由于react不能很好进行局部打印，且不能很好进行dom节点操作，故此引入npm包
## react-to-print介绍：
     如果开发者已经创建了一个React组件，并希望用户最终能够打印出该组件的内容，并且希望控制打印样式就可以来使用该组件
> 参考文档:https://www.npmjs.com/package/react-to-print


```javascript
//第一步安装依赖
npm install —save react-to-print

import React from 'react';
import ReactToPrint, { PrintContextConsumer } from 'react-to-print';
import { ComponentToPrint } from './ComponentToPrint';
class Example extends React.PureComponent {
  render() {
    return (
      <div>
        <ReactToPrint content={() => this.componentRef}>
          <PrintContextConsumer>
            {({ handlePrint }) => (
              <button onClick={handlePrint}>打印当前页</button>
            )}
          </PrintContextConsumer>
        </ReactToPrint>
        <ComponentToPrint ref={el => (this.componentRef = el)} />//打印区域
      </div>
    );
  }
}
```

案例二:打开新的页面再去打印
```javascript
import React from 'react';
import ReactToPrint from 'react-to-print';
import { ComponentToPrint } from './ComponentToPrint';
class Example extends React.PureComponent {
  render() {
    return (
      <div>
        <ReactToPrint
          trigger={() => {
            // NOTE: could just as easily return <SomeComponent />. Do NOT pass an `onClick` prop
            // to the root node of the returned component as it will be overwritten.
            return <a href="#”>打开新页打印</a>;
          }}
          content={() => this.componentRef}
        />
        <ComponentToPrint ref={el => (this.componentRef = el)} />
      </div>
    );
  }
}
```
