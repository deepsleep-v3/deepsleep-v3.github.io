---
layout:     post
title:      "HMCL++ 官宣進入公測！！"
subtitle:   " \"HMCL++！！\""
date:       2026-03-28 12:00:00 +0800
author:     "deepsleep-v3"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - HMCL++
mathjax: true
---

> First public version!!

大家好，這裡是 deepsleep-v3，HMCL++ 3.12.0.0 正式發佈！！

> 未來穿越者：deepsleep-v3，怎麼還有個 3.12.0 發佈？！

（回覆未來穿越者）：啊這，不得不提到 HMCL++ 的 upstream：HMCL-dev/HMCL 了⋯⋯***/HMCL/build.gradle.kts 裡的屎山⋯⋯

```kotlin
// /HMCL/build.gradle.kts
val projectConfig = PropertiesUtils.load(rootProject.file("config/project.properties").toPath())

val versionType = System.getenv("VERSION_TYPE") ?: projectConfig.getProperty("channel") ?: "dev"
val versionRoot = System.getenv("VERSION_ROOT") ?: projectConfig.getProperty("versionRoot") ?: "3"

// ...

val buildNumber = (System.getenv("BUILD_NUMBER")?: projectConfig.getProperty("buildNumber"))?.toInt()
if (buildNumber != null) {
    version = if (JenkinsUtils.IS_ON_CI && versionType == "dev") {
        "$versionRoot.0.$buildNumber"
    } else {
        "$versionRoot.$buildNumber"
    }
} else {
    val shortCommit = System.getenv("GITHUB_SHA")?.lowercase()?.substring(0, 7)
    version = if (shortCommit.isNullOrBlank()) {
        "$versionRoot.SNAPSHOT"
    } else {
        "$versionRoot.dev-$shortCommit"
    }
}
```
***
```properties
# /config/project.properties
#
# Hello Minecraft! Launcher
# Copyright (C) 2025 huangyuhui <huanghongxun2008@126.com> and contributors
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <https://www.gnu.org/licenses/>.
#
versionRoot=3.12
buildNumber=0
channel=dev
```

*****相關 Release 已在放出！！*****