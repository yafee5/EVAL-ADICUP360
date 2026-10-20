# v0.2 大陆采购附件

按1台原型+表列备件编制；PCB各5片不表示5套整机电子料。

- `conductivity-meter-v0.2-procurement-cn.xlsx`：优先使用，15页签，76行板上合并采购项、81行其他项目、209条逐位号、DNP和询价文字、报价回填、Q005电阻套件展开。
- `conductivity-meter-v0.2-procurement-cn.pdf`：可打印的完整采购说明。
- `采购清单与询价说明.md`：可复制的文本版。
- `electronics_order.csv`：合并电子料，勿与逐位号重复下单。
- `all_procurement_items.csv` / `procurement_items.json`：机器可读全部采购项。
- `Q005_resistance_standards_breakdown.csv`：Q005一套9只校准电阻的明细，不重复下单。
- `procurement_validation.json`：数量与追溯核对记录。

适用于已交付v0.2主板+3.3V LDO子板、R13=4.99k、freshwater_lowheat。原图/Gerber/固件仍使用上一份v0.2自焊包。

供应渠道是大陆购买/询价入口，不代表已核实具体店铺、现货或价格。ADI商城与授权渠道页已打开，授权页确认中电港、得捷、贸泽、Farnell；第三方具体商品受访问环境限制未在线核验。淘宝链接是搜索页。精密电阻、LCD、探头和标准液先审资料再下单。

±0.5%读数是目标，必须整机实测验证。昂贵校准设备可租用或委托实验室，Excel明确列了替代路径。
