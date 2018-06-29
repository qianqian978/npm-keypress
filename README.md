# Digital-Keyboard npm包开发

[![Example](https://github.com/qianqian978/react-keypress/blob/master/gif.gif)]

## Type

<table>
  <tbody>
    <tr>
      <td align="center" valign="middle">
        <img width="240px" src="https://github.com/qianqian978/react-keypress/blob/master/pic1.jpg">
        <p>decimal</p>
      </td>
      <td align="center" valign="middle">
        <img width="240px" src="https://github.com/qianqian978/react-keypress/blob/master/pic2.jpg">
        <p>integer/phone</p>
      </td>
      <td align="center" valign="middle">
        <img width="240px" src="https://github.com/qianqian978/react-keypress/blob/master/pic3.jpg">
        <p>idcard</p>
      </td>
    </tr>
  </tbody>
</table>

## PropTypes

| Property        | Type     | Default      | Description           |
| :-------------- | :------- | :----------- | :-------------------- |
| el | DOM |  | parent node  | 
| type  | String   | decimal | decimal，integer，phone，idcard |
| inputValue    | Function   |  |  return keyboard value      |

## Getting Started

### Install

```shell
npm install digital-keyboard --save-dev
```

### Usage Example

- **Native JavaScript**

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Digital Keyboard</title>
</head>
<body>
  <div id="values"></div>
  <div id="app"></div>
  <script src="./digitalKeyboard.js"></script>
</body>
</html>
```

```javascript
//digitalKeyboard.js
import DigitalKeyboard from 'digital-keyboard';

function inputValue(value){
  console.log(value); //DigitalKeyboard return value
  document.querySelector('#values').innerHTML = value;
}

new DigitalKeyboard(
    {
        el: document.querySelector('#app'), 
        type: 'idcard', 
        inputValue: inputValue
    }
);
```

- **React**

```jsx
import React from 'react';
import DigitalKeyboard from "digital-keyboard";
class KeyboardPage extends React.Component {

  constructor(){
    super();

    this.inputValue = this.inputValue.bind(this);
    this._renderKeyboard = this._renderKeyboard.bind(this);
  }

  componentDidMount(){
    this._renderKeyboard();
  }
    
  inputValue(value){
    console.log(value); //DigitalKeyboard return value
  }

  _renderKeyboard(){
    return new DigitalKeyboard (
      {
        el: this.refs.digitalKeyboard,
        type: 'number',
        inputValue: this.inputValue
      }
    );
  }

  render(){
    return (
      <div ref='digitalKeyboard'></div>
    )
  }
}

export default KeyboardPage;
```

- **Vue**

```js
<template>
  <div></div>
</template>
<script>
import DigitalKeyboard from "digital-keyboard";
export default {
  mounted () {
    this._renderDigitalKeyboard();
  },
  methods: () {
    _renderDigitalKeyboard() {
    	return new DigitalKeyboard (
          {
            el: this.$el,
            type: 'number',
            inputValue: this.inputValue
          }
        );
    },
     
    inputValue(value) {
      console.log(value); //DigitalKeyboard return value
    }
  }
}
</script>
```

