# 网易云音乐API

## NetEase(self)

### 函数

- `__init__(self)`
> 初始化函数，定义请求头和新建会话Session；
- `toplists(self)`
> 返回热门分类；
- `logout(self)`
> 登出；
- `_raw_request(self,method,endpoint,data)`

> **两个必传参数**：
>> **method**请求方法，post或者get;
>> **endpoint**

> **一个可选参数data**：
>> 在get方法中是params，post方法中是data；

> **返回值**是请求的response；

- `make_cookie(self, name, value)`
> **两个必传参数，返回初始cookie值；**

- `JavaScript解密方法`
> **encrypted_request(self,text)**  
> **aes(self,text,key)**  
> **rsa(self,text,pubkey,modulus)**  
> **create_key(self,size)**

> 一个必传参数text,即为params；
>> **这四个方法用来构成解密请求，详细构造过程是由JavaScript生成；**

- `request(self,method,path,params={},default={'code':-1},custom_cookies={'os':'pc'})`
> **endpoint**  
> **crsf_token**是cookie中的一个必带参数，从cookie中解析而来；  
> **params**为解密参数，在浏览器F12中可以看到，如果不带请求不到数据；  
> **异常处理捕捉RequestException和ValueError**  
>> 处理方式为写入log，最终返回data，出错时返回default；  

- `login(self,username,password)`
> **登录函数,接收参数为帐号和密码**；  
>> 还有另外一种登录方式，见源码；

- `daily_task(self,is_mobile=True)`
> 默认参数is\_mobile值为True，在移动端签到；

- `user_playlist(self,uid,offset=0,limit=50)` 
> **用户歌单**：
>> uid：用户id；  
>> offset：偏移量，默认为0；  
>> limit：返回数量，默认为50；

- `recommend_resource(self)`
> **每日推荐歌单**：
>> 请求方式为post；  
>> 直接返回推荐，登录时有效，未登录时返回空；  
>> **返回数据类型为list()**

- `recommend_playlist(self,total=True,offset=0,limit=20)`
> **每日推荐歌曲**：
>> 请求方式为post；  
>> 参数含义同上；  
>> 直接返回推荐，登录时有效，未登录时返回空；  
>> **返回数据类型为list()**

- `personal_fm(self)`
> **私人FM**：
>> 请求方式为post，无参数；

- `fm_like(self,songid,like=True,time=25,alg="itembased")`
> **收藏歌曲**：
> 参数alg含义未知；

- `fm_trash(self,songid,time=25,alg='RT')`
> **作用未知**：

- `search(self,keywords,stype=1,offset=0,totle="True",limit=50)`
> **搜索**：
>> keywords为搜索的关键字；  
>> style为搜索的类型，默认为1，即搜索单曲：  
>> style|含义  
>> ---|:---  
>> 1|单曲  
>> 100|歌手  
>> 10|专辑  
>> 1000|歌单  
>> 1002|用户  
>> *横向表格到底怎么打*  
>> 返回的数据类型为json；

- `new_albums(self,offset,limit)`
> **新碟上架**:
>> **返回数据类型为list();**

- `top_playlists(self,category="全部",order="hot",offset=0,limit=50)`
> **获取歌单，排序方式为热门，类型为全部**：
>> 具体类型详见[category](http://music.163.com/#/discover/playlist/);  
>> 如下图：![6b05d32c3325e0e920c5b2e76793b7d5](网易云音乐API.resources/1.jpg)  
>> **返回数据类型为list()**

- `playlist_catelogs(self)`
> **不知道是个啥**  
> **返回所有歌单类型，json**

- `playlist_detail(self,playlist_id)`
> **歌单详情**：
>> 返回歌单的歌曲名称及相关信息，list();

- `top_artists(self,offset=0,limit=100)`
> **热门歌手**：
>> 默认返回100个；

- `artists(self,artist_id)`
> **歌手单曲，好像是歌手主页的热门50首**
>> 确定是热门50首，类型为list()

- `get_artist_album(self,artist_id,offset=0,limit=50)`
> **歌手专辑**：
>> 好像是热门专辑;  
>> 确认返回热门50个专辑；

- `album(self,album_id)`
> **返回专辑的歌曲详情**

- `song_comments(self,music_id,offset=0,totle='false',limit=100)`
> **获取歌曲评论，默认获取50条**

- `songs_detail(self,ids)`
> **返回歌曲详情**：

- `songs_url(self,ids)`
> **返回歌曲的URL？**
>> quality、rate_map的意义未知；

- `song_lyric(self,music_id)`
> **返回歌曲歌词**
>> 返回类型为list；  
>> lv,kv,tv含义未知；

- `song_tlytic(self,music_id)`
> **含义未知**

- `djchannels(self,offset=0,limit=50)`
> ****
