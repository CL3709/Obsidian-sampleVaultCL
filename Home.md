---
banner: "http://img.netbian.com/file/2017/1207/5dd4b7e6b57c7e77c2354f782cfc2a74.jpg"
ObsidianUIMode: preview
banner_y: 0.5695
cssclasses:
  - darkblue
  - wideTable
  - darkblue-rounded
banner_x: 0.5
---
```ad-flex
<div style="float:left">  <%+ tp.date.now("A好，今天是YYYY年MM月Do dddd") %>
</div> 
<div>
<iframe style="float:right; margin-top:-3.2px" width="320" scrolling="no" height="27" frameborder="0" allowtransparency="true" src="https://i.tianqi.com?color=%23%FF7FB3CA&c=code&id=34&bdc=%23&icon=4&site=14&py=shenzhen"></iframe>
<!-----指定城市后面添加城市拼音比例如 深圳天气预报：https://i.tianqi.com/?c=code&id=34&bdc=%23&icon=4&site=14&py=shenzhen------>
</div>
```

>[!multi-column]
>>[!faq] **使用手册？**
>> 这里有一份关于这个示例库的说明：[[SampleVaultCL-beginPage|从这里开始]]

> [!multi-column]
>
>> [!note|min-0] **简览**
>> ```dataviewjs
>> //统计笔记 nofold 里面放入需要排除的文件夹
>> let nofold = '!"500_模板" and !"400_待办"'
>> let ftMd = new Date("2024-02-19")
>> let total = parseInt([new Date() - ftMd] / (60*60*24*1000))
>> let allFile = dv.pages(nofold).file
>> let totalMd = "✍️ =="+
>> 	allFile.length+"== 篇不知所云的文档"
>> let totalTag = "=="+allFile.etags.distinct().length+"== 个乱七八糟的标签"
>> let totalTask = "=="+allFile.tasks.length+"== 个已经荒废的事项"
>> dv.header(4, "📒 使用 Obsidian =="+total+"== 天了")
>> dv.header(5, totalMd)
>> dv.header(5, "🏷️ "+totalTag)
>> dv.header(5, "🗓️ " + totalTask)
>> ```
>> 
>> ```dataviewjs
>> //个性化进度条算法
>> let dates = moment().format('YYYY-MM-1');
>> let days = moment().diff(dates, "days");
>> let num = (days/30 * 10).toFixed(1);
>> dv.header(4,"⏱本月已走完 =="+num*10+'== %<br>')
>> dv.span(percentageToEmotes(num))
>> //dv.span(percentageToEmotes(num))
>> function percentageToEmotes(num) {
>>   //小数点分割
>> let str = num.toString().split('.');
>> let anum= parseInt(str[0]);
>> let bnum= parseInt(str[1]);
>> if(!bnum)
>> 	bnum=0;	
>> if(anum==10)
>> return "🌑".repeat(anum);
>> return "🌑".repeat(anum) +get_icon(bnum) + "🌕".repeat(9 - anum);
>> 
>> }
>> 
>> function get_icon(num){
>> switch( true ) {
>>     case num <=2   :
>> 		 return "🌕"
>>         break;
>>     case num <= 4 :
>> 		return "🌔"
>>         break;   
>>     case num <= 6 : 
>> 		return "🌓"
>>         break;
>> 	 case num <= 8 : 
>> 		return "🌒"
>>         break;
>> 		default:
>> 		return "🌑"
>>         break;
>> 		
>> }
>> }
>> ```
>> 
>> ```dataviewjs
>> //个性化进度条算法
>> let dates = moment().format('YYYY-1-1');
>> let days = moment().diff(dates, "days");
>> let num = (days/365 * 10).toFixed(1);
>> dv.header(4,"⏱今年已走完 =="+num*10+'== %<br>')
>> dv.span(percentageToEmotes(num))
>> //dv.span(percentageToEmotes(num))
>> function percentageToEmotes(num) {
>>   //小数点分割
>> let str = num.toString().split('.');
>> let anum= parseInt(str[0]);
>> let bnum= parseInt(str[1]);
>> if(!bnum)
>> 	bnum=0;	
>> if(anum==10)
>> return "🌑".repeat(anum);
>> return "🌑".repeat(anum) +get_icon(bnum) + "🌕".repeat(9 - anum);
>> 
>> }
>> 
>> function get_icon(num){
>> switch( true ) {
>>     case num <=2   :
>> 		 return "🌕"
>>         break;
>>     case num <= 4 :
>> 		return "🌔"
>>         break;   
>>     case num <= 6 : 
>> 		return "🌓"
>>         break;
>> 	 case num <= 8 : 
>> 		return "🌒"
>>         break;
>> 		default:
>> 		return "🌑"
>>         break;
>> 		
>> }
>> }
>> ```
>
>> [!abstract|wide-2] **最近编辑**
>> 
>> ```dataviewjs
>> let allFile = dv.pages('"000_收件"').file
>> let filenum = (allFile.length)
>> let totalMd = "🗃️ 收件箱还有 =="+
>> 	filenum+"== 篇文档没有任何去处"
>> dv.header(5, totalMd)
>> ```
>> 
>> ###### 📋 近期编辑的文档
>> ```dataview
>> table WITHOUT ID file.link AS "标题",file.mtime as "时间"
>> from "100_笔记" or "200_碎片" or "000_收件"
>> sort file.mtime desc
>> limit 5
>> ```
>> 
>

> [!multi-column]
>
>> [!example|min-0] **活动历史**
>> ```ActivityHistory
>> /
>> ```
>> 

> [!multi-column]
>
>> [!question|min-0] **还未完成或排期的个人安排**
>>> 📚 **这里的显示包含排期到未来的个人安排~**
>> ```tasks
>> not done
>> path includes 400_待办/410_日记录库
>> tag includes #个人 
>>hide backlink
>>hide created date
>>hide recurrence rule
>>hide done date
>>hide task count
>>hide edit button
>>short mode
>> ```
>
>>[!warning|wide-1] **还未完成或排期的工作事务**
>>>  📅 **这里不显示排期到未来的非个人事务~**
>>```tasks
>>not done
>>((path includes 400_待办/410_日记录库) AND (not done) AND (scheduled before tomorrow)) OR ((path includes 400_待办/410_日记录库) AND (done before tomorrow) AND (done after yesterday))
>>tag regex matches /(客户\/|部门\/|项目\/)/
>>hide backlink
>>hide created date
>>hide recurrence rule
>>hide done date
>>hide task count
>>hide edit button
>>short mode
>>```
>
