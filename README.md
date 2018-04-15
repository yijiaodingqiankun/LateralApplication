
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


