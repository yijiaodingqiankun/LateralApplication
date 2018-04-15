

侧滑菜单的最基本用法


1.首先它是一个布局，support-v4包下的，放在xml布局的最外层
2.在布局中只允许放2个直接子控件或子布局，第一个子控件是主屏幕中显示的内容，第二个子控件是滑动菜单中显示的内容
<?xml version="1.0" encoding="utf-8"?>
<android.support.v4.widget.DrawerLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    tools:context="com.jiyun.lateralapplication.MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <android.support.v7.widget.Toolbar
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:background="?attr/colorPrimary" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="主菜单显示的内容" />
    </LinearLayout>

    <TextView
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_gravity="start"
        android:background="#fff"
        android:text="侧滑菜单中显示的内容"
        android:textSize="30sp" />
</android.support.v4.widget.DrawerLayout>

3.第二个子控件要注意：android:layout_gravity="start"这个属性是必须指定的，因为我们要告诉DrawerLayout侧滑菜单是在屏幕的左边还是右边，left表示在左边，right表示在右边。start表示会根据系统语言进行判断，如果系统语言是从左往右的，比如英语、汉语，侧滑菜单就在左边，如果系统语言是从右往左的，比如阿拉伯语，侧滑菜单就在右边。


其他知识点：
//            让导航按钮显示出来
            actionBar.setDisplayHomeAsUpEnabled(true);

//            设置一个导航按钮图标
            actionBar.setHomeAsUpIndicator(R.mipmap.ic_launcher);

            Toolbar最左侧的按钮叫作HomeAsUp,默认是一个返回的箭头，含义是返回上一个活动

            HomeAsUp按钮的id永远都是android.R.id.home
            DrawerLayout的openDrawer()方法将滑动菜单展示出来，注意openDrawer()方法要求传人一个Gravity参数，为了保证这里的行为和Xml中定义的一致，我们传人了GravityCompat.START

 -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
            NavigationView要注意的点
            1.添加依赖 （design）compile 'com.android.support:design:26.0.0-alpha1'
            2.在res文件夹下创建menu文件夹，在menu文件夹下创建Menu resource file(xml)布局文件。
            3.在layout文件夹下创建headlayout，xml。
            menu是线上具体的菜单项的，headlayout是显示头布局的。
<android.support.design.widget.NavigationView
    android:id="@+id/nav"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_gravity="start"
    app:headerLayout="@layout/head"
    app:menu="@menu/nav_menu" />
注意红色的三行代码一定要有（也就是最后3行代码），最后侧滑菜单的监听等功能，自己加。

