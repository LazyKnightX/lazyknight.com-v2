---
layout: article
title: WE演示
permalink: /we/sample/
---

# /we/sample

## 触发器参数演示

![trigger_params](/assets/img/we/sample/trigger_params.png)  
(代码: [trigger_params_src.png](/assets/img/we/sample/trigger_params_src.png) 地图: [trigger_params.w3x](/assets/files/we/sample/trigger_params.w3x))

## ZINC operator演示

```jass
//! zinc
library Foo {
  struct fooStruct {
    private unit m_u;
    public method attach(unit u) { m_u = u; }
    public method operator atk() -> real {
      return GetUnitStateSwap(ConvertUnitState(0x12), m_u);
    }
  }

  function onInit() {
    TimerStart(CreateTimer(), 0, false, function() {
      fooStruct f = fooStruct.create();
      unit u = CreateUnit(Player(0), 'hfoo', 0, 0, 0);
      f.attach(u);
      BJDebugMsg("atk: " + R2S(f.atk));
    });
  }
}
//! endzinc
```

进入游戏后输出：`11.00`
