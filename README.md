# taro-antv-f2


目前支持: 微信小程序

根据 taro-f2@2.2.0 修改 https://www.npmjs.com/package/taro-f2/v/2.2.0

F2图表具体使用方法请参考: https://github.com/antvis/f2

> 直接克隆代码 可查阅示例


## 安装

```
$ yarn add taro-antv-f2 @antv/f2
```

## 使用指南

在 Taro 文件中引入组件
```jsx harmony

import { F2Canvas } from 'taro-antv-f2'

```

## 示例

```jsx harmony
import Taro from '@tarojs/taro'
import React, { Component } from 'react'
import { View } from '@tarojs/components'
import F2Canvas from '@components/f2-canvas'
import './index.scss'

export default class Line extends Component {

  initChart(F2, config){
    const chart = new F2.Chart(config);
    const data = [
      { value: 63.4, city: 'New York', date: '2011-10-01' },
      { value: 62.7, city: 'Alaska', date: '2011-10-01' },
      { value: 72.2, city: 'Austin', date: '2011-10-01' },
      { value: 58, city: 'New York', date: '2011-10-02' },
      { value: 59.9, city: 'Alaska', date: '2011-10-02' },
      { value: 67.7, city: 'Austin', date: '2011-10-02' },
      { value: 53.3, city: 'New York', date: '2011-10-03' },
      { value: 59.1, city: 'Alaska', date: '2011-10-03' },
      { value: 69.4, city: 'Austin', date: '2011-10-03' },
    ];
    chart.source(data, {
      date: {
        range: [0, 1],
        type: 'timeCat',
        mask: 'MM-DD'
      },
      value: {
        max: 300,
        tickCount: 4
      }
    });
    chart.area().position('date*value').color('city').adjust('stack');
    chart.line().position('date*value').color('city').adjust('stack');
    chart.render();
    // 注意：需要把chart return 出来
    return chart;
  }

  render () {
    return (
      <View style='width:100%;height:600px'>
        <F2Canvas onInit={this.initChart.bind(this)}></F2Canvas>
      </View>
    )
  }
}
```



