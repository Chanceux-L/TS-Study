# type关键字

## 给类型取别名

```tsx
type Name = string;
type NameResolver = () => string;
type NameOrResolver = Name | NameResolver;

function getName(x: NameOrResolver): Name {
  return typeof x === 'string' ? x : x();
}
```

## 字符串字面量类型

```tsx
type EventNames = 'click' | 'scroll' | 'mousemove';
function handleEvent(el: Element, event: EventNames) {
  // do something
}

handleEvent(document.getElementById('element'), 'scroll');
handleEvent(document.getElementById('element'), 'dbclick'); // 报错，event不能为dbclick
```

