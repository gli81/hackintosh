# Hackintosh TODO List

1. 找到检验`SSDT-HEPT.aml`正常工作的方式
2. 测试移除`SSDT-HEPT.aml`后能否继续正常工作
3. <del>移除`AppleALCU.kext`，并完善`config.plist`</del>
4. 定制`SSDT-EC.aml`，找到是否需要USB供电
5. 添加\`\`到`config.plist => ACPI => Patch`
6. 定制CPU管理`kext`
7. <del>找到检验核显正常工作的方式</del> `通过查看hackintool里的PCIe部分可以确定核显是否正常识别，通过hackintool主页能看到VDA是否正常工作，通过IORegistryMapper也能看到识别情况和驱动情况`
7. <del>驱动核显</del>`暂时放弃`
7. 找出蓝牙问题的解决的原因，`-btlfxnvramcheck`，重置nvram，`brcmfx-delay=3000`其中一个或没有任何一个，只是重新定制USB映射解决的
8. 更换为OpenCore Release版

