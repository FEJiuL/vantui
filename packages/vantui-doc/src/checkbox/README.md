# Checkbox 复选框

### 介绍

在一组备选项中进行多选。

### 引入

在 Taro 文件中引入组件

```js
import { Checkbox } from "vantui";
import { CheckboxGroup } from "vantui"; 
```

## 代码演示

### 基础用法

通过`value`绑定复选框的勾选状态。

```jsx
<View>
  <Checkbox
    value={ this.checked }
    onChange={ this.onChange }
  >
    复选框
  </Checkbox>
</View>
 
```

```js
this.state = {
  checked: true
};

function onChange(event) {
  this.setState({
    checked: event.detail
  });
} 
```

### 禁用状态

通过设置`disabled`属性可以禁用复选框。

```jsx
<View>
  <Checkbox
    disabled={ true }
    value={ this.state.checked }
    onChange={ this.onChange }
  >
    复选框
  </Checkbox>
</View>
 
```

### 自定义形状

将`shape`属性设置为`square`，复选框的形状会变成方形。

```jsx
<View>
  <Checkbox
    value={ this.state.checked }
    shape="square"
    onChange={ this.onChange }
  >
    复选框
  </Checkbox>
</View>
 
```

### 自定义颜色

通过`checkedColor`属性可以自定义选中状态下的图标颜色。

```jsx
<View>
  <Checkbox
    value={ this.state.checked }
    checkedColor="#07c160"
    onChange={ this.onChange }
  >
    复选框
  </Checkbox>
</View>
 
```

### 自定义大小

通过`iconSize`属性可以自定义图标的大小。

```jsx
<View>
  <Checkbox
    value={ this.state.checked }
    iconSize="25px"
  >
    复选框
  </Checkbox>
</View>
 
```

### 自定义图标

通过 icon 插槽自定义图标。

```jsx
<View>
  <Checkbox
    value={ this.state.checked }
    onChange={ this.onChange }
    renderIcon={ (
      <Image
        src={ this.state.checked ? this.state.activeIcon : this.state.inactiveIcon }
      />
    ) }
  >
    自定义图标
  </Checkbox>
</View>
 
```

```js
this.state = {
  checked: true,
  activeIcon: '//img.yzcdn.cn/iconActive.png',
  inactiveIcon: '//img.yzcdn.cn/iconNormal.png'
};

function onChange(event) {
  this.setState({
    checked: event.detail
  });
} 
```

### 禁用文本点击

通过设置`labelDisabled`属性可以禁用复选框文本点击。

```jsx
<View>
  <Checkbox
    value={ this.state.checked }
    labelDisabled={ true }
  >
    复选框
  </Checkbox>
</View>
 
```

### 复选框组

需要与`vanCheckboxGroup`一起使用，选中值是一个数组，通过`value`绑定在`vanCheckboxGroup`上，数组中的项即为选中的`Checkbox`的`name`属性设置的值。

```jsx
<View>
  <CheckboxGroup
    value={ this.state.result }
    onChange={ this.onChange }
  >
    <Checkbox name="a">
      复选框 a
    </Checkbox>
    <Checkbox name="b">
      复选框 b
    </Checkbox>
    <Checkbox name="c">
      复选框 c
    </Checkbox>
  </CheckboxGroup>
</View>
 
```

```js
this.state = {
  result: ['a', 'b']
};

function onChange(event) {
  this.setState({
    result: event.detail
  });
} 
```

### 限制最大可选数

```jsx
<View>
  <CheckboxGroup
    value={ this.state.result }
    onChange={ this.onChange }
    max={ 2 }
  >
    <Checkbox name="a">
      复选框 a
    </Checkbox>
    <Checkbox name="b">
      复选框 b
    </Checkbox>
    <Checkbox name="c">
      复选框 c
    </Checkbox>
  </CheckboxGroup>
</View>
 
```

### 搭配单元格组件使用

此时你需要再引入`Cell`和`CellGroup`组件，并通过 checkbox 的 toggle 方法手动触发切换。

```jsx
<View>
  <CheckboxGroup
    value={ this.state.result }
    onChange={ this.onChange }
  >
    <CellGroup>
      { this.state.list.map((item, index) => (
          <Cell
            key={index}
            title={ `复选框 ${ item }` }
            valueClass="valueClass"
            clickable={ true }
            dataIndex={ index }
            onClick={ this.toggle }
          >
            <Checkbox
              class={ `checkboxes-${ index }` }
              name={ item }
            />
          </Cell>
        
        )) }
    </CellGroup>
  </CheckboxGroup>
</View>
 
```

```js
this.state = {
  list: ['a', 'b', 'c'],
  result: ['a', 'b']
};

function onChange(event) {
  this.setState({
    result: event.detail
  });
}

function toggle(event) {
  const {
    index
  } = event.currentTarget.dataset;
  const checkbox = this.selectComponent(`.checkboxes-${index}`);
  checkbox.toggle();
}

function noop() {} 
```

```css
.valueClass {
  flex: none !important;
}
```
### TS信息
```ts 
import { ComponentClass, ReactNode } from 'react'
import { ITouchEvent, StandardProps } from '@tarojs/components'

export interface CheckboxProps extends StandardProps {
  name?: string
  value?: boolean
  disabled?: boolean
  checkedColor?: string
  labelPosition?: string
  labelDisabled?: boolean
  shape?: 'round' | 'square'
  iconSize?: string | number
  children?: ReactNode
  renderIcon?: ReactNode
  onChange?: (event: ITouchEvent) => any
}

declare const Checkbox: ComponentClass<CheckboxProps>

export { Checkbox }
```