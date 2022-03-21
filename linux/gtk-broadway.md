Title: 在浏览器中显示gtk+应用
Date: 2017-12-29 18:14:49
Category: linux
Tags: linux, gtk+, gnome
Slug: gtk-broadway

### 在浏览器中显示gtk+应用
```bash
GDK_BACKEND=broadway BROADWAY_DISPLAY=:5 gtk3-demo
```
BROADWAY_DISPLAY是可选的, 默认是0

port = 8080 + display

所以在浏览器中的访问地址是 `http://127.0.0.1:8085`

#### 参考连接
* [https://developer.gnome.org/gtk3/stable/gtk-broadway.html](https://developer.gnome.org/gtk3/stable/gtk-broadway.html)
* [https://developer.gnome.org/gtk3/unstable/gtk-building.html](https://developer.gnome.org/gtk3/unstable/gtk-building.html)
* [https://blogs.gnome.org/alexl/2011/04/18/broadway-update-3](https://blogs.gnome.org/alexl/2011/04/18/broadway-update-3/)
* [https://github.com/symbiose/symbiose/wiki/Broadway](https://github.com/symbiose/symbiose/wiki/Broadway)
* [Tutorial : using GTK+3 "Broadway" on Windows](http://www.tarnyko.net/en/?q=node/8)
