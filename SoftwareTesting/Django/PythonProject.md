# 五天Django学习+项目实战

## 1 Day1

### 1.1 orm

#### 1.1.1 创建数据库

`create database day15 DEFAULT CHARSET utf8 COLLATE utf8_general_ci`

#### 1.1.2 Django连接数据库

在settings文件中进行配置和修改

```
DATABASES = {
     'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME':  'sms',
        'USER': 'root',
        'PASSWORD': '1234560',
        'HOST': '127.0.0.1',
        'PORT': 3306
     }
}
```

#### 1.1.3 Django操作表

创建表，在models.py中

```Python
class UserInfo(models.Model):
    name = models.CharField(max_length=32)
    password = models.CharField(max_length=64)
    age = models.IntegerField()
```

执行命令，在终端中输入以下两条命令：

```
python manage.py makemigrations
python manage.py migrate
```

在表中新增列时，必须要对新增列指定数据：

* 手动输入一个值
* 指定默认值
* 允许为空

#### 1.1.4 操作表中的数据

#### 1.1.5 案例：用户管理

##### (1) 展示用户列表

* url
* 函数
  * 获取所有的用户信息
  * HTML渲染

insert into app01_userinfo(name, password, age) values ("张三", "123", 18);

insert into app01_userinfo(name, password, age) values ("李四", "1235", 28);

##### (2) 添加用户

* url
* 函数
  * GET：显示页面，输入内容
  * POST：提交->添加到数据库