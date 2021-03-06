# 将Gitbook发布到Github Pages
> 以Mac为例  

### 1. 安装Node.js


<pre><a href="https://nodejs.org/en/download/">Node.js下载地址</a></pre>
### 2. 安装Gitbook  


	npm install gitbook-cli -g
### 3. 在Github创建一个仓库，比如：web-cookbook
 * 克隆到本地：git clone git@github.com:USERNAME/web-cookbook.git

### 4. 初始化gitbook
 * gitbook init  

### 5. 创建分支
 > master分支保存.md的源码，gh-pages分支保存编译生成的html文件    

 * 创建gh-pages分支（分支名称不能变）：git checkout -b gh-pages
 * 清空分支下的文件：git rm *
 * 将分支push到仓库：git push -u origin gh-pages
 * 切换到主分支：git checkout master
 * 克隆分支到一个新文件（book-branch）：git clone -b gh-pages git@github.com:USERNAME/web-cookbook.git book-branch, 将book-branch加入到.gitignore文件中，即可忽略book-branch的修改  

### 6. 编译
 * 构建书籍：gitbook build
 * 本地浏览：gitbook serve
 > README.md和SUMMARY.md是Gitbook项目必备的两个文件，也就是一本最简单的gitbook也必须含有这两个文件，它们在一本Gitbook中具有不同的用处  
 > README.md这个文件相当于一本Gitbook的简介  
 > SUMMARY.md这个文件是一本书的目录结构  

### 7. 发布到Github Pages
 * 将_book下的内容拷贝到分支中，即book-branch文件夹中：cp -r ./_book/* book-branch/
 * 进入book-branch目录提交修改：
  * git add .
  * git commit -m 'publish book'
  * git push origin gh-pages
 * 访问USERNAME.github.io/web-cookbook查看  

### 8. gulp发布Gitbook到Github Pages
```javascript
var gulp = require("gulp"),  
	deploy = require("gulp-gh-pages");

gulp.task('publish', function () {  
  return gulp.src("_book/\*\*/\*.\*")
    .pipe(deploy({
      remoteUrl: "git@github.com:USERNAME/web-cookbook.git"
    }))
    .on("error", function(err){
      console.log(err)
    })
});
```

### 9. Gitbook的book.json文件
gitbook在编译书籍的时候会读取书籍源码顶层目录中的book.js或者book.json，这里以book.json为例，参考[gitbook文档](https://github.com/GitbookIO/gitbook)。
```json
{
    "description": null,
    "extension": null,
    "generator": "site",
    "isbn": null,
    "links": {
        "sharing": {
            "all": null,
            "facebook": null,
            "google": null,
            "twitter": null,
            "weibo": null
        },
        "sidebar": {
            "Style's GitBook":"http://stylever.github.io/web-cookbook"
        }
    },
    "output": null,
    "pdf": {
        "fontSize": 12,
        "footerTemplate": null,
        "headerTemplate": null,
        "margin": {
            "bottom": 36,
            "left": 62,
            "right": 62,
            "top": 36
        },
        "pageNumbers": false,
        "paperSize": "a4"
    },
    "plugins": [],
    "title": null,
    "variables": {}
}
```
### 10. Disqus评论插件
[Disqus](https://disqus.com/)是一款网站集成评论系统的工具，gitbook可以集成。
 * 在disqus注册一个账号
 * 创建一个website
 * 安装disqus 插件
 ```javascript
    $ npm install gitbook-plugin-disqus
 ```
 * 修改 book.json 配置文件
 ```json
 {
    "plugins": ["disqus"],
    "pluginsConfig": {
        "disqus": {
            "shortName": "introducetogitbook" (在disqus上创建的website的Shortname)
        }
    }  
  }
 ```