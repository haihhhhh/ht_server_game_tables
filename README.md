# ht_server_game_tables（共享配置表源）

策划维护 Datas 下的 Excel，服务端维护并同步 Defines/tables.xml 的类型和字段。客户端与服务端使用同一份源表，各自导出需要的语言和数据格式。

默认工具：Luban 5.1.0，运行环境 .NET 8。texts.xlsx 是文本；items.xlsx 是经验道具；levels.xlsx 是等级累计经验门槛，最后一级的经验是玩法上限。示例1001道具每个加10经验，等级从1至11、累计经验从0至1000，项目按玩法修改。
服务端导出入口位于 ../ht_server_game_template/scripts/Generate-Tables.bat 或 .sh，生成 Go 类型和 JSON，工具产物全部忽略、不入库。

不要把 Luban 的 outputCodeDir 指向手写代码目录；工具可能清理该目录。当前固定输出到 common/gamedata/generated，数据到 tables/exported。正式发布时将完整数据目录作为一个版本发布，服务内调用 Module.Reload 整套切换。

官方工具与说明：https://github.com/focus-creative-games/luban/releases/tag/v5.1.0 、https://www.datable.cn/docs/guide/install 。工具不要求部署到生产游戏进程。

本项目采用 [MIT 许可证](LICENSE)。
