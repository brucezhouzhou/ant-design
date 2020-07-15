---
order: 10
title:
  zh-CN: 通过 Hooks 获取上下文
  en-US: Get context with hooks
---

## zh-CN

通过 `message.useMessage` 创建支持读取 context 的 `contextHolder`。

## en-US

Use `message.useMessage` to get `contextHolder` with context accessible issue.

```jsx
import { message, Button } from 'antd';

const Context = React.createContext({ name: 'Default' });

function Demo() {
  const [messsageApi, contextHolder] = message.useMessage();
  const info = () => {
    messsageApi
      .info(<Context.Consumer>{({ name }) => `Hello, ${name}!`}</Context.Consumer>, 3)
      .then(() => {
        console.log('promise me');
      });
  };

  return (
    <Context.Provider value={{ name: 'Ant Design' }}>
      <Button type="primary" onClick={info}>
        Display normal message
        {contextHolder}
      </Button>
    </Context.Provider>
  );
}

ReactDOM.render(<Demo />, mountNode);
```
