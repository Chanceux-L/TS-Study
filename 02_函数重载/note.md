# 函数重载

重载允许一个函数接受不同的数量或类型的参数时，作出不同的处理。方法名相同，参数列表和类型不同。

```tsx
function reverse(x: number | string): number | string | void {
  switch (typeof x) {
    case 'number':
      return Number(x.toString().split('').reverse().join(''));
    case 'string':
      return x.split('').reverse().join('');
  }
}
```

**缺点：不能精确表达，输入数字时输出为数字，输入字符串时输出也应该为字符串**

这时，可以利用重载定义多个`reverse`的函数类型

```tsx
function reverse(x: number): number;
function reverse(x: string): string;
function reverse(x: number | string): number | string | void {
  switch (typeof x) {
    case 'number':
      return Number(x.toString().split('').reverse().join(''));
    case 'string':
      return x.split('').reverse().join('');
  }
}
```

注意：TS会优先从最前面的函数定义开始匹配，所以多个函数定义如果有包含关系，需要优先把精确的定义写在前面。