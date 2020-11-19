# Sublime Text


## 删除所有注释

删除源代码中所有注释，步骤如下

1. 将下面的 `Python` 代码保存到 `Packages/User` 目录下（可以通过点击 `Preferences -> Browse Packages` 进入 `Packages` 目录，然后再进入 `User` 目录），并命名为 `remove_comments.py`。

```python

import sublime_plugin


class RemoveCommentsCommand(sublime_plugin.TextCommand):
    def run(self, edit):
        comments = self.view.find_by_selector('comment')
        for region in reversed(comments):
            self.view.erase(edit, region)

```

2、现在可以通过控制台运行这个插件，只需输入下面的命令即可。Windows 可以使用快捷键 Ctrl + \`呼出控制台，OSX 可以使用快捷键 Control + \` 呼出控制台，也可以点击 `View -> Show Console` 呼出控制台

``` python

view.run_command('remove_comments')

```

3. 设置快捷键，可以将插件绑定为快捷键，方便之后的调用，点击 `Preferences -> Key Bindings` 并写入下面代码，即可使用

``` python
{ "keys": ["ctrl+alt+shift+c"], "command": "remove_comments"}
```