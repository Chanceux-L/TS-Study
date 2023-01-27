# 泛型

泛型（Generics）是指在定义函数、接口或类的时候，不预先指定具体的类型，而在使用的时候再指定类型的一种特性。

```tsx
function createArray(length: number, value: any) :Array<any> {
  let result = [];
  for (let i = 0; i < length; i++) {
    result[i] = value;
  }
  return result;
}
createArray(3, 'x'); // ['x', 'x', 'x']

// 使用泛型
function createArray<T>(length: number, value: T) :Array<T> {
  let result: T[] = [];
  for (let i = 0; i < length; i++) {
    result[i] = value;
  }
  return result;
}
createArray<string>(3, 'x'); // ['x', 'x', 'x']
```

## 多个类型参数

```tsx
function swag<T, U>(tuple: [T, U]): [U, T] {
  return [tuple[1], tuple[0]];
}

swag(7, 'seven'); // [7, 'seven']
swag('seven', 7); // ['seven', 7]
```

## 泛型约束

在函数内部使用泛型变量的时候，由于事先不知道它是哪种类型，所以不能随意的操作它的属性和方法。

```tsx
function getLength<T>(arg: T) {
	return arg.length; // 报错
}
```

```tsx
interface Property {
  length: number;
}

function getLength<T extends Property>(arg: T) {
	return arg.length;
}
```

使用了`extends`约束了泛型`T`必须符合接口`Property`的形状，也就是调用的时候也需要包含`length`属性。