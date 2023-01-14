

关于 AVBook

AVBook 是基于 Laravel 开发的 Web 应用程序，通过 Artisan 控制台实现avmoo,javbus,javlibrary的爬虫采集数据入库mysql，前端页面模仿javbus，并添加一些类似javlibrary的功能。该系统相当于以上三个网站的结合体，能够使你更加方便地管理你的影片。
预览

（FBI WARNING：不要在公共场所打开以下图片）

underage 首页截图

underage 详情页截图
Get Started

git clone https://github.com/guyueyingmu/avbook.git

cd avbook;cp .env.example .env #复制 .env.example 为 .env 并设置数据库信息

composer install

php artisan migrate

#替换  avbook/config/urlconfig.php  文件中的域名为最新域名 #从被墙域名获取：avmoo.com ;javbus.com;javlib.com

php artisan avbook:avmoo  #启动avmoo爬虫

php artisan avbook:javbus --movie=1 --page=10 --magpage=10 #启动javbus爬虫

php artisan scandir --path='/moviefiles' #扫描指定目录moviefiles中的文件，正则匹配番号，设置为已拥有状态

php artisan avbook:javlib --genre --movie  #javlibrary爬虫

以上操作适用于Linux环境
For windows 用户

这里提供一份开箱即用的压缩包 avbook_laragon.7z

链接：https://pan.baidu.com/s/1LPeGNNy-3MEDC0g9EbusLg 提取码：gmmg

压缩包中包含更新到2019.5.12的全部数据
使用方法:

    1.解压到 D:\laragon
    2.打开 D:\laragon\laragon.exe ,点击 启动所有
    3.点击 网站 或者访问 http://avbook.test enjoy it

    ps:
    Ⅰ. 如果没有解压到 D:\laragon 需自行修改Nginx配置，并在hosts文件新增一行 ：127.0.0.1      avbook.test
    Ⅱ. laragon终端启动爬虫前先 git pull 更新到最新版本。

其他注意事项

avmoo 有反爬虫机制，目前的反反爬虫方法是修改 User-Agent ，用的人多了应该会失效，建议下载avbook_laragon.7z导入数据库，进行增量更新。

windows 下 mysql 性能有限，需耐心等待，建议将数据库导入 homestead 使用。

在带宽够用的情况下 php artisan avbook:avmoo --max=500 将并发设置为500可在1小时内采集完 avmoo 全站30余万条电影信息，并发过大时建议使用 SMProxy 加一层连接池提高速度。

必须等 avmoo 采集完成，才能启动 javbus 爬虫。

最后，北京第三区交通委提醒您：道路千万条，安全第一条。飙车一时爽，一直飙一直爽。。。
License

The AVBook is open-source software licensed under the MIT license.
