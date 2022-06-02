v2.48更新内容:
1.支持sparse镜像烧录,且擦除分区尾部的verity信息
2.支持gpt分区表烧录,可以是partition_table格式的gpt文件或者parameter文件
3.支持mtp,uvc设备的切换

v2.5更新内容:
1.解决nand擦除flash问题

v2.52更新内容：
1.gpt支持固件uuid
通过在parameter文件中，按以下格式指定uuid:
uuid:分区名=00000000-0000-0000-0000-000000000000