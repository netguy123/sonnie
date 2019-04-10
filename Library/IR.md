# 机构库

## 职称评审与等级聘用上传流程
1. [ ] 统一登录。自动获取姓名、工资号、院系、邮箱等的信息
2. [ ] 填写起始年限、手机号（座机也可）
3. [ ] 上传excel（提示：其他格式也可以）
4. [ ] 以上信息保存到表里

## 文章列表

### 文章列表的关联、比对顺序
1.  SCI、EI的 DOI 是否相等
2.  EI的与中如果是中文，则用 CSCD 比较英文，在总表中显示中文
3.  
   - 1. SCI和EI的字段比较：PG & Title前若干字符
   - 2. 在1的基础上增加 ISSN
   - 3. 在2的基础上增加出版年
   - 4. Title的前若干字符
4. SCI、EI vs CSCD
   - 1. PG
   - 2. PG & 出版年

### 比对
- [ ] 点击打开后，保存这些基本信息在SESSION，以防切换页面后丢失
- [ ] 左侧显示总表
- [ ] 右侧显示该库的文章清单。未关联的，未加入总表的，以颜色区分

## EI

- [ ] 上传pdf（detailed格式），得到downloaded time和收录号，与作者绑定（事先建好表），并标记为：已收录&上次收录时间
- [ ] 触发式查询收录情况（或者每半年定时更新）。如果仍然收录，则修改收录时间；否则修改为未收录。有可能题名不变而收录号改变，所以要给出链接。
- [ ] 从Ei中，根据检索式+Language=Chinese，导出某种格式，要包含DOI、Title、ISSN、Accession Number
- [ ] 根据DOI或Title+ISSN到CSCD检索，得到其中文标题
- [ ] 上传题名列表，匹配后标记到该作者名下
- [ ] 要能导出所有的收录号，以 xx OR xx 拼接
- [ ] 输出格式：Accession Number以及Citation，要能显示Detail

## 软件

DSpace安装和配置 https://wiki.duraspace.org/display/DSDOC5x/Installing+DSpace
1. 让tomcat以dspace用户运行：创建dspace用户，并加入tomcat组，然后在tomcat的启动脚本里写入 TOMCAT_USER="dspace"
2. 要安装oracle instantclient，然后在mvn install:install-file -Dfile=<绝对路径>/ojdbc6.jar -DgroupId=com.oracle -DartifactId=ojdbc6 -Dversion=11.2.0.4.0 -Dpackaging=jar -DgeneratePom=true
3. mvn -Ddb.name=oracle package
4. dspace这个用户在oracle的dspace表空间，要有建表和视图的权限
5. 11.2.0.2这个版本的jdbc驱动不能用！
