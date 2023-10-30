---
title: 组件内部函数调用this.State时this指向设置的3种方法
date: 2018-08-02 19:05
tags: React
catetory: 学习总结
---

1. 在构造函数中首先声明：

```javascript
constructor(props) {
  super(props);
  this.onClickRestart = this.onClickRestart.bind(this);
  this.state = {
    squares: Array(25).fill(null),
    xIsNext: true,
  };
};
```

2. 使用箭头函数
MSN中关于箭头函数表达式的说明是这样的：

> 箭头函数表达式的语法比函数表达式更短，并且没有自己的 `this` ，`arguments`，`super` 或  `new.target`。这些函数表达式更适用于那些本来需要匿名函数的地方，并且它们不能用作构造函数。

因此，使用箭头函数的函数表达式的 `this` 的指向自动为该函数表达式的上下文：

```javascript
class Board extends Component {
  constructor(props) {
    super(props);
    this.onClickRestart = this.onClickRestart.bind(this);
    this.state = {
      squares: Array(25).fill(null),
      xIsNext: true,
    };
  };
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    })
  }
  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }
  // ...
}
```

在上面的代码中， `renderSquare(i)` 函数在调用 `handleClick(i)` 函数时使用箭头函数，由于上述原因，`handleClick` 函数的 `this` 自动指向的就是其所在的函数作用域的对象，而该函数作用域当前就是 `class Board` 。

3. 直接在函数调用的时候进行绑定：
```javascript
renderSquare(i) {
  return (
    <Square
      value={this.state.squares[i]}
      onClick={this.handleClick.bind(this,i)}
    />
  );
}
```
