### 项目重命名计划 - pig 改为 dataselfcloud ###
将项目中所有与 pig 相关的命名全部替换为 dataselfcloud，包括模块名、包名、类名、配置文件等，确保项目结构完整且可正常运行。

## 项目重命名执行计划

### 一、重命名范围分析

根据代码扫描，需要修改的内容包括：

**1. 目录/模块名称**
- `pig-auth` → `dataselfcloud-auth`
- `pig-boot` → `dataselfcloud-boot`
- `pig-common` → `dataselfcloud-common`
- `pig-gateway` → `dataselfcloud-gateway`
- `pig-register` → `dataselfcloud-register`
- `pig-upms` → `dataselfcloud-upms`
- `pig-visual` → `dataselfcloud-visual`

**2. Java 包名**
- `com.pig4cloud.pig` → `com.dataselfcloud.dataselfcloud`
- `com.pig4cloud.plugin` → `com.dataselfcloud.plugin`
- `com.pig4cloud.captcha` → `com.dataselfcloud.captcha`

**3. Maven 坐标**
- groupId: `com.pig4cloud` → `com.dataselfcloud`
- artifactId: `pig-*` → `dataselfcloud-*`

**4. 配置文件内容**
- Docker 镜像命名空间
- 项目描述信息
- URL 地址等

### 二、执行步骤（按顺序执行）

#### 阶段一：备份与准备（必须先执行）

1. **创建项目备份**
   - 在项目外部创建完整备份
   - 确保 Git 已提交所有更改

2. **验证项目当前状态**
   - 确认项目可以正常编译
   - 记录当前的依赖关系

#### 阶段二：重命名目录结构

3. **重命名根目录下的模块文件夹**
   - `pig-auth` → `dataselfcloud-auth`
   - `pig-boot` → `dataselfcloud-boot`
   - `pig-common` → `dataselfcloud-common`
   - `pig-gateway` → `dataselfcloud-gateway`
   - `pig-register` → `dataselfcloud-register`
   - `pig-upms` → `dataselfcloud-upms`
   - `pig-visual` → `dataselfcloud-visual`

4. **重命名 pig-common 子模块**
   - `pig-common-bom` → `dataselfcloud-common-bom`
   - `pig-common-core` → `dataselfcloud-common-core`
   - `pig-common-datasource` → `dataselfcloud-common-datasource`
   - `pig-common-excel` → `dataselfcloud-common-excel`
   - `pig-common-feign` → `dataselfcloud-common-feign`
   - `pig-common-log` → `dataselfcloud-common-log`
   - `pig-common-mybatis` → `dataselfcloud-common-mybatis`
   - `pig-common-oss` → `dataselfcloud-common-oss`
   - `pig-common-seata` → `dataselfcloud-common-seata`
   - `pig-common-security` → `dataselfcloud-common-security`
   - `pig-common-swagger` → `dataselfcloud-common-swagger`
   - `pig-common-websocket` → `dataselfcloud-common-websocket`
   - `pig-common-xss` → `dataselfcloud-common-xss`

5. **重命名 pig-visual 子模块**
   - `pig-codegen` → `dataselfcloud-codegen`
   - `pig-monitor` → `dataselfcloud-monitor`
   - `pig-quartz` → `dataselfcloud-quartz`

6. **重命名 pig-upms 子模块**
   - `pig-upms-api` → `dataselfcloud-upms-api`
   - `pig-upms-biz` → `dataselfcloud-upms-biz`

#### 阶段三：修改 Java 包结构

7. **重命名 Java 包路径**
   - 将所有 `com/pig4cloud/pig` 目录重命名为 `com/dataselfcloud/dataselfcloud`
   - 将所有 `com/pig4cloud/plugin` 目录重命名为 `com/dataselfcloud/plugin`
   - 将所有 `com/pig4cloud/captcha` 目录重命名为 `com/dataselfcloud/captcha`

#### 阶段四：修改 Maven 配置文件

8. **修改根 pom.xml**
   - groupId: `com.pig4cloud` → `com.dataselfcloud`
   - artifactId: `pig` → `dataselfcloud`
   - name: `${project.artifactId}`
   - url: 更新为新的项目地址
   - docker.namespace: `pig4cloud` → `dataselfcloud`
   - modules 列表中的模块名
   - 版权信息注释

9. **修改所有子模块的 pom.xml**
   - parent groupId 和 artifactId
   - 当前模块的 artifactId
   - 依赖中的 groupId 和 artifactId
   - 描述信息中的项目名称
   - 版权信息注释

#### 阶段五：修改 Java 源代码

10. **批量替换 Java 文件中的包导入**
    - `import com.pig4cloud.pig` → `import com.dataselfcloud.dataselfcloud`
    - `import com.pig4cloud.plugin` → `import com.dataselfcloud.plugin`
    - `import com.pig4cloud.captcha` → `import com.dataselfcloud.captcha`

11. **修改 package 声明**
    - `package com.pig4cloud.pig` → `package com.dataselfcloud.dataselfcloud`
    - `package com.pig4cloud.plugin` → `package com.dataselfcloud.dataselfcloud`

12. **修改类注释中的版权信息**
    - `Copyright (c) 2020 pig4cloud Authors` → `Copyright (c) 2025 dataselfcloud Authors`
    - 作者信息可保留或更新

#### 阶段六：修改配置文件

13. **修改 application.yml / application.properties**
    - 应用名称
    - 服务名称
    - 包扫描路径
    - 日志配置中的包路径

14. **修改 logback-spring.xml**
    - logger name 中的包路径

15. **修改 Dockerfile**
    - 镜像名称和标签
    - 注释说明

16. **修改 docker-compose.yml**
    - 服务名称
    - 镜像名称
    - 容器名称

#### 阶段七：修改文档和其他文件

17. **修改 README.md**
    - 项目名称和描述
    - 徽章链接
    - 文档链接
    - 模块说明
    - 删除或更新原项目的链接和二维码

18. **修改 .gitee 和 .github 配置**
    - 工作流文件中的项目名称
    - Issue 模板中的项目信息

19. **修改数据库脚本**
    - `db/pig.sql` → `db/dataselfcloud.sql`
    - `db/pig_config.sql` → `db/dataselfcloud_config.sql`
    - SQL 文件内容中的注释和说明

20. **修改 LICENSE 文件**
    - 更新版权所有者信息（保留原作者致谢）

#### 阶段八：验证与测试

21. **清理和重新编译**
    - 删除所有 target 目录
    - 删除 IDE 配置文件（.idea、*.iml）
    - 执行 `mvn clean`

22. **重新构建项目**
    - 执行 `mvn install` 验证编译
    - 检查是否有编译错误
    - 解决依赖问题

23. **功能验证**
    - 启动各个服务模块
    - 验证服务注册发现
    - 验证基本功能可用

24. **Git 提交**
    - 提交所有更改
    - 添加详细的提交说明

### 三、注意事项

**⚠️ 重要提醒：**

1. **执行顺序严格按照计划**
   - 必须先备份，再执行重命名
   - 目录重命名要在文件内容修改之前完成

2. **批量替换需谨慎**
   - 使用 IDE 的重构功能而非简单的文本替换
   - 避免替换到不该替换的内容（如第三方库）

3. **保留原项目信息**
   - 在 README 中保留对原 pig 项目的致谢
   - 遵守 Apache 2.0 开源协议

4. **测试覆盖**
   - 每个阶段完成后进行编译测试
   - 发现问题及时回滚

5. **依赖关系**
   - 注意模块间的依赖顺序
   - 先修改被依赖的模块（如 common）

6. **配置文件**
   - 检查所有 yml/properties 文件
   - 确保没有遗漏的配置项

### 四、回滚方案

如果执行过程中出现问题：

1. 使用 Git 回滚到备份点
2. 或者从外部备份恢复
3. 分析失败原因后重新执行

### 五、预估工作量

- 目录重命名：约 30 分钟
- Maven 配置修改：约 1 小时
- Java 代码修改：约 2-3 小时
- 配置文件修改：约 1 小时
- 测试验证：约 1-2 小时
- **总计：约 5-7 小时**

### 六、成功标准

1. ✅ 项目可以正常编译（mvn clean install 成功）
2. ✅ 所有服务可以正常启动
3. ✅ 服务注册发现正常
4. ✅ 基本功能可用
5. ✅ 无编译警告和错误
6. ✅ Git 历史清晰可追溯


updateAtTime: 2025/12/30 13:52:46

planId: 783547f0-7be1-49c1-9950-02ae0912a8d6