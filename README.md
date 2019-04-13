## 介绍

tinymce 图片上传插件

## 源码 

 地址：https://github.com/bowens-h/tinymce-imageupload

fork：https://github.com/x-shadow-x/tinymce-imageupload

##  与原包的差异

1. 增加上传图片时的 loading 效果

## 安装

1. 安装包

```bash
$ npm i tinymce-uploadimages
```

2. 在 plugins 与 toolbar 中增加 imageupload
3. 在 根目录下添加图标 image/images.png （可到 https://www.iconfont.cn/ 中搜索 images 获取）

## 例子

```js
import tinymce from 'tinymce'
import 'tinymce-imageupload'

tinymce.init({
    selector: '#tinymceEditer',
    height: 500,
    branding: false,
    elementpath: false,
    language_url: '/static/tinymce/langs/zh_CN.js', // 具体路径视项目结构而定
    skin_url: '/static/tinymce/skins/lightgray', // 具体路径视项目结构而定
    theme_url: '/static/tinymce/themes/modern/theme.js', // 具体路径视项目结构而定
    menubar: 'edit insert view format table tools',
    convert_urls: false,
    plugins: 'imageupload', // 注意引入的组件时~需要去掉前面的tinymce-前缀
    toolbar: 'imageupload', // 注意引入的组件时~需要去掉前面的tinymce-前缀
    autosave_interval: '20s',
    image_advtab: true,
    imageupload_url: '//localhost:3000', // 接收图片的后端地址
    imageupload_converCb: res => {
        // 根据后端返回的数据，转换成符合插件要求的数据结构
        return {
            error: res.data.error,
            pathList: res.data.data.pathList
        }
    },
    table_default_styles: {
        width: '100%',
        borderCollapse: 'collapse'
    }
})
```

##
