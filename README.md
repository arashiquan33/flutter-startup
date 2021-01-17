# flutter_startup

learn flutter base content

# flutter-issue-summary

flutter常见问题汇总

### android emulator closed because of an internal error

仿真机启动报错，https://www.iditect.com/how-to/54759286.html

### running gradle tash assembleDebug 报错，下载gradle失败

https://www.freesion.com/article/58001056925/

https://www.cnblogs.com/phen/p/13427912.html

https://www.cnblogs.com/letfly/p/13811457.html

最后无奈，在线下载gradle,使用第三个链接地址给出的方案

### run 报错，Could not resolve all artifacts for configuration ':classpath'.    > Could not find com.android.tool，从maven.aliyun下载失败

重新配置项目下andriod/build.gradle

https://www.cnblogs.com/022414ls/p/13469136.html

### row组件不设置textDirection，报错

Horizontal RenderFlex with MainAxisAlignment.start has a null textDirection, so the alignment cannot be resolved.

row源码里记载了，大概意思就是当row没有children或者只有一个，或者mainAxisAlignment属性设置为start或者end，默认为start，这两种情况时，需要设置文字方向

```js

/// The [textDirection] argument defaults to the ambient [Directionality], if
  /// any. If there is no ambient directionality, and a text direction is going
  /// to be necessary to determine the layout order (which is always the case
  /// unless the row has no children or only one child) or to disambiguate
  /// `start` or `end` values for the [mainAxisAlignment], the [textDirection]
  /// must not be null.
```

### No direction widget found

flutter布局有个概念，是文字方向，有的组件构造函数里可以设置textDirection,有的不行，如果要全局统一设置，其中一个办法是最外层使用 Directionality

```js
  Widget build(BuildContext context) {
    //Directionality 最上层设置文字方向
    return Directionality(
      textDirection: TextDirection.ltr,
      child: Container(
        margin:EdgeInsets.fromLTRB(0, 25, 0, 0),
        decoration: BoxDecoration(color: Color.fromRGBO(138,197,241,1)),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          children: [
            header,
            body,
            footer
          ],
        ),
      ),
    );
  }

```
