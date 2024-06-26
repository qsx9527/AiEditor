# AiEditor 与 React 整合

在 React 中，我们通过使用 `useRef` Hook 得到 dom 节点，然后再通过 `new AiEditor` 进行实例化，示例代码如下：

```jsx
import {useEffect, useRef} from 'react'
import {AiEditor} from "aieditor";
import "aieditor/dist/style.css"

function App() {

    //定义 ref
    const divRef = useRef(null);

    //初始化 AiEditor
    useEffect(() => {
        if (divRef.current) {
            const aiEditor = new AiEditor({
                element: divRef.current,
                placeholder: "点击输入内容...",
                content: 'AiEditor 是一个面向 AI 的开源富文本编辑器。 ',
            })
            return ()=>{
                aiEditor.destroy();
            }
        }
    }, [])

    return (
        <>
            <div>
                <h1>AiEditor，一个面向 AI 的富文本编辑器</h1>
            </div>
            <div ref={divRef} style={{height: "600px"}} />
        </>
    )
}

export default App
```

更多 react 集成示例请参考：https://gitee.com/aieditor-team/aieditor/tree/main/demos/react-ts 