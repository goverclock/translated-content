---
title: feBlend
slug: Web/SVG/Element/feBlend
tags:
  - SVG
  - SVG 滤镜
  - 元素
  - 需要兼容性表
translation_of: Web/SVG/Element/feBlend
---
{{SVGRef}}

`feBlend`滤镜把两个对象组合在一起，使它们受特定的混合模式控制。这类似于图像编辑软件中混合两个图层。该模式由属性{{ SVGAttr("mode") }}定义。

## 用法

{{svginfo}}

## 示例

## 属性

### 全局属性

- [核心属性](/en/SVG/Attribute#Core) »
- [外观属性](/en/SVG/Attribute#Presentation) »
- [滤镜属性属性](/en/SVG/Attribute#Filter) »
- {{ SVGAttr("class") }}
- {{ SVGAttr("style") }}

### 专有属性

- {{ SVGAttr("in") }}
- {{ SVGAttr("in2") }}
- {{ SVGAttr("mode") }}

## DOM 接口

该元素实现了[`SVGFEBlendElement`](/en/DOM/SVGFEBlendElement)接口。

## 示例

### SVG

```plain
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink">
  <defs>
    <filter id="spotlight">
      <feFlood result="floodFill" x="0" y="0" width="100%" height="100%"
          flood-color="green" flood-opacity="1"/>
      <feBlend in="SourceGraphic" in2="floodFill" mode="multiply"/>
    </filter>
  </defs>

  <image xlink:href="/files/6457/mdn_logo_only_color.png"
      x="10%" y="10%" width="80%" height="80%"
      style="filter:url(#spotlight);"/>
</svg>
```

### Result

{{EmbedLiveSample("Example", 200, 200)}}

## 参见

- {{ SVGElement("filter") }}
- {{ SVGElement("animate") }}
- {{ SVGElement("set") }}
- {{ SVGElement("feColorMatrix") }}
- {{ SVGElement("feComponentTransfer") }}
- {{ SVGElement("feComposite") }}
- {{ SVGElement("feConvolveMatrix") }}
- {{ SVGElement("feDiffuseLighting") }}
- {{ SVGElement("feDisplacementMap") }}
- {{ SVGElement("feFlood") }}
- {{ SVGElement("feGaussianBlur") }}
- {{ SVGElement("feImage") }}
- {{ SVGElement("feMerge") }}
- {{ SVGElement("feMorphology") }}
- {{ SVGElement("feOffset") }}
- {{ SVGElement("feSpecularLighting") }}
- {{ SVGElement("feTile") }}
- {{ SVGElement("feTurbulence") }}
- [SVG tutorial: Filter effects](/en/SVG/Tutorial/Filter_effects)
