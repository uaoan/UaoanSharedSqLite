# UaoanSharedSqlite
 封装SharedPreferences，数据共享
### 集成
 **1.在 project 的 settings.gradle 文件中找到 allprojects{} 代码块添加以下代码：** 

```
allprojects {
    repositories {
        mavenCentral()
        maven { url 'https://jitpack.io' }      //增加 jitPack Maven 仓库
    }
}
```
 **在 app 的 build.gradle 文件中找到 dependencies{} 代码块，并在其中加入以下语句：** 

```
implementation 'com.github.uaoan:UaoanSharedSqlite:1.0'
```


```
//创建UaoanSharedSqlite
UaoanSharedSqlite sqlite=new UaoanSharedSqlite();

//初始化，"uaoan"为表命
sqlite.init(this,"uaoan");

//写入数据
sqlite.putBoolean("title",false); //布尔型等等...
putFloat()
putInt()
putLong()
putString()

//写入一个合集
sqlite.putStringList("title", new UaoanSharedSqlite.StringSet() {
            @Override
            public void put(Set<String> name) {
                name.add("七桐");
                name.add("uaoan");
            }
        });

//获取读取数据
sqlite.getBoolean("title"); //获取布尔型等等...
getFloat()
getInt()
getLong()
getString()

//获取全部数据
sqlite.getAllList(new UaoanSharedSqlite.AllList() {
            @Override
            public void getList(String name, String key, Map.Entry<String, ?> entry) {
                
            }
        });

//删除数据
sqlite.remove("title");

//清除表数据
clear()

//修改数据
set("title","uaoan");

//添加一个监听器，当SharedPreferences 中的数据发生变化时会收到通知。
sqlite.setOnUaoanSharedSqliteChangeListener(new UaoanSharedSqlite.OnUaoanSharedSqliteChangeListener() {
            @Override
            public void onSharedPreferenceChanged(SharedPreferences sharedPreferences, String key) {
                Toast.makeText(MainActivity.this, "数据更新了"+key, Toast.LENGTH_SHORT).show();
            }
        });

//注销注册的监听器。
sqlite.removeOnUaoanSharedSqliteChangeListener();
```
