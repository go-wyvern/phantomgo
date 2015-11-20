# phantomgo
usage
```
package main

import (
	"fmt"
	"github.com/go-wyvern/phantomgo"
	"io/ioutil"
)

func main() {
	p := phantomgo.NewPhantom()
	res, _ := p.Start([]string{"open", "http://weibo.com"})
	output, _ := ioutil.ReadAll(res)
	fmt.Println(string(output))
}
```
可动态执行phantomjs提供的JavaScript接口
```
package main

import (
	"fmt"
	"github.com/go-wyvern/phantomgo"
	"io/ioutil"
)

func main() {
	p := phantomgo.NewPhantom()
	js := `
		var system = require('system');
		console.log(system.args[0],system.args[1],system.args[2]);
		phantom.exit();
		`
	res, _ := p.Exec(js,"11","22")
	output, _ := ioutil.ReadAll(res)
	fmt.Println(string(output))
	
}
```
