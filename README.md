# 考研题库 · kaoyan-bank

这是「做题台」和「作战板」用的题库仓库，给一个人用。

## 结构

```
bank/
  index.json     清单：有多少题、分几个文件
  math.json      数学 105 题（55 道真题选择 + 自编）
  408.json       408 四科 118 题
  english.json   英语 26 题
papers/
  math1-1987.md … math1-2025.md   数学一真题原文（markdown）
```

## 每题的结构

```json
{"id":"m1","sub":"数学","ch":"行列式","lvl":1,"stem":"题干",
 "opts":["A 项","B 项","C 项","D 项"],"ans":2,"sol":"解析"}
```

- 填空/计算题没有 `opts`，改写成 `"type":"fill"`，`ans` 是文字答案（可加 `alts` 备选）。
- `ans` 对选择题来说是正确项下标（0 = A）。

## 页面怎么用它

`做题.html` 启动时先 fetch
`https://cdn.jsdelivr.net/gh/black-whileman/kaoyan-bank@main/bank/index.json`，
拿到清单再拉各个 json，合并进内置题库（同 id 去重）。
拉不到（断网 / jsDelivr 抽风）就退回内置那 249 题，照常能用。

## 改题流程

1. 改 `bank/*.json`
2. `git add -A && git commit -m "加题" && git push`
3. 所有设备刷新页面就是新题库（jsDelivr 有几分钟缓存，可在页面点「重新同步」）

## 版权

`papers/` 里的真题来自公开仓库 TsekaLuk/Kaoyan-Math1-Papers，仅个人复习用，不再分发。
`bank/` 里的题目为自编或据真题改写，用于练习。
