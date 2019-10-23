# FcfrtMvp
FcfrtMvp+RxHttp+RxJava（Kotlin和JAVA共用完美支持）支持一键创建MVP项目，框架简约风格及详细注释，并于基于RxokHttp做为请求框架封装，一条链就能发送任意请求，主要优势如下 :

  **1. 一键创建Mvp项目，解决多个文件创建分不到头脑的问题**
  
  **2. 该框架只做为一个基础框架，方便开发工程师可根据自己的项目任意扩展，从而提高开发效率**
 
  **3. 支持Json、DOM等任意数据解析方式，可自定义数据解析器**
  
  **4. 支持Get、Post、Put、Delete等任意请求方式，可自定义请求方式**
  
  **5. 支持在Activity/Fragment/View/ViewModel/任意类中，自动关闭请求**
  
  **6. 支持统一加解密，且可对单个请求设置是否加解密**
  
  **7. 支持添加公共参数/头部，且可对单个请求设置是否添加公共参数/头部**
  
  **8. 史上最优雅的实现文件上传/下载及进度的监听，且支持断点下载**
  
  **9. 史上最优雅的对错误统一处理，且不打破Lambda表达式**
  
  **10. 史上最优雅的处理多个BaseUrl及动态BaseUrl**
  
  **11. 30秒即可上手，学习成本极低**

## 前言
由于本人文字功底不怎么样就不过多介绍如果有不懂的欢迎进群提问，如果觉得该框架可以的话给一个你宝贵的Star🙏，在此非常感谢RxHttp作者的大力支持。

# QQ群：574181465
## 准备工作
首先，我们需要把框架模版中的FcfrtMvpActivity框架模板复制在Android Studio 安装包下面的\plugins\android\lib\templates\activities\下

此时重起一下Android studio即可




## 接下来导入我们提供的demo中的根包名处点击new->Activity->FcfrtMvp

![image](https://github.com/FCFRT/FcfrtMvp-master/blob/master/img/创建Activity.png)

如图点击后，就会出现如下图所示更具自己的所需名称及内容填写即可：

![image](https://github.com/FCFRT/FcfrtMvp-master/blob/master/img/创建Activity2.png)


## FcfrtMvp框架时语言的选择

如上图所示只需要做下方选择Kotlin或者Java即可 均可以完美适配两种语言。

## FcfrtMvp布局规范
传统布局是这样的
**传统布局属性用方法**
```java
<androidx.constraintlayout.widget.ConstraintLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@color/colorPrimaryDark">
         <TextView
            android:id="@+id/tv_txt"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintBottom_toBottomOf="parent"
            android:gravity="center_vertical|center_horizontal"
            android:text="FcfrtMvp支持一键创建MVP框架。"
            android:textSize="20dp"/>
</androidx.constraintlayout.widget.ConstraintLayout>
```
**使用FcfrtMvp后**
```java
<androidx.constraintlayout.widget.ConstraintLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        style="@style/w_match_h_match"
        android:background="@color/colorPrimaryDark">
         <TextView
            android:id="@+id/tv_txt"
           style="@style/w_match_h_match"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintLeft_toLeftOf="parent"
            app:layout_constraintRight_toRightOf="parent"
            app:layout_constraintBottom_toBottomOf="parent"
            android:gravity="center_vertical|center_horizontal"
            android:text="FcfrtMvp支持一键创建MVP框架。"
            android:textSize="@dimen/font_size_40px"/>
</androidx.constraintlayout.widget.ConstraintLayout>
```
我们在框架类加入了布局样式及尺寸像素和字体大小模板，让代码更整洁，开发效率更高，例如：
字体大小设置：android:textSize="@dimen/font_size_40px" 代表字体：20sp
布局左边距：android:layout_marginLeft="@dimen/space_20"代表左边距：10dp

**使用FcfrtMvp框架中的权限一句话搞定**
```java
 FcfrtPermissionsUtil.requestPermission(this,object :FcfrtPermissionListener{
                /**
                 * 通过授权
                 * @param permission
                 */
                override fun permissionGranted(permission: Array<out String>) {
                    showToast("授权成功")
                }

                /**
                 * 拒绝授权
                 * @param permission
                 */
                override fun permissionDenied(permission: Array<out String>) {
                    showToast("授权失败")
                }
            },*FcfrtPermission.Group.STORAGE)
```
**使用FcfrtMvp框架中的权限配置类**
```java
object FcfrtPermission {

    const val REQUEST_INSTALL_PACKAGES = "android.permission.REQUEST_INSTALL_PACKAGES" // 8.0及以上应用安装权限

    const val SYSTEM_ALERT_WINDOW = "android.permission.SYSTEM_ALERT_WINDOW" // 6.0及以上悬浮窗权限

    const val READ_CALENDAR = "android.permission.READ_CALENDAR" // 读取日程提醒
    const val WRITE_CALENDAR = "android.permission.WRITE_CALENDAR" // 写入日程提醒

    const val CAMERA = "android.permission.CAMERA" // 拍照权限

    const val READ_CONTACTS = "android.permission.READ_CONTACTS" // 读取联系人
    const val WRITE_CONTACTS = "android.permission.WRITE_CONTACTS" // 写入联系人
    const val GET_ACCOUNTS = "android.permission.GET_ACCOUNTS" // 访问账户列表

    const val ACCESS_FINE_LOCATION = "android.permission.ACCESS_FINE_LOCATION" // 获取精确位置
    const val ACCESS_COARSE_LOCATION = "android.permission.ACCESS_COARSE_LOCATION" // 获取粗略位置

    const val RECORD_AUDIO = "android.permission.RECORD_AUDIO" // 录音权限

    const  val READ_PHONE_STATE = "android.permission.READ_PHONE_STATE" // 读取电话状态
    const val CALL_PHONE = "android.permission.CALL_PHONE" // 拨打电话
    const val READ_CALL_LOG = "android.permission.READ_CALL_LOG" // 读取通话记录
    const val WRITE_CALL_LOG = "android.permission.WRITE_CALL_LOG" // 写入通话记录
    const val ADD_VOICEMAIL = "com.android.voicemail.permission.ADD_VOICEMAIL" // 添加语音邮件
    const val USE_SIP = "android.permission.USE_SIP" // 使用SIP视频
    const val PROCESS_OUTGOING_CALLS = "android.permission.PROCESS_OUTGOING_CALLS" // 处理拨出电话
    const val ANSWER_PHONE_CALLS ="android.permission.ANSWER_PHONE_CALLS"// 8.0危险权限：允许您的应用通过编程方式接听呼入电话。要在您的应用中处理呼入电话，您可以使用 acceptRingingCall() 函数
    const val READ_PHONE_NUMBERS = "android.permission.READ_PHONE_NUMBERS"// 8.0危险权限：权限允许您的应用读取设备中存储的电话号码

    const val BODY_SENSORS = "android.permission.BODY_SENSORS" // 传感器

    const val SEND_SMS = "android.permission.SEND_SMS" // 发送短信
    const val RECEIVE_SMS = "android.permission.RECEIVE_SMS" // 接收短信
    const val READ_SMS = "android.permission.READ_SMS" // 读取短信
    const val RECEIVE_WAP_PUSH = "android.permission.RECEIVE_WAP_PUSH" // 接收WAP PUSH信息
    const val RECEIVE_MMS = "android.permission.RECEIVE_MMS" // 接收彩信

    const val READ_EXTERNAL_STORAGE = "android.permission.READ_EXTERNAL_STORAGE" // 读取外部存储
    const val WRITE_EXTERNAL_STORAGE = "android.permission.WRITE_EXTERNAL_STORAGE" // 写入外部存储

    const val RECEIVE_BOOT_COMPLETED ="android.permission.RECEIVE_BOOT_COMPLETED"//开机启动权限

    object Group {

        // 日历
        val CALENDAR = arrayOf(READ_CALENDAR, WRITE_CALENDAR)

        // 联系人
        val CONTACTS = arrayOf(READ_CONTACTS, WRITE_CONTACTS, GET_ACCOUNTS)

        // 位置
        val LOCATION = arrayOf(ACCESS_FINE_LOCATION, ACCESS_COARSE_LOCATION)

        // 存储
        val STORAGE = arrayOf( READ_PHONE_STATE, READ_EXTERNAL_STORAGE, WRITE_EXTERNAL_STORAGE )
    }
}
```
## 其他教程

**[RxHttp详细使用教程](https://github.com/liujingxing/RxHttp)**









