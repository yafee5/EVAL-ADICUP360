# 淡水电导率：自焊制板版 v0.2

本版为当前推荐的制板交付，替代 v0.1 中不完整的主板制造资料与6V供电建议。主板沿用ADI官方CN0359 Rev A四层铜箔，装配按本版ECO；新增35×35mm双层ADP3338电源板。厂家只做裸板，用户自行采购和焊接。

- `conductivity-meter-v0.2-schematics-and-build.pdf`：22页完整电路、自焊ECO、厂家说明和审查记录；主板完整三页图在第19–21页，电源子板图在第22页。
- `conductivity-meter-v0.2-factory-only.zip`：直接发板厂的文件包，内含两份独立Gerber ZIP、裸板工艺说明和电路图。主板与电源板分别导入、分别生产。
- `CN0359_mainboard_4layer_Gerber_v02.zip`：四层主板的九层CAM图形及明确小数点公制钻孔。
- `CN0359_power_adapter_2layer_Gerber_v02.zip`：双层电源板Gerber及分开的PTH/NPTH钻孔。
- `self_solder_bom.xlsx`：209行主板及小板采购/装配记录，DNP、改值和自焊难点分别注明。
- `conductivity-meter-v0.2-self-solder-kit.zip`：完整自焊资料、KiCad小板源文件、官方来源、复核脚本、低热固件及校准工具。
- [`procurement/`](procurement/)：新增大陆采购附件，含15页签Excel、完整PDF、淘宝搜索入口、官网/授权渠道说明、标准液/探头询价文字和报价回填表。按1台原型加备件编制，76行板上合并采购项、81行其他项目，保留209条逐位号供对账；与原BOM是同一批电子料，不重复采购。

必须按ECO停装主板U4/L2/D3/C17，用稳压5.0V±2%供电；子板3.3V接主板L5.1，L5.3是地不可注入。主板R13=4.99kΩ，配freshwater_lowheat/200µA固件。MCU为LFCSP且底部EP必须焊接，需要热风/回流条件。

主板来源/图形与247孔槽定位已检查；新增小板ERC=0、DRC=0、未连接=0、原理图PCB一致性问题=0。尚未装机和实测±0.5%读数，需按标准液、温度槽与不确定度保护带验收。
