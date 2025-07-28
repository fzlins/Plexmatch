# Plexmatch

[![English](https://img.shields.io/badge/docs-English-blue)](../README.md) [![简体中文](https://img.shields.io/badge/docs-简体中文-yellow)](./README.zh-CN.md)

一个用于为 Plex 媒体服务器生成 `.plexmatch` 文件的 Python 工具，帮助正确匹配具有复杂文件名的视频文件。

## 功能特性

- 自动扫描指定目录中的视频文件
- 支持多种视频格式（mp4, mkv, avi, mov 等）
- 从文件名中提取剧集编号
- 生成 Plex 兼容的 `.plexmatch` 文件
- 支持按顺序匹配模式
- 支持自定义季数设置

## 安装要求

```bash
pip install natsort
```

## 使用方法

### 基本用法

```bash
python -m Plexmatch -d "C:\your\video\directory"
```

### 网络路径

```bash
python -m Plexmatch -d "//Network\directory"
```

### 命令行参数

- `-d, --directory`: 指定视频文件目录（必需）
- `-o, --order`: 仅选择按顺序排列的文件
- `-ow, --overwrite`: 覆盖现有的 .plexmatch 文件
- `-s, --season`: 指定季数

### 使用示例

```bash
# 基本扫描
python -m Plexmatch -d "C:\TV Shows\My Series\Season 1"

# 按顺序匹配并指定季数
python -m Plexmatch -d "C:\TV Shows\My Series\Season 2" -o -s 2

# 覆盖现有文件
python -m Plexmatch -d "C:\TV Shows\My Series\Season 1" -ow
```

## 支持的视频格式

3g2, 3gp, asf, asx, avc, avi, avs, bivx, bup, divx, dv, dvr-ms, evo, fli, flv, m2t, m2ts, m2v, m4v, mkv, mov, mp4, mpeg, mpg, mts, nsv, nuv, ogm, ogv, tp, pva, qt, rm, rmvb, sdp, svq3, strm, ts, ty, vdr, viv, vob, vp3, wmv, wtv, xsp, xvid, webm

## 工作原理

1. 扫描指定目录中的所有视频文件
2. 过滤掉特殊文件（如 [SP], [MENU] 等）
3. 使用自然排序对文件进行排序
4. 从文件名中提取剧集编号
5. 生成格式为 `ep: S{season}E{episode}: {filename}` 的 .plexmatch 文件

## 注意事项

- 如果目录中已存在 `.plexmatch` 文件，程序会退出（除非使用 `-ow` 参数）
- 程序会自动跳过包含 `[SP]` 和 `[MENU]` 标记的文件
- 剧集编号通过正则表达式从文件名中提取（查找 2-3 位数字）

## 许可证

请查看 LICENSE 文件了解详细信息。