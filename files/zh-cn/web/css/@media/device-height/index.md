---
title: device-height
slug: Web/CSS/@media/device-height
translation_of: Web/CSS/@media/device-height
---
{{cssref}} {{deprecated_header}}

**`device-height`** [CSS](/zh-CN/docs/CSS) [media feature](/zh-CN/docs/Web/CSS/Media_Queries/Using_media_queries#Media_features) 可以用来测试设备的渲染高度。注意，该条媒体查询将会在 媒体查询 level4（目前处于候选草案）中废弃

## 语法

`device-height` feature is specified as a {{cssxref("&lt;length&gt;")}} value. It is a range feature, meaning that you can also use the prefixed **`min-device-height`** and **`max-device-height`** variants to query minimum and maximum values, respectively.

## 例子

在高度低于 800px 时加载指定样式

```html
<link rel="stylesheet" media="screen and (max-device-height: 799px)" href="http://foo.bar.com/short-styles.css" />
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
