# Cordova Plugin快速搭建入门(cordova 8.0环境)

## 示例
1. 创建一个名为toast的插件，plugman create --name MyToast --plugin_id com.hrj.demo.toast --plugin_version 1.0.0
2. 进入MyToast目录，输入plugman platform add --platform_name android，还需要手动修改一下，见模板（往下看）
3. 在toast目录里创建package.json，输入plugman createpackagejson ./
    （询问别名时输入MyToast）
4. cordova plugin add <路径>，例如：cordova plugin add ../ionicPluginDemo/MyToast

## 其他命令
1. 查看cordova版本
    cordova -v

2. 创建工程
    cordova create testapp com.my.testapp
    cd testapp
    cordova platform add android

3. 查看插件列表
    cordova plugin list
    
4. 移除某一个插件
    cordova plugin remove com.hrj.demo.toast

5. 另一个引用插件方式
    cordova plugin add ../ionicPluginDemo/MyToast

## plugin.xml模板
<?xml version='1.0' encoding='utf-8'?>
<plugin xmlns:android="http://schemas.android.com/apk/res/android"
    id="com.hrj.demo.toast"
    version="1.0.0"
    xmlns="http://apache.org/cordova/ns/plugins/1.0">
    <name>MyToast</name>
    <js-module
        name="MyToast"
        src="www/MyToast.js">
        <clobbers target="cordova.plugins.MyToast" />
    </js-module>
    <platform name="android">
        <config-file
            parent="/*"
            target="res/xml/config.xml">
            <feature name="MyToast">
                <param
                    name="android-package"
                    value="com.hrj.demo.toast.MyToast" />
            </feature>
        </config-file>
        <config-file
            parent="/*"
            target="AndroidManifest.xml"></config-file>
        <source-file
            src="src/android/MyToast.java"
            target-dir="src/com/hrj/demo/toast" />
    </platform>
</plugin>



