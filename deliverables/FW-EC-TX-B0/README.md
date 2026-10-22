# FW-EC-TX Rev B0：精简电导率变送器工程包

**状态：工程样机，未生产放行。** κ(T)、四线Pt1000和Modbus核心已有源码/HEX及主机测试；正式ISO7888 nLF因子仍缺，κ25默认NaN并置UNVERIFIED。主板paste/CPL/IPC356/电气DRC未生成，不能把本包当完整自动贴片资料。

目标：两极K≈1cm⁻¹；10–50µS/cm ±1%读数、50–2000 ±0.5%；0–50°C温度整链±0.05°C。上述精度尚未实测。

## 先看这些文件

- `docs/交付状态.md` / `docs/delivery_status.json`：按文件与功能列出已做和缺项。
- `bom/FW_EC_TX_B0_BOM.xlsx`：新版10页签物料表；199条主板采购子项记录，含DNP；整机232条记录、68组合并采购项。两张表是同一批料，勿重复下单。
- `docs/FW_EC_TX_B0_design_and_schematics.pdf`：设计、接线、验证边界与全部现有电路图。
- `docs/整机接线.md` / `docs/FW_EC_TX_B0_wiring.pdf`：电导池、Pt1000、隔离485、5V与MAIN3V3接线。
- `firmware/build/fw_ec_tx_b0.hex`：新固件；禁止当作nLF功能已完成的出厂固件。原ASCII控制台、显示、本地菜单、编码器和蜂鸣器不再链接。
- `firmware/protocol/register_map.csv`、`docs/firmware_modbus_寄存器与校准.md`：完整0基寄存器、状态、写保护和校准操作。
- `firmware/tools/tx_modbus.py`：Modbus读取/配置/维护校准工具；默认地址1、9600 8E1。

## 硬件组成

1. 主板1块：原Rev A四层模拟铜保留，更换顶丝印，按B0 DNP。`hardware/mainboard/manufacturer/`只具备工程裸板CAM。
2. 电源/隔离485合并板1块：两路独立ADP3338-3.3、ADM2587E、TVS和跳线120Ω；旧独立35mm LDO板不再另买。
3. LT5400匹配网络适配片4块：6.25k/1k维持0.16，绝对阻值相对原7.5k/1.2k改变，寄生/负载和安装仍须验证。

已停装LCD/连接器、编码器/旋钮、蜂鸣器及其专用支持件；R17继续作为BM启动上拉，J4继续用于SWD。两块新增设计各有真KiCad源及自己的paste/drill/IPC/CPL/ERC/DRC，不能用其报告代替主板DRC。

## 尚不能跳过的项目

- 对应Rev A的原生PADS PCB/网表尚未取得。主板完整生产文件仍需恢复；详见`hardware/mainboard/README_主板生产边界.md`。
- 正式ISO7888/对应EN标准的nLF表尚未核验，详见`compensation/ISO7888_因子表获取与审核清单.md`；测试表不进生产默认配置。
- R13/R47精密电阻完整MPN及分销SKU待定标；所有库存/价格/生命周期未实时确认，未将访问失败写成缺货/停产。
- 尚未焊装、上电、标定或进行精度/温升/EMC/浪涌/隔离试验。具体指标只可在相应验证后宣称。

## 复现

固件：安装GNU Arm Embedded GCC和Python3，在`firmware/`运行`make`；`CROSS_COMPILE`可指定工具链前缀。主机测试命令以固件验证报告为准。Python串口工具需pyserial。

硬件：KiCad9、Python pcbnew与各目录的生成/审查脚本；元件库表与自定义库在相应板目录。打开源文件可重新审图，重新导出后须重跑ERC/DRC和本项目导出一致性检查。

BOM：`python3 tools/build_bom.py`，内部归档的baseline和规格JSON供追溯。报告打包需openpyxl、reportlab、PyMuPDF、pandoc、Inkscape；`make_release.py`不会把未通过/缺失的新增板制造文件标为检查通过。

原ADI设计档案、源版本/链接及哈希在`hardware/mainboard/sources_original/`。候选受控下载与Rev A/B差异证据在`source_candidates/`。原厂版权/许可原文随源码保留；生产丝印不含原品牌或未经试验的合规标志。
