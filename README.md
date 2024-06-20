# Typecho Plugin Katex
基于[memset0/typecho-plugin-katex](https://github.com/memset0/typecho-plugin-katex)更新并简单修订的KaTeX插件，同时增加使用pjax等策略时的说明。

如果是使用在`footer.php`中增加script启用pjax刷新的策略，则需要在

```js
$(document).on('pjax:end',   function() { $('#preloader').remove(); });//Pjax结束
```

前面增加一行以下内容：

```js
$(document).on('pjax:complete', function() { var tmp = document.getElementsByTagName('katex-inline'); for (var i = 0; i < tmp.length; i++) { var t = tmp[i].innerHTML, e; console.log(katex.render(tmp[i].innerText, tmp[i], {displayMode: false, throwOnError: false})); } tmp = document.getElementsByTagName('katex'); for (var i = 0; i < tmp.length; i++) { var t = tmp[i].innerHTML, e; console.log(katex.render(tmp[i].innerText, tmp[i], {displayMode: true, throwOnError: false})); } });
```

如果使用其他pjax方式，请参照对应说明将以下js内容添加到流程中。

```js
var tmp = document.getElementsByTagName('katex-inline'); for (var i = 0; i < tmp.length; i++) { var t = tmp[i].innerHTML, e; console.log(katex.render(tmp[i].innerText, tmp[i], {displayMode: false, throwOnError: false})); } tmp = document.getElementsByTagName('katex'); for (var i = 0; i < tmp.length; i++) { var t = tmp[i].innerHTML, e; console.log(katex.render(tmp[i].innerText, tmp[i], {displayMode: true, throwOnError: false})); }
```

---
## 以下是memset0的说明
这个插件基于 [zyuzhi](https://github.com/zyuzhi) 的 [MarkdownKatex-typecho](https://github.com/zyuzhi/MarkdownKatex-typecho) 插件修改而来，做了一些微小的改动：

1. 更新 KaTeX 的版本
2. 渲染不再依赖 jQuery

**NOTE：导入时请务必将文件夹名改为 `MarkdownKatex` 再导入！**
