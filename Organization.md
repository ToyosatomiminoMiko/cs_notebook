# Computer Organization

计算机组成原理

## Hardware

### 芯片?

- FPGA 制造商
  - Intel®/Altera
  - AMD®/Xilinx
- MCU 制造商
  - STMicroelectronics
  - Texas Instruments

#### 封装方式

- QFP
    *Quad Flat Package*
    四侧引脚扁平封装
  - LQFP
  - TQFP
- BGA
*Ball Grid Array*
- LGA
*Land Grid Array*
- PGA
*Pin Grid Array*

### 显示技术

- EL
*Electro-Luminescent*
电致发光
- LCD
*Liquid Crystal Display*
液晶显示
- OLED
*Organic Light-Emitting Diode*
有机发光二极管
- TOLED
透明有机发光二极管
- LED
*Light Emitting Diode*
发光二极管
- CRT
*Cathode Ray Tube*
阴极射线管
- VFD
*Vacuum Fluorescent Display*
真空荧光显示器
- NIXIE
*Nixie tube*
辉光管

### 门电路

#### NAND

与非门

#### NOR

或非门

#### universal gates (通用逻辑门)

NAND, NOR
> 可以只使用这两种逻辑门中的一种构造任何数字电路,并实现计算机中的所有功能
> 现代的电脑一般会用到不止一种逻辑门,不过一般来讲厂家还是会尽量多用与非门,少用或非门.这是因为尽管两种逻辑门在逻辑功能上相同,但在实际的芯片产品上,与非门占据的面积却更小,延迟也更少(响应速度更快). -TC

### 存储技术

**非易失性存储器**: 断电后数据不会丢失.ROM家族和Flash都属于此类.

**易失性存储器**: DRAM 断电后不能保持数据.SRAM和DRAM属于此类;
断电后电容电荷不会"立即"完全消失,会短时间残留,但逻辑上属于易失性.

#### 非易失性存储器(NVM)

NVM,*Non-Volatile Memory*

##### ROM

*Mask ROM*
*Read-Only Memory*
只有掩膜 ROM 是制造时固定、不可修改
在芯片制造时,通过掩膜工艺将数据"刻"在电路里.一旦生产完成,数据永久固定,无法修改

##### PROM

*Programmable ROM*
出厂时为全"1"(或全"0"),取决于工艺.用户使用专用的编程器,通过高电压将内部的熔丝烧断(熔丝型,也有反熔丝型),从而将某些位写为"0"(或"1").一次性编程.

##### EPROM

*Erasable Programmable ROM*
利用浮栅晶体管存储电荷.编程时用高电压注入电荷,擦除时需要紫外线照射芯片上的石英窗口约20..30分钟,使电荷获得能量逃逸,从而擦除整个芯片

##### EEPROM

*Electrically Erasable Programmable ROM*
同样是浮栅晶体管,但结构更精细,允许用电信号进行擦除和写入.关键是可以**按字节进行擦写**

##### Flash

Flash是EEPROM浮栅技术的衍生/变体,但关键区别是: EEPROM 可按字节擦写, Flash 通常按块/页擦除.

- NOR Flash
晶体管**并联**结构,读取速度快,支持字节级的随机读取,可以直接在芯片上运行代码.但密度低,成本高,按"块"擦除,写入速度慢.主要用于存储关键程序代码,如主板BIOS,路由器固件,嵌入式系统启动代码等.

- NAND Flash
晶体管**串联**结构,密度高,写入和擦除速度快,成本低,按页读写,按块擦除,不能像 NOR 那样按字节随机读取.主要用于大容量数据存储,如 SSD,U盘,手机,相机存储卡等.

#### 易失性存储器

SRAM 和 DRAM 是典型的易失性 RAM
*Volatile Memory*
随机存储器(RAM,*Random Access Memory*)

##### DRAM

*Dynamic RAM*
电容存储 动态刷新 内存

双倍数据速率(DDR,double data rate)
上升沿下降沿传输

##### SRAM

*Static RAM*
SRAM 由双稳态触发器/锁存器构成,不需要刷新
CPU Register(触发器) & L1,L2 cache(6晶体管)

#### 排位

按速度划分:

1. Register (Flip-Flops)
2. L1,L2 Cache (SRAM)
3. L3 Cache
4. memory (DRAM)
5. SSD (Solid State Drive) (NAND Flash)
6. HDD (Hard Disk Drive)

#### 读写

机械硬盘 HDD: 小物理读写单位通常是**扇区(sector)**,如 512B 或 4kB.
固态硬盘 SSD: NAND 闪存内部最小读写单位是**页(page)**,最小擦除单位是**块(block)**.
