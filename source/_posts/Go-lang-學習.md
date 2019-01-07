---
title: GO lang Hello World
date: 2018-10-17 17:27:08
categories:
- 學習
tags: 
- Go
- Visual Studio Code
---
# GO lang Hello World !


## 安裝 GO

1. 下載
https://golang.org/

![](https://i.imgur.com/nqkLVtr.png)

1. 選擇自己的作業系統

![](https://i.imgur.com/L4Xbr7h.png)

3. 安裝

![](https://i.imgur.com/L9HsVaY.png)

![](https://i.imgur.com/oRDbix1.png)

4. 測試GO 是否有安裝成功
![](https://i.imgur.com/n0W4ziL.png)


##  Visual Studio Code 開發

#### 安裝套件

![](https://i.imgur.com/qxy8dCo.png)


### Hello World

![](https://i.imgur.com/TrwsY6c.png)


```
package main
import "fmt"
func main() {
	fmt.Println("Hello, 世界")
}
```

## GO WebApi

### 簡單的 router 範例

![](https://i.imgur.com/KlzrTTI.png)

![](https://i.imgur.com/7xnUwXu.png)


```
package main
import (
	"fmt"
	"log"
	"net/http"
	"github.com/gorilla/mux"
)

func main() {
	router := mux.NewRouter().StrictSlash(true)
	router.HandleFunc("/", Index)
	router.HandleFunc("/news", News)
	router.HandleFunc("/news/{DetailID}", Detail)
	log.Fatal(http.ListenAndServe(":8080", router))
}

func Index(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Home!")
}

func News(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "最新消息 Master")
}

func Detail(w http.ResponseWriter, r *http.Request) {
	vars := mux.Vars(r)
	DetailID := vars["DetailID"]
	fmt.Fprintln(w, "最新消息 Detail ID:", DetailID)
}

```

## 參考網址

  [官方網站](https://golang.org/)
  [GO WEB API](https://tutorialedge.net/golang/creating-restful-api-with-golang/)
  [7個GO WEB API框架](https://nordicapis.com/7-frameworks-to-build-a-rest-api-in-go/)
  [微服務 GO](https://nordicapis.com/writing-microservices-in-go/)
  [用GO構建 Restful API](https://blog.csdn.net/xingwangc2014/article/details/51623157)
  [Golang 建構簡單WEB 框架](https://zhuanlan.zhihu.com/p/27604688)