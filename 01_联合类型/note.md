# 联合类型

联合类型（Union types）表示取值可以为多种类型中的一种。

eg：

```tsx
let a = string | number;
a = 'seven';
a = 7
a = false; // 报错，a类型只能为字符串或数值类型
```

## 访问联合类型的属性或方法

当TS不确定一个联合类型的变量到底是哪个类型的时候，我们**只能访问此联合类型的所有类型里的共有属性或方法**。

```tsx
function getLength(thing: string | number): number {
  return thing.toString();
  return thing.length; // 报错，length不是string和number的共有属性
}
```

