# VASP的输入文件

VASP运行至少包含四个输入文件：`INCAR`、`POSCAR`、`POTCATR`、`KPOINTS`。

## INCAR

INCAR 是VASP运行的**控制文件**，他告诉VASP要**做什么以及如何去做**。INCAR文件中包含很多标签及其对应的值，通过修改他们来修改VASP运行的参数。

标签的含义可以查 [VASP手册](https://www.vasp.at/wiki/index.php/Category:INCAR) 。

## POSCAR

POSCAR是个**结构文件**，他告诉VASP要运行的是什么物质。该文件包含晶格几何形状和离子位置等。

这是一个POSCAR文件的示例：

```
O2 molecule           # 注释行
10                    # 比例，提供了通用缩放因子（晶格常数）
1.0 0.0 0.0           # 3-5行 格矢
0.0 1.0 0.0
0.0 0.0 1.0
O                     # 元素类别（与它们在POTCAR文件中的顺序一致）
2                     # 原子数量
Selective Dynamic     # 
Direct                # 坐标类别：直角/笛卡尔
0.5 0.5 0.5    F F F  # 每个原子的三个(X Y Z)坐标。
0.5 0.5 0.623  F F T
```

第8行：该模式允许为每个原子提供额外的标志，以指示在离子弛豫期间是否将允许更改此原子的相应坐标。如果仅缺陷周围的某些壳或表面附近的层应松弛，则此设置很有用。**选择性动力学输入标签是可选的，如果省略了选择性动力学标签，则第八行将在笛卡尔和直角坐标之间进行切换，如下。**

第9行：（如果不启用选择性动力学，则为第8行）指定原子位置是在笛卡尔坐标系中还是在直角坐标（分别为分数坐标）中提供。仅一行上的第一个字符是有效的，并且VASP识别的唯一关键字符是`C`or`c` for `cartesian mode`，`D`or`d`for `direct mode`。

```
O2 molecule           # 注释行
10                    # 比例，提供了通用缩放因子（晶格常数）
1.0 0.0 0.0           # 3-5行 格矢
0.0 1.0 0.0
0.0 0.0 1.0
O                     # 元素类别（与它们在POTCAR文件中的顺序一致）
2                     # 原子数量
Direct                # 坐标类别：直角/笛卡尔
0.5 0.5 0.5           # 每个原子的三个(X Y Z)坐标。
0.5 0.5 0.623  
```

## POTCAR

赝势文件。POTCAR文件包含计算中使用的每个原子种类的伪势。如果物种数量大于一个，则**按照POSCAR中原子的顺序**合并每个物种的POTCAR文件。



## KPOINTS

K点取样文件。KPOINTS文件用于指定Bloch矢量（k点），这些矢量将用于在计算中对布里渊区进行采样。

可以使用几种不同的方法在KPOINTS文件中指定k点：（1）作为自动生成的（移位的）常规点网格；（2）通过线段的起点和终点；或（ 3）作为点和权重的明确列表。

手册：[KPOINTS - Vaspwiki](https://www.vasp.at/wiki/index.php/KPOINTS)



---

还有一些其他的文件：[Category:Input Files - vaspwiki](https://www.vasp.at/wiki/index.php/Category:Input_Files) .