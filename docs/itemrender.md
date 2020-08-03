# ItemRender使用教程

ItemRender原作者为[Kobata](https://github.com/Kobata)，MCMOD百科现使用的是专门定制的修改版本。修改版本目前支持1.7.10至1.14.4版本，最主要的新加功能为批量导出json。  
下载请前往：[百科下载](https://www.mcmod.cn/download/1166.html)

## 基础功能

### 导出方块/物品

首先，请进入设置查看导出方块/物品的按键。如下图所示：

![block key](https://cloud.githubusercontent.com/assets/5229241/12267820/e92cab28-b984-11e5-8c2b-1f954742bb34.png)

默认的按键为 `[` 和 `]`。如果按键冲突了请改为其它的按键。括号后面的数字代表导出图片的分辨率。

找到按键之后，请进入游戏，并将你需要渲染的物品拿在手上，分别按下先前查看的按键(默认 `[` 和 `]`)，注意按下之后如果没开Toggle Render游戏内将不会有任何反应，但其实已经完成了。

渲染完毕之后，请进入 `.minecraft/rendered/` 文件夹(`.minecraft/` 为游戏目录)，如果没出问题你将会看到渲染出的图片已经保存在文件夹里了。带有 `_grid` 的文件为小图标，默认为32x，无后缀名的为大图标，默认为128x。

在添加条目时，图标在拓展信息选项卡内，选择导出的文件上传即可：

![upload](https://cloud.githubusercontent.com/assets/5229241/12271426/00452bd0-b996-11e5-86e4-d84137fa7f47.png)

如果你发现导出的图片中方块/物品超过图片的大小，请看下面高级功能部分的指令部分。

>如果安装了Not Enough Items(NEI)，你也可以使用NEI的Item Panel批量导出物品图标。
>
>进入方法为：Options->Tools->Data Dumps->Item Panel->PNG
>如下图：
>![nei](https://cloud.githubusercontent.com/assets/5229241/12268873/aaff74fc-b989-11e5-8517-c47b4eb511dc.png)
>
>点击左边的32x32按钮可以切换分辨率。导出的文件会输出到 `.minecraft/itempanel_icons/` 文件夹。

### 导出生物

请进入设置查看导出生物的按键。如下图所示：

![entity key](https://cloud.githubusercontent.com/assets/5229241/12269034/5af3ccfa-b98a-11e5-8a66-94e3faca35a9.png)

默认的按键为 `;` 和 `'`。如果按键冲突了请改为其它的按键。括号后面的数字代表导出图片的分辨率。

查看好按键之后，进入游戏，并寻找或生成一只需要渲染的生物。请将鼠标指向生物，并分别按下先前查看的按键(默认 `;` 和 `'`)。按下后游戏内不会有反应，请到 `.minecraft/rendered/` 文件夹内寻找渲染好的文件。带有 `_grid` 的文件为小图标，默认为128x，无后缀名的为大图标，默认为512x。

如果你发现导出的图片中生物超过图片的大小，请看下面高级功能部分的指令部分。

### 批量导出

首先，请保证客户端内的mod数量越少越好，最好只装要导出的mod和ItemRender，否则导出的时间会非常长，甚至导致导出失败。

接下来，进入设置查看批量导出的按键。如下图所示：

![export key](https://cloud.githubusercontent.com/assets/5229241/12269284/a08db28e-b98b-11e5-9c78-b8ff771b8eed.png)

默认的按键为 `I`。如果按键冲突了请改为其它的按键。

查看好按键之后，请进入游戏，直接按下刚才查看的按键(默认 `I`)。接下来客户端应该会未响应一会，请不要操作客户端，耐心等待。一旦客户端恢复响应，那么导出就完成了。请到`.minecraft/export/`文件夹中找导出的文件。文件应该类似于下图：

![json](https://cloud.githubusercontent.com/assets/5229241/12271450/1a6bf30e-b996-11e5-8cca-6a55dd01c3d3.png)

导出的文件以modid.json的形式命名，内容包括mod内所有物品的：中文名，英文名，最大耐久，最大堆叠数量，大图标，小图标(储存为Base64字符串)。**如果你想批量导入物品，请将JSON文件交给编辑员。**

嘛，导出后游戏的确会有副作用，比如说语言换了什么的，不用这么在意细节是吧_(:з」∠)_
<br>
<br>
注意ItemRender导出的JSON文件和NEI在Item Panel导出的JSON是完全不同的！

ItemRender导出的JSON文件为百科定制，只有ItemRender的JSON才能正常导入。

而NEI的JSON文件为物品的NBT数据(具体见：[http://www.mcmod.cn/post/189.html](http://www.mcmod.cn/post/189.html))。

## 高级功能

### 缩放大小

ItemRender添加了一条指令 `/itemrender scale [value]`以解决物品/生物导出的图标不完整的问题，其中 `[value]` 为缩放因子，范围是0.0-2.0。

使用时请进入游戏，并在渲染之前输入指令，比如 `/itemrender scale 0.8`。注意这条指令同时影响生物和方块/物品的渲染大小，并且也会影响批量导出时物品图标的大小。所以在批量导出如无特殊情况请保证缩放因子调为1.0。

### 显示上次渲染结果

先去按键设置查看Toggle Render的键位，默认为 `O`。如下图：

![toggle key](https://cloud.githubusercontent.com/assets/5229241/12271455/2aa72ac2-b996-11e5-9cc0-e3397c30eab7.png)

使用时请进入游戏，在渲染过方块/物品之后按下按键(默认 `O`)，你会在游戏窗口左上角看到上一次渲染的方块/物品，再次按下按键则关闭显示。显示效果如下图：

![toggle](https://cloud.githubusercontent.com/assets/5229241/12271464/375f0c80-b996-11e5-91e5-8eff3287419e.png)

### 导出黑名单

由于mod中有些物品导出时会导致崩溃(比如说神秘5的某一个Research Note)，ItemRender添加了导出黑名单功能。如果想要启用，请在主菜单中点击Mods->ItemRender->Config->BlackList。

点击加号添加条目，条目的格式为 `unlocalizedName@metadata`。如果你不知道条目该怎么写，把DebugMode打开，崩溃了之后看log(客户端的)，最后正在处理的那个就是出问题的物品。

### 导出玩家

这个功能和导出生物一样，不过导出的对象是玩家自己。按键设置里查看按键，默认为 `P`：

![player key](https://cloud.githubusercontent.com/assets/5229241/12271475/471bdca2-b996-11e5-9085-73286ba7d6a6.png)

进入游戏，按下按键(默认 `P`)，渲染之后请到 `.minecraft/rendered/` 文件夹内寻找 `player.png`。

## 设置

设置的所有内容都可以在游戏内修改，游戏内设置进入方法为Mods->ItemRender->Config。

- **BlackList**：导出黑名单，推荐在游戏内设置
- **DebugMode**：调试模式，主要是为了判断导出出错的物品用的
- **ExportVanillaItems**：是否导出原版物品，原版物品在导出时会占用很长时间，如果不需要导出原版物品的话请设置为false
- **RenderBlockGrid**：方块/物品渲染小图标分辨率
- **RenderBlockMain**：方块/物品渲染大图标分辨率
- **RenderEntityGrid**：生物渲染小图标分辨率
- **RenderEntityMain**：生物渲染大图标分辨率
- **RenderPlayer**：玩家渲染分辨率

## 错误

如果在游戏中按键无反应，且在修改按键界面看到 `OpenGL Error` 的提示，那说明你的电脑不支持OpenGL 3.2及以上版本，请考虑升级显卡驱动或者更换显卡。
