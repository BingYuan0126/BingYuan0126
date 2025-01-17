#  Youbike站點推薦系統前端網頁製作
 使用技術
-   Bootstrap5.2.3
-   JQuery
-  Font Awesome 圖標庫
   ## 環境布置
   在head底下輸入
  下方程式碼為引用Bootstrap5.2.3
    ```
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
    ```
    引用Font Awesome 圖標庫
    ```
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    ```
    在body的最底下引用
    ```
    <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha384-KyZXEAg3QhqLMpG8r+Knujsl5+5hb7ie2ElVx2Lt5PLOME6/JCMVWvD2qxCUV6MG" crossorigin="anonymous"></script>
    ```
    此兩段程式碼為Bootstrap官方說明如要使用官方組件需添加的js
    Popper.js 来处理定位和弹出效果
    ```
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js" integrity="sha384-oBqDVmMz9ATKxIep9tiCxS/Z9fNfEXiDAYTujMAeBAsjFuCZSmKbSSUnQlmh/jp3" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.min.js" integrity="sha384-cuYeSxntonz0PPNlHhBs68uyIAVpIIOZZ5JqeqvYYIcEL727kskC66kF92t6Xl2V" crossorigin="anonymous"></script>
    ```
  ## 開始製作網頁

  ### 直接導入Bootstrap官方的導航欄組件
    ```
    <nav class="navbar navbar-dark bg-dark fixed-top navbar-expand-lg">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">YouBike最佳站點推薦系統</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasDarkNavbar" aria-controls="offcanvasDarkNavbar">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="offcanvas offcanvas-end text-bg-dark" tabindex="-1" id="offcanvasDarkNavbar" aria-labelledby="offcanvasDarkNavbarLabel">
                <div class="offcanvas-header">
                    <h5 class="offcanvas-title" id="offcanvasDarkNavbarLabel">YouBike最佳站點推薦系統</h5>
                    <button type="button" class="btn-close btn-close-white" data-bs-dismiss="offcanvas" aria-label="Close"></button>
                </div>
                <div class="offcanvas-body">
                    <ul class="navbar-nav justify-content-center flex-grow-1 pe-3">
                        <li class="nav-item">
                            <a class="nav-link active" aria-current="page" href="{% url 'io' %}">首頁</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="{% url 'bikemap' %}">站點地圖</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="{% url 'bike' %}">腳踏車步道</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="{% url 'food' %}">YouBike米其淋</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="{% url 'chart' %}">站點地圖分析</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="{% url 'member' %}">會員專區</a>
                        </li>
                        <li class="nav-item">
                            <a class="nav-link" href="{% url 'about_us' %}">關於我們</a>
                        </li>
                    </ul>
                    <ul class="navbar-nav justify-content-end flex-grow-2 pe-3">
                        <li class="nav-item">
                            <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
                                登入/註冊
                              </button>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </nav>
    ```
    
  ### 新增官方模態框 
    ```
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
            <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">登入</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body">
                <form>
                    <div class="mb-3">
                        <label for="username" class="form-label">帳號</label>
                        <input type="text" class="form-control" id="username" placeholder="請輸入帳號">
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">密碼</label>
                        <input type="password" class="form-control" id="password" placeholder="請輸入密碼">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">登入</button>
            <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#registerModal">
                註冊
            </button>

            </div>
        </div>
        </div>
    </div>
    ```
  ### 新增點擊註冊按鈕時跳入註冊的模態框
    ```
    <!-- Register Modal -->
    <div class="modal fade" id="registerModal" tabindex="-1" aria-labelledby="registerModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="registerModalLabel">註冊</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form>
                        <div class="mb-3">
                            <label for="registerUsername" class="form-label">帳號</label>
                            <input type="text" class="form-control" id="registerUsername" placeholder="請輸入帳號">
                        </div>
                        <div class="mb-3">
                            <label for="registerPassword" class="form-label">密碼</label>
                            <input type="password" class="form-control" id="registerPassword" placeholder="請輸入密碼">
                        </div>
                        <div class="mb-3">
                            <label for="registerCarrier" class="form-label">電信</label>
                            <select class="form-control" id="registerCarrier">
                              <option value="">請選擇電信</option>
                              <option value="chunghwa">中華電信</option>
                              <option value="taiwanmobile">台灣大哥大</option>
                              <option value="fareastone">遠傳電信</option>
                              <option value="tstar">台灣之星</option>
                              <option value="apt">亞太電信</option>
                            </select>
                          </div>
                        <div class="mb-3">
                            <label for="registerEmail" class="form-label">電子郵件</label>
                            <input type="email" class="form-control" id="registerEmail" placeholder="請輸入電子郵件">
                        </div>
                        <button type="submit" class="btn btn-primary">註冊</button>
                    </form>
                </div>
            </div>
    ```
        </div>
    </div>

  ### 導入Bootstrap官方輪播圖
  ```
  <div class="custom-imgbackground">
        <div id="carouselExampleCaptions" class="carousel slide" data-bs-ride="false">
            <div class="carousel-indicators">
              <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
              <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="1" aria-label="Slide 2"></button>
              <button type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide-to="2" aria-label="Slide 3"></button>
            </div>
            <div class="carousel-inner">
              <div class="carousel-item active">
                <img src="#圖片放置處" class="d-block w-100" alt="...">
                <div class="carousel-caption d-none d-md-block">
                  <h5>標題1</h5>
                  <p>介紹1</p>
                </div>
              </div>
              <div class="carousel-item">
                <img src="#圖片放置處" class="d-block w-100" alt="...">
                <div class="carousel-caption d-none d-md-block">
                  <h5>標題2</h5>
                  <p>介紹2</p>
                </div>
              </div>
              <div class="carousel-item">
                <img src="#圖片放置處" class="d-block w-100" alt="...">
                <div class="carousel-caption d-none d-md-block">
                  <h5>標題3</h5>
                  <p>介紹3</p>
                </div>
              </div>
            </div>
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
              <span class="carousel-control-prev-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
              <span class="carousel-control-next-icon" aria-hidden="true"></span>
              <span class="visually-hidden">Next</span>
            </button>
          </div>
    </div>
  ```
### 新增Yt影片區
#### 創建了三個div
- 第一個為yt影片的背景圖片
- 第二個為影片的鑲嵌位置
- 第三個為為影片添加一層半透明的覆蓋用於讓使用者無法點擊影片
```
<div class="video-background">
    <div class="video-container">
        <div class="video-overlay"></div>
        <img src="https://img.youtube.com/vi/yZkG1chgLz4/maxresdefault.jpg" class="video-placeholder" alt="Video loading placeholder">
        <iframe
            src="https://www.youtube.com/embed/yZkG1chgLz4?autoplay=1&controls=0&mute=1&loop=1&playlist=yZkG1chgLz4&playsinline=1&fs=0&iv_load_policy=3&modestbranding=1&rel=0&showinfo=0&start=9"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen
            onload="this.previousElementSibling.style.display='none';">
        </iframe>
    </div>
</div>
```
### 新增布告欄
```
<div class="announcement-board">
        <h1>公告欄</h1>
        <ul>
            <li>2024/06/11(二) 09:00-13:00 新北市 永和區 YouBike 2.0『中正路666巷口』 暫停營運</li>
            <li>2024/06/06(五) 10:00 台北市 新增大安區1站 YouBike 2.0 正式營運公告</li>
            <li>2024/06/5(五)及06/07(五)09:00 - 16:00，06/08(六)及06/09(日)08:00 - 20:00新北市 中和區YouBike 2.0『捷運中原站』、『板南路492號』、『板南立言街口』 暫停營運</li>
            <li>2024/06/04(二) - 06/30(日) 新北市 新莊區 60 站 YouBike 1.0 場站升級營運公告</li>
            <li>2024/06/04(二) 即刻起-06/08(六)00:00 新北市 新莊區 YouBike 2.0『龍安福營路口』 暫停營運</li>
            <li>溫馨提醒 - 2024/06/04(二) 起 新北市 新莊區 YouBike 2.0 『龍安福營路口』因現場施工，請注意騎乘安全</li>
            <li>2024/06/04 (二) 10:00 台北市 新增大安區1站 YouBike 2.0 正式營運公告</li>
            <li>2024/06/01(六) 08:00 - 06/02(日) 23:00 新北市 三重區YouBike 1.0及YouBike 2.0『先嗇宮』暫停營運</li>
            <li>2024/06/03 (一) 09:00 - 17:00 台北市 大安區YouBike 2.0『臨江公園』暫停營運</li>
            <li>2024/06/01(六) 08:00-20:00 新北市 三重區 YouBike 2.0『三重區停八停車場』 暫停營運</li>
        </ul>
    </div>
```
### 新增底層欄位
#### 這邊用到了Font Awesome的圖標
- class="social-icon facebook"><i class="fab fa-facebook></i> 導入圖標
- fa-3x則是調整大小
```
<div class="custom-background2">
        <div class="container">
            <div class="row">
                <div class="col-md-6 contact-info">
                    <h2>聯繫我們</h2>
                    <p>電話: 123-456-789</p>
                    <p>Email: info@youbike.com</p>
                </div>
                <div class="col-md-6 social-software">
                    <h2>社交媒體</h2>
                    <a href="https://www.facebook.com/youbike" class="social-icon facebook"><i class="fab fa-facebook fa-3x"></i></a>
                    <a href="https://www.instagram.com/youbike_tw/" class="social-icon instagram"><i class="fab fa-instagram fa-3x"></i></a>
                    <a href="https://www.linkedin.com/company/youbike" class="social-icon line"><i class="fab fa-line fa-3x"></i></a>
                    <a href="https://www.youtube.com/youbike" class="social-icon youtube"><i class="fab fa-youtube fa-3x"></i></a>
                    <a href="https://discord.com/youbike" class="social-icon discord"><i class="fab fa-discord fa-3x"></i></a>
                </div>
            </div>
        </div>
    </div>
```
 


    

    
