# 华为云ModelArts入门教程☁️

##  一、建立自己的OBS存储对象（用于在云平台上存储文件）
（1）在搜索栏输入OBS，选择"对象存储服务OBS=>"，进入OBS控制台
![CEC5DE39-7C2C-4973-B3E5-E3C7EB9C267F.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601627117033-09c07540-3878-4c59-bce3-628d5914416b.jpeg#align=left&display=inline&height=490&margin=%5Bobject%20Object%5D&name=CEC5DE39-7C2C-4973-B3E5-E3C7EB9C267F.jpeg&originHeight=490&originWidth=2388&size=440782&status=done&style=none&width=2388)
（2）按照链接中的教程创建桶：[如何创建桶](https://support.huaweicloud.com/usermanual-obs/obs_03_0306.html)
（3）按照链接中的教程新建文件夹 ：[新建文件](https://support.huaweicloud.com/usermanual-obs/obs_03_0316.html)
![FF65D723-F488-4642-98EE-2F23A0241D4C.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601627238613-5bb24e6a-bc19-4af1-ae04-e610829be3a9.jpeg#align=left&display=inline&height=946&margin=%5Bobject%20Object%5D&name=FF65D723-F488-4642-98EE-2F23A0241D4C.jpeg&originHeight=946&originWidth=2388&size=500010&status=done&style=none&width=2388)
（4）从本地上传文件（单次不超过100个），大批量参考链接：[大数据量上传方式](https://support.huaweicloud.com/bestpractice-obs/obs_05_0110.html)（推荐使用[OBS Browser+](https://support.huaweicloud.com/browsertg-obs/obs_03_1000.html)）
![C4D54D8A-6A98-4791-946D-D937ACF3C6AC.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601627510857-42ed67ba-7890-475b-b854-4d45cd25f4a3.jpeg#align=left&display=inline&height=590&margin=%5Bobject%20Object%5D&name=C4D54D8A-6A98-4791-946D-D937ACF3C6AC.jpeg&originHeight=590&originWidth=2358&size=346613&status=done&style=none&width=2358)
![D22C52C2-8B20-4110-9241-ACDF0E0A6479.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601627650862-fbc3b73a-15b7-411f-9bd0-7f32217d223a.jpeg#align=left&display=inline&height=1261&margin=%5Bobject%20Object%5D&name=D22C52C2-8B20-4110-9241-ACDF0E0A6479.jpeg&originHeight=1261&originWidth=1759&size=410310&status=done&style=none&width=1759)
##  二、自动训练&算法训练（notebook）
###  自动训练
（1）在搜索栏输入ModelArts，并进入控制台
![A803F7CE-48E1-43F1-8206-43C8F75107CF.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601628374251-85ef63b5-f076-438b-8800-2c4b33090e8c.jpeg#align=left&display=inline&height=611&margin=%5Bobject%20Object%5D&name=A803F7CE-48E1-43F1-8206-43C8F75107CF.jpeg&originHeight=611&originWidth=2388&size=427652&status=done&style=none&width=2388)
（2）跟随新手教程即可完成自动训练"寻找云宝"的目标检测模型
![753B12E2-B67C-4169-A716-7043716F3D9A.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601628490990-a7ef92a4-2a1a-4846-868b-1188a9285497.jpeg#align=left&display=inline&height=541&margin=%5Bobject%20Object%5D&name=753B12E2-B67C-4169-A716-7043716F3D9A.jpeg&originHeight=541&originWidth=1811&size=425470&status=done&style=none&width=1811)
（3）完成数据标注后进行模型的训练
![E15619C4-60BF-4534-9D8D-BC155C87FC0A.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601628820743-75b33d47-dc17-44bf-accb-d2943a8809f5.jpeg#align=left&display=inline&height=1449&margin=%5Bobject%20Object%5D&name=E15619C4-60BF-4534-9D8D-BC155C87FC0A.jpeg&originHeight=1449&originWidth=2362&size=458586&status=done&style=none&width=2362)
数据标注
![00415A3E-7442-4FAA-AE38-DBD3032F7F30.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601628960381-b4889ebf-d5ea-4f00-b664-39f8b0d483f6.jpeg#align=left&display=inline&height=1456&margin=%5Bobject%20Object%5D&name=00415A3E-7442-4FAA-AE38-DBD3032F7F30.jpeg&originHeight=1456&originWidth=2387&size=241883&status=done&style=none&width=2387)
模型训练
（4）训练完成后将模型进行在线部署为API接口
![7692FEE5-2C82-432F-A2E9-3FAC8C85472F.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601629301179-1199b32b-feaa-4927-8d33-229133d8eac8.jpeg#align=left&display=inline&height=1668&margin=%5Bobject%20Object%5D&name=7692FEE5-2C82-432F-A2E9-3FAC8C85472F.jpeg&originHeight=1668&originWidth=2388&size=288710&status=done&style=none&width=2388)
模型训练完成，点击部署开始API在线部署
![8D230635-6F3A-4A27-8BDA-D95AD64E7FCF.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601629320585-ff62efcf-dfda-4446-a35e-7033a2da7ad3.jpeg#align=left&display=inline&height=1453&margin=%5Bobject%20Object%5D&name=8D230635-6F3A-4A27-8BDA-D95AD64E7FCF.jpeg&originHeight=1453&originWidth=2387&size=359875&status=done&style=none&width=2387)
模型在线部署完成，上传图片测试或查看接口调用指南接入其他程序调用


###  算法训练（notebook）
（1）将自己要训练的模型和代码文件上传至自己的桶
（2）创建notebook
![5B59183E-E7D3-49CB-A26C-649D2259A191.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601629988373-8eeb792c-8d97-4376-a5b1-3108dceb076f.jpeg#align=left&display=inline&height=1384&margin=%5Bobject%20Object%5D&name=5B59183E-E7D3-49CB-A26C-649D2259A191.jpeg&originHeight=1384&originWidth=472&size=152398&status=done&style=none&width=472)
在modelarts控制台选择notebook
![065006BE-341B-4BB9-B620-EE450144C01B.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601630852938-ac47d994-c97a-4299-bdb4-434775af7038.jpeg#align=left&display=inline&height=1097&margin=%5Bobject%20Object%5D&name=065006BE-341B-4BB9-B620-EE450144C01B.jpeg&originHeight=1097&originWidth=2372&size=437736&status=done&style=none&width=2372)
创建notebook
![FB8BD47E-9307-4CB1-B73A-437A540A2C56.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601630983013-6f1114cd-7f1f-4ad0-9413-b51389e50738.jpeg#align=left&display=inline&height=1581&margin=%5Bobject%20Object%5D&name=FB8BD47E-9307-4CB1-B73A-437A540A2C56.jpeg&originHeight=1581&originWidth=2388&size=810225&status=done&style=none&width=2388)
注意选择存储配置为对象存储服务，存储位置选择自己上传的模型位置（根据自身需要设置自动停止时间）
![00D9C958-1B9F-4111-B247-0A0C44422543.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601631031064-5e012db9-8b8b-4e87-a433-e614d137ef96.jpeg#align=left&display=inline&height=984&margin=%5Bobject%20Object%5D&name=00D9C958-1B9F-4111-B247-0A0C44422543.jpeg&originHeight=984&originWidth=2306&size=516193&status=done&style=none&width=2306)
点击创建的notebook实例名称即可进入notebook
![438AD6D5-409C-4410-8610-1B874C5F406C.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601631120503-e35772b4-578f-45ff-b3cb-929d9868251e.jpeg#align=left&display=inline&height=1458&margin=%5Bobject%20Object%5D&name=438AD6D5-409C-4410-8610-1B874C5F406C.jpeg&originHeight=1458&originWidth=2388&size=675012&status=done&style=none&width=2388)
将OBS中的文件与notebook进行同步
![58085E11-C523-4B5C-A49A-19A1AD1B7FDC.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601631161067-15d0291f-d2e9-4b81-9ff5-685b3a2085dd.jpeg#align=left&display=inline&height=1445&margin=%5Bobject%20Object%5D&name=58085E11-C523-4B5C-A49A-19A1AD1B7FDC.jpeg&originHeight=1445&originWidth=2388&size=671924&status=done&style=none&width=2388)
打开终端进行环境配置
![F16D326B-B9F6-4051-8A51-E6D28566E38F.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601631187994-cdd77791-59f4-4f04-8d32-0a01653cb85e.jpeg#align=left&display=inline&height=612&margin=%5Bobject%20Object%5D&name=F16D326B-B9F6-4051-8A51-E6D28566E38F.jpeg&originHeight=612&originWidth=2388&size=312177&status=done&style=none&width=2388)
当前目录下的/work目录存放了我们所有的项目文件
![3D30B7DC-802C-4816-9598-AEC257225033.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601631231233-aff6371c-edb5-44d2-a580-d3bee3144301.jpeg#align=left&display=inline&height=645&margin=%5Bobject%20Object%5D&name=3D30B7DC-802C-4816-9598-AEC257225033.jpeg&originHeight=645&originWidth=2388&size=448291&status=done&style=none&width=2388)
通过readme查看当前notebook支持的初始环境，使用source命令激活环境，然后进行后续环境配置和训练


##  三、使用预配置模型进行训练
（1）在modelarts控制台进入AI市场
![59068BB3-95A3-48F5-BAF4-B967E6FB121D.png](https://cdn.nlark.com/yuque/0/2020/png/819385/1601631919655-325aa61d-4bee-46c0-813a-5dbdba96a931.png#align=left&display=inline&height=1668&margin=%5Bobject%20Object%5D&name=59068BB3-95A3-48F5-BAF4-B967E6FB121D.png&originHeight=1668&originWidth=2388&size=1241493&status=done&style=none&width=2388)
（2）选择合适的模型进行订阅
![97C40CB4-AE0A-41B7-841E-73BB3C9797A4.jpeg](https://cdn.nlark.com/yuque/0/2020/jpeg/819385/1601631983168-abdacebe-b1cd-41e0-a4a8-96c577473962.jpeg#align=left&display=inline&height=874&margin=%5Bobject%20Object%5D&name=97C40CB4-AE0A-41B7-841E-73BB3C9797A4.jpeg&originHeight=874&originWidth=2388&size=369042&status=done&style=none&width=2388)


（3）根据链接中的步骤进行预配置模型的训练和部署：[预配置模型训练方法](https://support.huaweicloud.com/bestpractice-modelarts/modelarts_10_0025.html)




































































































