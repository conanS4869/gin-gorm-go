## swaggo 使用
### 安装
- 下载依赖
```shell
go get -u github.com/swaggo/swag/cmd/swag
```
- 安装命令行
` 进入github.com/swaggo/swag/cmd/swag`
- 执行 
```shell
go intall
```
- 安装files和gin-swagger
```shell
go get -u github.com/swaggo/gin-swagger
go get -u github.com/swaggo/files
```
### 使用
- 在方法上添加注释
```go
// GetRankList
// @Tags 公共方法
// @Summary 用户排行榜
// @Param page query int false "page"
// @Param size query int false "size"
// @Success 200 {string} json "{"code":"200","data":""}"
// @Router /rank-list [get]
```
- 在路由中配置
```go
import (
	_ "gin-gorm-go/docs"
"github.com/gin-gonic/gin"
swaggerfiles "github.com/swaggo/files"
ginSwagger "github.com/swaggo/gin-swagger"
)
func Router() *gin.Engine {
r := gin.Default()
// Swagger 配置
r.GET("/swagger/*any", ginSwagger.WrapHandler(swaggerfiles.Handler))
return r
}
```
- 执行 `生成docs`
```shell
swag init
```
### 启动程序，访问url: http://localhost:8080/swagger/index.html



