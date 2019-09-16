# 侧滑筛选功能的实现的思路-使用DrawerLayout布局实现侧滑功能
### 其布局界面如下
```java
<android.support.v4.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/dzx_drawerLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical" >
        <TextView
            android:id="@+id/empty_text_dzxMain"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_horizontal"
            android:text="该条件下没有数据"
            android:textColor="@android:color/darker_gray"
            android:textSize="16sp" />

        <android.support.v4.widget.SwipeRefreshLayout
            android:id="@+id/refresh_dzx"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:background="#fafafa" >

            <ListView
                android:id="@+id/listView_dzx"
                android:layout_width="match_parent"
                android:layout_height="match_parent" />
        </android.support.v4.widget.SwipeRefreshLayout>
    </LinearLayout>
//侧滑栏的内容布局，从这里开始
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_gravity="end"
        android:background="@android:color/white"
        android:orientation="vertical" >

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical" >

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="5dp"
                android:text="设施类型："
                android:textSize="12sp" />

            <RadioGroup
                android:id="@+id/rg1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <RadioButton
                    android:id="@+id/rg1_rb1"
                    android:layout_width="70dp"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:gravity="center"
                    android:text="桥梁"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />

                <RadioButton
                    android:id="@+id/rg1_rb2"
                    android:layout_width="70dp"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:gravity="center"
                    android:text="道路"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />
            </RadioGroup>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical" >

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="5dp"
                android:text="经费预算："
                android:textSize="12sp" />

            <RadioGroup
                android:id="@+id/rg2_1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <RadioButton
                    android:id="@+id/rg2_rb1"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="10万元以内"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />

                <RadioButton
                    android:id="@+id/rg2_rb2"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="10-20万元"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />

                <RadioButton
                    android:id="@+id/rg2_rb3"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="20-50万元"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />
            </RadioGroup>

            <RadioGroup
                android:id="@+id/rg2_2"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <RadioButton
                    android:id="@+id/rg2_rb4"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="50-100万元"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />

                <RadioButton
                    android:id="@+id/rg2_rb5"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="100万元以上"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />
            </RadioGroup>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical" >

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="5dp"
                android:text="项目总量："
                android:textSize="12sp" />

            <RadioGroup
                android:id="@+id/rg3_1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <RadioButton
                    android:id="@+id/rg3_rb1"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="1千平方米以内"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />

                <RadioButton
                    android:id="@+id/rg3_rb2"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="1千-5千平方米"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />

                <RadioButton
                    android:id="@+id/rg3_rb3"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="5千-1万平方米"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />
            </RadioGroup>

            <RadioGroup
                android:id="@+id/rg3_2"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal" >

                <RadioButton
                    android:id="@+id/rg3_rb4"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_margin="5dp"
                    android:background="@drawable/dzx_radiobutton_selector"
                    android:button="@null"
                    android:text="1万平方米以上"
                    android:textColor="@color/dzx_text_selector"
                    android:textSize="12sp" />
            </RadioGroup>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical" >

            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_marginStart="5dp"
                android:text="项目的开工时间："
                android:textSize="12sp" />

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_marginStart="5dp"
                android:orientation="horizontal" >

                <TextView
                    android:id="@+id/startTime_dzxMain"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="请选择开始时间"
                    android:textColor="@android:color/darker_gray"
                    android:textSize="12sp" />

                <TextView
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="---" />

                <TextView
                    android:id="@+id/endTime_dzxMain"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="请选择结束时间"
                    android:textColor="@android:color/darker_gray"
                    android:textSize="12sp" />
            </LinearLayout>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:orientation="horizontal" >

            <Button
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_gravity="bottom"
                android:layout_weight="1"
                android:background="@android:color/transparent"
                android:onClick="drawer_reset"
                android:text="重置" />

            <Button
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_gravity="bottom"
                android:layout_weight="1"
                android:background="@color/dzx_head_bg_color"
                android:onClick="drawer_confirm"
                android:text="确定"
                android:textColor="@android:color/white" />
        </LinearLayout>
    </LinearLayout>
    //侧滑栏的内容布局从这里结束
</android.support.v4.widget.DrawerLayout>
```
### android:textColor="@color/dzx_text_selector"//该属性设置控件字体颜色的selector,其selector文件位于color资源文件夹下
```java 
<selector xmlns:android="http://schemas.android.com/apk/res/android" >
    <item android:state_checked="true" android:color="@android:color/white"></item>
    <item android:state_checked="false" android:color="@android:color/darker_gray"></item>
</selector>
```
### android:background="@drawable/dzx_radiobutton_selector"//设置控件被选中时的背景颜色，该selector位于drawable资源文件夹中，其内容如下：
```java
<selector xmlns:android="http://schemas.android.com/apk/res/android" >
    <item android:state_checked="true" android:drawable="@drawable/dzx_radiobutton_checked_bg"></item>
	<item android:state_checked="false" android:drawable="@drawable/dzx_search_radiobutton_bg"></item>
</selector>
```
### dzx_search_radiobutton_bg.xml
```java
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle"
     >
    <corners android:radius="5dp"></corners>
	<stroke android:color="@android:color/darker_gray" android:width="3px"></stroke>
	<padding android:left="5dp" android:top="5dp" android:right="5dp" android:bottom="5dp"/>
</shape>
```
### dzx_radiobutton_checked_bg.xml
```java
<shape xmlns:android="http://schemas.android.com/apk/res/android" 
    android:shape="rectangle"
    >
    <corners android:radius="5dp"></corners>
	<stroke android:color="@color/dzx_head_bg_color" android:width="3px"></stroke>
	<padding android:left="5dp" android:top="5dp" android:right="5dp" android:bottom="5dp"/>
	<solid android:color="@color/dzx_head_bg_color"></solid>
</shape>
```
### 侧滑界面的控件
```java
DrawerLayout drawer;// 筛选的抽屉布局
RadioGroup rg1;// 设施类型的radioGroup
RadioGroup rg2_1;// 经费预算的radioGroup的第一行
RadioGroup rg2_2;// 经费预算的radioGroup的第二行
RadioGroup rg3_1;// 项目总量的radioGroup的第一行
RadioGroup rg3_2;// 项目总量的radioGroup的第二行
RadioGroup rg4_1;// 项的开工时间的radioGroup的第一行
RadioGroup rg4_2;// 项目的开工时间的radioGroup的第二行
RadioButton rg1_rb1;// 桥梁
RadioButton rg1_rb2;// 道路
RadioButton rg2_rb1;// 10万以内
RadioButton rg2_rb2;// 10-20万元
RadioButton rg2_rb3;// 20-50万元
RadioButton rg2_rb4;// 50-100万元
RadioButton rg2_rb5;// 100万元以上
RadioButton rg3_rb1;// 1千平方米以内
RadioButton rg3_rb2;// 1-5千平方米
RadioButton rg3_rb3;// 5千-1万平方米
RadioButton rg3_rb4;// 1万平方米以上
TextView startTime;// 筛选界面的开始时间
TextView endTime;// 筛选界面的结束时间
Map<String, String> condition_map;// 存放筛选界面的条件的map
    
// 初始化radioButton，radioGroup和condition_map的方法
private void initRadioView() {
rg1 = (RadioGroup) findViewById(R.id.rg1);
rg2_1 = (RadioGroup) findViewById(R.id.rg2_1);
rg2_2 = (RadioGroup) findViewById(R.id.rg2_2);
rg3_1 = (RadioGroup) findViewById(R.id.rg3_1);
rg3_2 = (RadioGroup) findViewById(R.id.rg3_2);
rg1_rb1 = (RadioButton) findViewById(R.id.rg1_rb1);
rg1_rb1.setOnClickListener(this);
rg1_rb2 = (RadioButton) findViewById(R.id.rg1_rb2);
rg1_rb2.setOnClickListener(this);
rg2_rb1 = (RadioButton) findViewById(R.id.rg2_rb1);
rg2_rb1.setOnClickListener(this);
rg2_rb2 = (RadioButton) findViewById(R.id.rg2_rb2);
rg2_rb2.setOnClickListener(this);
rg2_rb3 = (RadioButton) findViewById(R.id.rg2_rb3);
rg2_rb3.setOnClickListener(this);
rg2_rb4 = (RadioButton) findViewById(R.id.rg2_rb4);
rg2_rb4.setOnClickListener(this);
rg2_rb5 = (RadioButton) findViewById(R.id.rg2_rb5);
rg2_rb5.setOnClickListener(this);
rg3_rb1 = (RadioButton) findViewById(R.id.rg3_rb1);
rg3_rb1.setOnClickListener(this);
rg3_rb2 = (RadioButton) findViewById(R.id.rg3_rb2);
rg3_rb2.setOnClickListener(this);
rg3_rb3 = (RadioButton) findViewById(R.id.rg3_rb3);
rg3_rb3.setOnClickListener(this);
rg3_rb4 = (RadioButton) findViewById(R.id.rg3_rb4);
rg3_rb4.setOnClickListener(this);
startTime = (TextView) findViewById(R.id.startTime_dzxMain);
startTime.setOnClickListener(this);
endTime = (TextView) findViewById(R.id.endTime_dzxMain);
endTime.setOnClickListener(this);
condition_map = new HashMap<String, String>();
condition_map.put("faceType", "");
condition_map.put("money", "");
condition_map.put("totalNum", "");
condition_map.put("startTime", "");
condition_map.put("endTime", "");
	}
// radioGroup和radioButton的点击方法,当他们被点击时为condition_map设置值
@Override
public void onClick(View v) {
// TODO Auto-generated method stub
switch (v.getId()) {
    case R.id.rg1_rb1:
	condition_map.put("faceType", "B03");
	break;
	case R.id.rg1_rb2:
			condition_map.put("faceType", "B01");
			break;
		case R.id.rg2_rb1:
			rg2_2.clearCheck(); //为了实现同一类型的筛选条件能够实现多行，在同一类型的radioGroup被点击时，清空该类型的其他radioGroup。
			condition_map.put("money", "10~t");
			break;
		case R.id.rg2_rb2:
			rg2_2.clearCheck();
			condition_map.put("money", "10~t20");
			break;
		case R.id.rg2_rb3:
			rg2_2.clearCheck();
			condition_map.put("money", "20~t50");
			break;
		case R.id.rg2_rb4:
			rg2_1.clearCheck();
			condition_map.put("money", "50~t100");
			break;
		case R.id.rg2_rb5:
			rg2_1.clearCheck();
			condition_map.put("money", "100~t");
			break;
		case R.id.rg3_rb1:
			rg3_2.clearCheck();
			condition_map.put("totalNum", "1000~t");
			break;
		case R.id.rg3_rb2:
			rg3_2.clearCheck();
			condition_map.put("totalNum", "1000~t5000");
			break;
		case R.id.rg3_rb3:
			rg3_2.clearCheck();
			condition_map.put("totalNum", "5000~t10000");
			break;
		case R.id.rg3_rb4:
			rg3_1.clearCheck();
			condition_map.put("totalNum", "10000~t");
			break;
		case R.id.startTime_dzxMain:
			getDate(startTime, "startTime");

			break;
		case R.id.endTime_dzxMain:
			getDate(endTime, "endTime");

			break;
		default:
			break;
		}
	}     
    
// drawerLayout设置时间的方法
	private void getDate(final TextView text, final String key) {
		Calendar calendar = Calendar.getInstance();
		my_year = calendar.get(Calendar.YEAR);
		my_mon = calendar.get(Calendar.MONTH);
		my_day = calendar.get(Calendar.DAY_OF_MONTH);
		date_dialog = new DatePickerDialog(DZXMainActivity.this, null, my_year, my_mon, my_day);
		date_dialog.setButton(AlertDialog.BUTTON_POSITIVE, "确定", new DialogInterface.OnClickListener() {

			@Override
			public void onClick(DialogInterface dialog, int which) {
				// TODO Auto-generated method stub
				DatePicker picker = date_dialog.getDatePicker();
				my_year = picker.getYear();
				my_mon = picker.getMonth() + 1;
				my_day = picker.getDayOfMonth();
				String str1 = "";
				String str2 = "";
				if (my_mon <= 9) {
					str1 = "0" + my_mon;
				} else {
					str1 = "" + my_mon;
				}
				if (my_day <= 9) {
					str2 = "0" + my_day;
				} else {
					str2 = "" + my_day;
				}
				date_str = my_year + "-" + str1 + "-" + str2;
				text.setText(date_str);
				condition_map.put(key, text.getText().toString());
				date_dialog.dismiss();
			}
		});
		date_dialog.show();

	}
  	// 筛选界面的确定按钮的方法
	public void drawer_confirm(View v) {
		drawer.closeDrawer(Gravity.END);
    //通过筛选条件进行拼接请求数据的URL
		String url = UrlUtil.MAIN_SERVER + "getDZXScheme.html?isFinished=" + isFinished + "&faceType="
				+ condition_map.get("faceType") + "&money=" + condition_map.get("money") + "&" + "totalNum="
				+ condition_map.get("totalNum") + "&startTime=" + condition_map.get("startTime") + "&endTime="
				+ condition_map.get("endTime") + "";
    //请求数据的方法
		getData(url);
	}
```
