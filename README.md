# Examination-Assistant
体检系统Python 环境校验工具
项目结构：

main.py: 主逻辑与报告生成。

db_client.py: 使用 cx_Oracle 封装数据库操作。

network_tester.py: 负责网络连通性检测。

config.json: 存放数据库连接串及预期的 IP 地址。

核心逻辑（根据文档与截图定制）：

数据库校验：连接数据库并查询 tj_xtsz_xtbl 表。对比当前值与预期值。重点检查：

blmc 为 ‘JMPDF导出地址’ 的 blz 是否为有效的 URL。

blmc 为 ‘医生站项目费用状态控制’ 的 blz 是否开启（1 表示开启）。

blmc 为 ‘VIP人员是否允许先体检后付费’ 的配置状态。

网络连通性：从 tj_xtsz_xtbl 获取 ‘文件服务 HOSR’ 的 IP，并自动 ping 该地址，确保文件服务器在线。

身份证校验位检查：根据文档第 2 页，验证 ‘身份证号校验控制’ 变量是否已按规范设置为‘强制校验’。

输出：

脚本运行结束时，在控制台打印一个表格（推荐使用 prettytable 库），显示：变量名称、当前值、检测状态（正常/异常）、建议操作。

同时将结果写入 deployment_check.log。
