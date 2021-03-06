# 图形解锁

## 效果
![img](https://github.com/mzyq/LockView/blob/master/img/preview.gif)

[APK下载](https://fir.im/xb47)

## 依赖
[![](https://jitpack.io/v/mzyq/LockView.svg)](https://jitpack.io/#mzyq/LockView)
### Gradle
```
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```

```
dependencies {
	        compile 'com.github.mzyq:LockView:{VERSION}'
	}
```
### Maven
```
<repositories>
		<repository>
		    <id>jitpack.io</id>
		    <url>https://jitpack.io</url>
		</repository>
	</repositories>
```
```
<dependency>
	    <groupId>com.github.mzyq</groupId>
	    <artifactId>LockView</artifactId>
	    <version>{VERSION}</version>
	</dependency>
```

## 用法
```
<com.muzi.library.LockView
        android:id="@+id/lockView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:count="3"
        app:try_num="5"/>
```

* count:显示三行三列
* try_num:点击5次后不可点击，调用``` setReset()```可重置，如果设置-1，一直可用。
  (**必须设置默认的密码，才能生效。**)


## 方法
* setReset():清空当前选项，并可以点击
* setPsd(List<Interge> psd):设置默认密码
* 回调
```
setOnLockState(new LockView.OnLockState() {
            @Override
            public void onError() {
                Toast.makeText(MainActivity.this, "密码错误", Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onSuccess() {
                Toast.makeText(MainActivity.this, "密码正确", Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onUnable() {
                Toast.makeText(MainActivity.this, "不可用", Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onPassWord(List<Integer> psd) {
                builder.setLength(0);
                for (Integer integer : psd) {
                    builder.append(integer);
                }
                Toast.makeText(MainActivity.this, "输入密码:" + builder.toString(), Toast.LENGTH_SHORT).show();
            }
        });
```

## License
```
Copyright 2018 MuZi

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
