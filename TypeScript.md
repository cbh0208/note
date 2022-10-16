# 配置

### 安装

```shell
npm install -g typescript
yarn global add typescript
```



# 类型

### 可选属性

- `?`表示可选

```typescript
function printName(obj: { first: string; last?: string }) {
  // ...
}
// Both OK
printName({ first: "Bob" });
printName({ first: "Alice", last: "Alisson" });
```



### 联合类型

- `|`表示联合

```typescript
function printId(id: number | string) {
  console.log("Your ID is: " + id);
}
// OK
printId(101);
// OK
printId("202");
// Error
printId({ myID: 22342 });
// Argument of type '{ myID: number; }' is not assignable to parameter of type 'string | number'.
// Type '{ myID: number; }' is not assignable to type 'number'.
```



### 类型别名(`type`)

- 用`type`定义
- 不可拓展

```typescript
type Point = {
  x: number;
  y: number;
};
 
// Exactly the same as the earlier example
function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}
 
printCoord({ x: 100, y: 100 });
```



### 接口(`interface`)

- 用`interface`定义
- 可拓展

```typescript
interface Point {
  x: number;
  y: number;
}
 
function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}
 
printCoord({ x: 100, y: 100 });
```



###  类型断言

- 使用类型断言将其指定为一个更具体的类型
- 用`as` 或`<>`


```typescript
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
```

```typescript
const myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");
```

