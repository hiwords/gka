
<p align="center">
  <a href ="https://github.com/joeyguo/gka"><img alt="gka" src="https://user-images.githubusercontent.com/10385585/27863888-bb5e4826-61be-11e7-8994-4b19bb49bb22.png"></a>
</p>
<p align="center">
简单的、高效的帧动画生成工具
</p>
<p align="center">
<a href="https://www.npmjs.org/package/gka"><img src="https://img.shields.io/npm/v/gka.svg?style=flat"></a>
<a href="https://github.com/joeyguo/gka#license"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
</p>

--- 

[gka](https://github.com/joeyguo/gka) 是一款简单的、高效的帧动画生成工具。

通过对图片集进行处理，一键式生成序列帧动画文件，并内置相关优化。

* **一键式 :**  图片文件批量序列化重命名，生成帧动画文件，支持预览
* **性能佳 :**  支持`合图模式`✓，`相同帧图片复用`✓，`图片空白裁剪`✓，`图片压缩`✓

![preview](https://cloud.githubusercontent.com/assets/10385585/24502038/ac4bd9f2-157e-11e7-87e0-a9a44aaffafa.gif)

# Install

```sh
$ sudo npm install -g gka
```

# Usage

### `gka <dir> [options]`

```
-d, --dir <string>            -d  图片文件夹地址

-u, --unique [boolean]        -u  开启相同帧图片复用 默认 true
-c, --crop                    -c  开启空白裁剪模式
-s, --sprites                 -s  开启合图模式
-m, --mini                    -m  开启图片压缩

-p, --prefix [string]         -p  重命名前缀 默认 prefix-
-f, --frameduration <number>  -f  每帧时长 默认 0.04

-t, --template [string]       -t  生成动画文件模板 默认 px

-i, --info                    -i  输出信息文件

-a, --algorithm <string>      -a  合图布局模式 默认 binary-tree，可选 top-down | left-right ..
```


```sh
# 帧动画生成 - 普通模式

$ gka <imageDir>
```

```sh
# 帧动画生成 - 合图模式[-s] + 图片压缩[-m]

$ gka <imageDir> -sm
```

```sh
# 帧动画生成 - 裁剪模式

$ gka <imageDir> -c
```

```sh
# 压缩图片

$ gka <imageDir> -m [-u false -t flase]
```

# Examples

### 生成帧动画 &middot; `普通模式`

1.示例参数： 

- 图片目录：E:\gka-test\img
- 图片名前缀：prefix-

2.命令

```sh
# gka [-d] <imageDirPath> -p [prefix] 

$ gka E:\gka-test\img -p prefix-
```

3.结果： 
<table>
    <thead>
        <tr><th>Before</th><th>After</th></tr>
    </thead>
    <tbody>
        <tr>
            <td><pre><code>
./img
├── 害羞_00000.png
├── 害羞_00001.png
├── 害羞_00002.png
├── 害羞_00003.png
├── 害羞_00004.png
└── ...
</code></pre></td>
<td><pre><code>
./img-gka
└── gka.html
└── prefix-gka.css
└── img
    ├── prefix-1.png
    ├── prefix-2.png
    ├── prefix-3.png
    ├── prefix-4.png
    └── ...
</code></pre></td>
        </tr>
    </tbody>
</table>

### 生成帧动画 &middot; `合图模式`

1.示例参数： 

- 图片目录：E:\gka-test\img
- 图片名前缀：prefix-

2.命令

```sh
# gka [-d] <imageDirPath> -s -p [prefix]

$ gka E:\gka-test\img -s -p prefix-
```

3.结果： 
<table>
    <thead>
        <tr><th>Before</th><th>After</th></tr>
    </thead>
    <tbody>
        <tr>
            <td><pre><code>
./img
├── 害羞_00000.png
├── 害羞_00001.png
├── 害羞_00002.png
├── 害羞_00003.png
├── 害羞_00004.png
└── ...
</code></pre></td>
<td><pre><code> 
./img-gka-sprites
└── img
    └── prefix-sprites.png
└── gka.html
└── prefix-gka.css
</code></pre></td>
        </tr>
    </tbody>
</table>

## 图片压缩

1.示例参数： 

- 图片目录：E:\gka-test\img

2.命令
```sh
# gka <imageDirPath> -m [-u false -t flase]

$ gka E:\gka-test\img -m
```

# Welcome

* 欢迎 Pull requests、Issues 一般在24小时内处理
* 讨论与咨询请+QQ 3201590286  :D

# License

[MIT](./LICENSE) 

Copyright (c) 2017 - present, joeyguo

# Log

- v1.0.x 重命名图片文件、 生成 keyframe animation css 动画、自动化合图、自动化图片压缩、效果预览
- v1.1.0 相同帧图片复用
- v1.4.5 支持输出信息文件、合图布局参数
- v1.4.6 增加图片预加载
- v2.0.0 增加图片裁剪模式、暴露图片去重开关、增加模板选择、优化图片信息文件
