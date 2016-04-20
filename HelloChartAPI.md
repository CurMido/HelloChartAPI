#HelloChartAPI-Android
####缘由:
>在Android开发过程中，由于项目需求，对图表类控件使用比较频繁，在各种各样的图表类中，选择了HelloChart这个图表库，但是在使用时发现这类控件并没有太多的使用说明，网络上对此介绍也比较少。在使用的时候需要花费时间去观察每个子类的方法所代表的意义，所以写一份关于HelloChart的使用文档。


##类LineChartView
######lecho.lib.hellocharts.view.LineChartView
######LineChartView lineChart = new LineChartView(this)

####lineChart

方法| 说明
-------- | ---
setZoomEnabled(boolean isZoomEnabled)|是否支持缩放
setInteractive(boolean isInteractive)|图表是否可以与用户互动
setValueSelectionEnabled(boolean isValueSelectionEnabled)|图表数据是否选中进行显示
setValueSelectionEnabled(boolean isValueSelectionEnabled)|动画
setLineChartData(LineChartData data)|图表设置数据，数据类型为LineChartData

####轴
######初始化节点数据集合：`List<PointValue> pointValues = new ArrayList<PointValue>()`
方法|说明
-------- | ---
add(PointValue object)|添加节点数据

######初始化轴：`Axis axisX/Y = new Axis()`
方法|说明
-------- | ---
setName(String name)|轴名称
setValues(List<AxisValue> axisValuesX/Y)|添加刻度值集合
setLineColor(int lineColor)|轴线颜色
setTextColor(int textcolor)|轴文字颜色
setTextSize(int size)|轴文字大小
setTypeface(Typeface type)|文字样式
setHasTiltedLabels(bolean isHasTit)|轴文字向左旋转角度
setHasLines(boolean isHasLines)|是否显示轴网格线
setHasSeparationLine(boolean isHasSeparationLine)|是否有分割线
setInside(boolean isInside)|轴文字是否在轴内部
######初始化轴刻度值：  `ArrayList<AxisValue> axisValuesX/Y = new ArrayList<AxisValue>()`
方法|说明
-------- | ---
add(AxisValue object)|添添加轴显示的刻度值
####Line
######初始化：`Line line = new Line(List<PointValue> pointValues)`
方法|说明
-------- | ---
setColor(Color color)|折线颜色
setStrokeWidth(float w)|折线宽度
setFilled(boolean isFilled)|折线覆盖区域是否填充
setCubic(boolean isCubic)|是否立体
setPointColor(Color color)|节点颜色
setPointRadius(float s)|节点半径
setHasLabels(boolean isHasLabels)|是否显示节点数据
setHasLines(boolean isHasLines)|是否显示折线
setHasPoints(boolean isHasPoint)|是否显示节点
setShape(ValueShape.CIRCLE)|节点图形样式 DIAMOND菱形、SQUARE方形、CIRCLE圆形
setHasLabelsOnlyForSelected(boolean isHasLabelsOnly)|隐藏数据，触摸可以显示
####LineChartData
######初始化：`LineChartData lineChartData = new LineChartData(List<Line> lines)`
方法|说明
-------- | ---
setAxisYLeft(Axis axis)|将Axis添加到左边轴上
setAxisXBottom(Axis axis)|同理
setAxisYRight(Axis axis)|同理
setAxisXTop(Axis axis)|同理
setBaseValue(flart baseValue)|反向覆盖区域
setValueLabelBackgroundAuto(boolean isValueLabelBackgrountAuto)|节点数据背景是否跟随节点颜色
setValueLabelBackgroundColor(int color)|节点数据背景颜色
setValueLabelBackgroundEnabled(boolean isValueLabelBackgroundEnabled)|节点数据是否有背景
setValueLabelsTextColor(int textColor)|节点数据文字颜色
setValueLabelTextSize(int textSize)|节点数据文字大小
setValueLabelTypeface(Typeface.MONOSPACE)|节点数据文字样式
setLineChartData(LineChartData data)|添加数据到图表

###代码
``` python

public void AddLineChartDate(){
		
		List<Line> lines = new ArrayList<Line>();
		List<PointValue> pointValues = new ArrayList<PointValue>();//节点数据结合
		Axis axisY = new Axis();//Y轴属性
		Axis axisYRight = new Axis();//Y轴属性
		Axis axisX = new Axis();//X轴属性
		for (int i = 0; i < numberOfLines; i++) {
			axisY.setName("Y轴");
			axisX.setName("X轴");
			axisYRight.setName("axisYRight");
			ArrayList<AxisValue> axisValuesY = new ArrayList<AxisValue>();
			ArrayList<AxisValue> axisValuesX = new ArrayList<AxisValue>();
			ArrayList<AxisValue> axisValuesYRight = new ArrayList<AxisValue>();
			for (int j = 0; j < LineChartNums; j++) {
				pointValues.add(new PointValue(j, j*(i+1)));//添加节点数据
				axisValuesY.add(new AxisValue(j).setValue(j));//添加Y轴显示的刻度值
				axisValuesX.add(new AxisValue(j).setValue(j));//添加X轴显示的刻度值
				axisValuesYRight.add(new AxisValue(j).setValue(j*10));
				
			}
			axisY.setValues(axisValuesY);
			axisX.setValues(axisValuesX);
			axisYRight.setValues(axisValuesYRight);
			axisX.setLineColor(Color.BLACK);//无效果
			axisY.setLineColor(Color.BLUE);//无效果
			
			axisX.setTextColor(Color.BLACK);//设置X轴文字颜色
			axisY.setTextColor(Color.BLUE);//设置Y轴文字颜色
			
			axisX.setTextSize(20);//设置X轴文字大小
			axisX.setTypeface(Typeface.SERIF);//设置文字样式
			
			axisX.setHasTiltedLabels(true);//设置X轴文字向左旋转45度
			axisX.setHasLines(true);//是否显示X轴网格线
			axisY.setHasLines(true);
			
			axisX.setHasSeparationLine(true);//..
			axisX.setInside(true);//设置X轴文字在X轴内部
			
			
		}
		Line line = new Line(pointValues);
		line.setColor(Color.GREEN);//设置折线颜色
		line.setStrokeWidth(5);//设置折线宽度
		line.setFilled(true);//设置折线覆盖区域颜色
		line.setCubic(isCubic);//节点之间的过渡
		line.setPointColor(Color.RED);//设置节点颜色
		line.setPointRadius(10);//设置节点半径
		line.setHasLabels(true);//是否显示节点数据
		line.setHasLines(true);//是否显示折线
		line.setHasPoints(true);//是否显示节点
		line.setShape(ValueShape.CIRCLE);//节点图形样式 DIAMOND菱形、SQUARE方形、CIRCLE圆形
		line.setHasLabelsOnlyForSelected(false);//隐藏数据，触摸可以显示
		lines.add(line);//将数据集合添加到线
		
		chartData = new LineChartData(lines);
		chartData.setAxisYLeft(axisY);//将Y轴属性设置到左边
		chartData.setAxisXBottom(axisX);//将X轴属性设置到底部
		chartData.setAxisYRight(axisYRight);
		chartData.setBaseValue(20);//设置反向覆盖区域颜色
		chartData.setValueLabelBackgroundAuto(false);//设置数据背景是否跟随节点颜色
		chartData.setValueLabelBackgroundColor(Color.BLUE);//设置数据背景颜色
		chartData.setValueLabelBackgroundEnabled(false);//设置是否有数据背景
		chartData.setValueLabelsTextColor(Color.RED);//设置数据文字颜色
		chartData.setValueLabelTextSize(15);//设置数据文字大小
		chartData.setValueLabelTypeface(Typeface.MONOSPACE);//设置数据文字样式
		
		
		lineChart.setLineChartData(chartData);//将数据添加到控件中
	}
```

##后续继续补充