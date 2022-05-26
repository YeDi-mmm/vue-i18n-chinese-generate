# vue-i18n 自动提取中文工具

###  通过该工具，可以将vue-i18n的vue项目（vue/js）自动提取中文（js文件会自动查找，绑定$t方法）
### 安装
```
npm install -g vue-i18n-chinese-generate
yarn global add vue-i18n-chinese-generate
```
### 运行

项目根目录命令行执行 i18n
```
# 生成国际化文件
i18n generate ./src （可指定执行的目录，例如：i18n generate ./src/views/HomeView.vue）
# 然后就会在根目录生成一个 zh_langs.js 的配置文件，之后对项目引入vue-i18n并采用该配置文件即可
```

执行生成命令时，可以通过参数控制key和index，如下
```
i18n generate ./src --p src/lang  指定设置生成文件的路径
-k, --key <key>            自定义key前缀，默认为相对执行目录的文件路径
-s, --single               是否为单文件index序列，默认为全局序列，当自定义key之后，此设置无效
-p, --path <path>          设置生成文件的路径，默认为运行目录（请设置已经存在的目录！！！）
-f, --filename <filename>  设置生成文件名，默认为zh_langs
```

```javascript
import VueI18n from 'vue-i18n';

Vue.use(VueI18n);
const i18n = new VueI18n({
	locale: 'en', // 默认语言
	messages: {
		'en': require('./en_langs'), // 引入当前英文语言包
		'zh': require('./zh_langs') // 引入当前中文语言包
	}
});

new Vue({
	router,
	i18n,
	render: h => h(App)
}).$mount('#app');
```

### 参考
[vue-i18n 文档](https://kazupon.github.io/vue-i18n/)
