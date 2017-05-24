# NotePad
This is an AndroidStudio rebuild of google SDK sample NotePad
### 一.实现功能如下：
### 基础功能
#### 1.NoteList中显示条目增加时间戳显示
#### 2.添加笔记查询功能（根据标题查询）
### 附加功能
#### 3.UI美化
#### 4.更改记事本主页面的背景
#### 5.笔记分类
#### 6.更改编辑框页面背景

### 二.代码实现
####  1.运用TextWatcher 实时监听EditText搜索框里输入内容的变化 public void onTextChanged(CharSequence charSequence, int i, int i1, int i2)，实现了实时搜索
Cursor cursor = managedQuery(
                getIntent().getData(),            
                PROJECTION,
                //获取editText搜索框中的内容                                           
                NotePad.Notes.COLUMN_NAME_TITLE + "  like  ?",                             
                new  String[]{editText.getText().toString()+"%" },                           
                NotePad.Notes.DEFAULT_SORT_ORDER  
        );
####  2.运用sharedPreferences保存和读取主页面背景颜色，实现对背景色的修改
//创建一个sharedPreferences,保存在文件名为Color的文件中
sharedPreferences=getSharedPreferences("Color",MODE_ENABLE_WRITE_AHEAD_LOGGING);
//初始化sharedPreferences
//SharedPreferences.Editor editor=sharedPreferences.edit();
//editor.putInt("name",123);
color=sharedPreferences.getInt("color",Color.WHITE);

####  3.运用Spinner组件实现分类功能NotePad.Notes.spinner=(Spinner)findViewById(R.id.spinner);
//运用Spinner组件
NotePad.Notes.spinner=(Spinner)findViewById(R.id.spinner);
String arr[]={"全部","学习","工作","其他"};
ArrayAdapter<String> adapter=new ArrayAdapter<String>(this,android.R.layout.simple_list_item_multiple_choice,arr);
NotePad.Notes.spinner.setAdapter(adapter);
mCursor.moveToFirst();
NotePad.Notes.spinner.setSelection(mCursor.getInt(4));

####  4.修改显示时间格式SimpleDateFormat simpleFormatter=new SimpleDateFormat("yyyy/MM/dd HH:mm:ss")

####  具体改动参看源码

### 三.功能演示
#### 1.主页面
![pic1](https://github.com/Zhangluying/NotePad-master/blob/master/pic/1.png)
#### 2.创建一个新的笔记后可以对其分类进行选择
![pic2](https://github.com/Zhangluying/NotePad-master/blob/master/pic/2.png)
#### 3.长按编辑框可以对编辑框的背景颜色进行选择
![pic3](https://github.com/Zhangluying/NotePad-master/blob/master/pic/3.png)
#### 选择好颜色后的效果：
![pic4](https://github.com/Zhangluying/NotePad-master/blob/master/pic/4.png)
#### 4.创建好的文件会自动显示其创建（修改）时间及分类
![pic5](https://github.com/Zhangluying/NotePad-master/blob/master/pic/5.png)
#### 5.在主页面的上方有一个设置背景色的按钮，点击后弹出颜色板提供颜色的选择
![pic6](https://github.com/Zhangluying/NotePad-master/blob/master/pic/6.png)
#### 修改颜色后的效果：
![pic7](https://github.com/Zhangluying/NotePad-master/blob/master/pic/7.png)
#### 6.在搜索框中输入搜索关键字将会进行实时搜索
![pic8](https://github.com/Zhangluying/NotePad-master/blob/master/pic/8.png)
![pic9](https://github.com/Zhangluying/NotePad-master/blob/master/pic/9.png)
