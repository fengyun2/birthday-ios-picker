### 兼容PC和移动设备的日期滑动选择jquery插件(仿ios风格) - 基于 jquery(不兼容zepto)

使用说明:
1. 在页面上一如 css 和 js (可参考 date.html)
```
<link rel="stylesheet" href="css/normalize3.0.2.min.css" />
<link rel="stylesheet" href="css/style.css?v=7" />
<link href="css/mobiscroll.css" rel="stylesheet" />
<link href="css/mobiscroll_date.css" rel="stylesheet" />

<script src="js/jquery.min.js"></script>
<script src="js/mobiscroll_date.js" charset="gb2312"></script>
<script src="js/mobiscroll.js"></script>
```

2. 日期组件初始化

``` js
<script type="text/javascript">
	$(function () {
		var currYear = (new Date()).getFullYear();
		var opt={};
			// opt.date = {preset : 'date'};
			// opt.datetime = {preset : 'datetime'};
			// opt.time = {preset : 'time'};
			opt.default = {
		theme: 'android-ics light', //皮肤样式
		// theme: 'mobiscroll', //皮肤样式
		display: 'modal', //显示方式
		// display: 'bottom',
		mode: 'scroller', //日期选择模式
		// dateFormat: 'yyyy-mm-dd',	// 返回结果格式化为年月格式
		// dateFormat: 'yy/mm',
		// wheels:[],

		preset: 'datetime',
		timeFormat: 'HH:ii',
		timeWheels: 'HHii',
		lang: 'zh',
		setText: '确定',
		cancelText: '取消',
		dateOrder: 'HH-ii',
		minWidth: 35,
		stepMinute: 5,
		// dateOrder: 'yymmdd',
		showNow: true,
		// nowText: "今天",
		nowText: "",
		startYear: currYear - 50, //开始年份
		endYear: currYear + 10, //结束年份
		onBeforeShow: function (html,inst) { // (可能是我这个版本的问题,我的没有成功)
			console.log('onBeforeShow-html: ',html);
			console.log('onBeforeShow-inst: ',inst);
			// inst.settings.wheels[0].length>2?inst.settings.wheels[0].pop():null;
		}, //弹掉“日”滚轮
		headerText: function (valueText) { //自定义弹出框头部格式(可能是我这个版本的问题,我的没有成功)
			console.log('valueText: ',valueText);
            // array = valueText.split('/');
            // return array[0] + "年" + array[1] + "月";
        },
        validate: function(html, index){
        	console.log('html: ',html);
        },
        onChange: function(val, inst){
        	var str = val.split(' ')[0].split('-')[0]+':'+val.split(' ')[0].split('-')[1];
        	console.log('onChange-val: ',val);
        	console.log('onChange-str: ',str);

            // console.log(this);
            // $(this).val(str);
        },
        onSelect: function(val){
        	var str = val.split(' ')[0].split('-')[0]+':'+val.split(' ')[0].split('-')[1];

        	console.log('onSelect-val: ',val);
        	console.log('onSelect-str: ',str);
            // $(this).val(str);
        }
    };

    $("#USER_AGE").mobiscroll($.extend(opt['date'], opt['default']));

});
</script>
```
