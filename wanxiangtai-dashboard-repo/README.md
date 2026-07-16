# 万相台投放数据看板

单文件静态看板(HTML + CSS + JS,图表用 Chart.js CDN),内部用纯JS路由做多页面切换(不依赖URL hash跳转),无需构建工具,可直接打开或部署到 GitHub Pages。

## 目录结构

```
.
├── index.html          # 看板主文件(9个页面全部在这一个文件里,内部切换)
├── lenovo-logo.png      # 侧边栏logo(已抠透明背景)
└── .nojekyll            # 告诉GitHub Pages不要用Jekyll处理这些文件
```

## 页面清单

- 总览
- 数据接入状态
- 历史数据查询(T-1)
- 品类明细
- 主体明细
- 全景视图
- 渠道费率
- 知识库 / 规则库V1.0
- 基础策略提示(含自动化预览)

## 本地预览

直接双击打开 `index.html`,或者在这个目录下起一个静态服务器:

```
python3 -m http.server 8000
```

然后访问 http://localhost:8000

## 部署到 GitHub Pages

1. 把这个文件夹的内容 push 到你的 GitHub 仓库(`index.html` 和 `lenovo-logo.png` 必须在同一层)
2. 仓库 `Settings -> Pages`
3. `Build and deployment` 选择 `Deploy from a branch`,选你 push 的分支和根目录 `/`
4. 保存后等一两分钟,访问 `https://<你的用户名>.github.io/<仓库名>/` 即可看到看板

## 数据说明(重要,更新时留意)

看板里大部分数据是**演示数据**,不是真实自动化产出,页面上已经标注清楚:

- 历史数据查询(T-1)、主体明细(100条来自你贴的真实数据)、全景视图:结构对应真实流水线字段,方便以后直接换真实JSON
- 渠道费率里的淘客/热浪:演示值,待确认真实数据来源
- 知识库/规则库V1.0:分层阈值部分为真实数据,缺失的品类如实标"—",不编造
- 数据接入状态页:万相台实时采集和瓴羊one T-1数据流都还没真接上,现在是占位展示

等真实API/数据库接入后,把对应的 `historyRecords`、`subjectsData`、`categoryThresholds` 等JS常量换成从接口取回的数据即可,页面渲染逻辑不用改。
