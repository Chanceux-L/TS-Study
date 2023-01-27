# 类型断言

## 断言的限制

- 父类可以被断言为子类
- 任何类型都可以被断言为`any`
- `any`可以被断言为任何类型

>问：类型断言有没有什么限制呢？是不是任何一个类型都可以被断言为任何另一个类型？
>
>答：否，并不少任何一个类型都可以被断言为任何另一个类型。

具体来说，若`A`能兼容`B`，那么`A`能够被断言为`B`，`B`也能够被断言为`A`。

```tsx
interface Animal {
  name: string;
}

interface Cat {
  name: string;
  run(): void;
}

function testAnimal(animal: Animal) {
  return (animal as Cat);
}

function testCat(cat: Cat) {
  return (cat as Cat);
}

// 不报错，因为有共同属性（或者方法）：name
```

**双重断言**（不到万不得已，千万别用）

```tsx
interface Cat {
  run(): void;
}

interface Fish {
  swim(): void;
}

function testCat(cat: Cat) {
  return (cat as any as Fish);
}
```

