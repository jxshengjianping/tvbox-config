# tvbox-config（小苹果多仓·自建镜像）

把“小苹果流浪版 5.0”内置的多仓配置镜像到自己的 GitHub 仓库，用于 TVBox 类 App 的「配置」输入框。

## 多仓地址（上传后填这个）

```
https://gitee.com/jxshengjianping/tvbox-config/raw/master/line.json
```

国内 raw 域名不稳时的备用（jsDelivr 走 CDN）：

```
https://cdn.jsdelivr.net/gh/jxshengjianping/tvbox-config@main/line.json
```

## 目录结构

```
line.json            多仓清单（urls 数组，6 条线路）
configs/*.json       6 条线路的单仓配置（spider 已全部指向本仓库）
spider/*.jar|*.png   各线路解析器（spider.jar）
assets/*             配置里引用的 js/json/txt/png 等相对资源
```

## 已镜像的线路

| 线路 | 配置文件 | 站点数 |
|---|---|---|
| 🍎小苹果┃主线路 | configs/01_main.json | 39 |
| 🍎小苹果┃王二小线 | configs/02_wex.json | 100 |
| 🍎小苹果┃摸鱼线路 | configs/03_fish.json | 111 |
| 🍎小苹果┃真心线路 | configs/07_zhenxin.json | 74 |
| 🍎小苹果┃东篱线路 | configs/09_dongli.json | 98 |
| 🍎小苹果┃空空4K线路 | configs/12_kong4k.json | ~ |

## 未镜像的线路及原因

| 原线路 | 原因 |
|---|---|
| 饭太硬 | 原地址返回 HTML 页面（站点已挂） |
| 小米 | 返回十六进制加密串，需 App 端解密，无法直接使用 |
| 肥猫 / 虎斑 / 嗷呜 | 中文域名，DNS 解析失败（原本就不可用） |
| 俊佬 | GitLab 返回登录页（仓库已私有） |

## 已知残留外链（不影响使用）

- `configs/12_kong4k.json` 里两条站点 jar 仍指向 `gitee.com/arlen29/...`：gitee 对服务器 IP 返回 423，拉不下来；这两个 jar 属于站点提供方，不是原作者仓库，家用网络一般可直连。
- `configs/07_zhenxin.json` 里部分 `./lib/*` 资源原站已 404，已改写成原站绝对地址，行为与原配置一致。

## 更新方式

原作者的 line.json 变化时，重新抓取并重建即可（本仓库脚本在本地，不在仓库内）。
