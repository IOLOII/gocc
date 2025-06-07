# gocc

一个用于检测 go 项目 静态代码质量的工具, 集成多款开源扫描工具并支持可视化 html 输出，支持 圈复杂度，代码重复率,安全漏洞 等多个维度的检查。

### Features

- 🚀 更快的执行速度，完全基于本地计算
- 🚀 集成 gocyclo, dupl, govulncheck 等主流开源工具
- 🚀 支持 多种输出选项 html(还未支持), console 和 json
- 🚀 丰富的可选配置

### 当前版本支持

| 特性      | 支持情况 |
|---------|----|
| 圈复杂度    | ✅  |
| 单元测试覆盖率 | ✅  |
| 大文件     | ✅  |
| 长函数     | ✅  |
| 安全漏洞    | ✅  |
| 代码重复率   | ✅  |
| 敏感词检测   | ❌  |
| 语法规范    |  ✅ |


## 使用说明

 **install**

 ```bash
 go install github.com/hanshuaikang/gocc@latest
 ```

 **usage**

```bash
gocc run --config ./gocc.yaml .

## or

gocc run --config ./gocc.yaml ./files file1.go file2.go
```

## 配置文件示例

在项目根目录下新建 gocc.yaml gocc 运行时会自动检查当前根目录下是否存在名为 gocc.yaml 的配置文件
如果存在，则自动加载该配置。

```yaml
reportType: "console"
ignoreError: false
linters:
  enable:
      - bigFile
      - longFunc
      - copyCheck
      - cyclo
      - unittest
      - security
      - syntax
linters-settings:
  bigFile:
    maxLines: 800
  longFunc:
    maxLength: 80
  cyclo:
    ignoreRegx: "_test"
  security:
    env:
      - GOVERSION=go1.19
  copyCheck:
    threshold: 50
    ignoreRegx: "_test"
```

## Thanks

- [@chenjiandongx](https://github.com/chenjiandongx)
