```
启动web项目时出错以及解决方案如下:
1、首先删除项目目录下的node_modules文件夹及以下的文件
2、npm cacke clean --force  如果之前运行过命令，再运行之后出错，需要清除缓存
	上述方法适用于Unexpected end of JSON input while parsing near '..." 或者 出现 No Such file or directory..
3、npm install --registry=https://registry.npm.tabao.org    用淘宝镜像安装
	（1）出错：  ERROR: CAN'T FIND PYTHON EXECUTABLE "PYTHON", YOU CAN SET THE PYTHON ENV VARIABLE.
		解决方案：缺少python环境 npm install --global --production windows-build-tools
	（2）出错：	npm ERR! code ELIFECYCLE
			npm ERR! errno 1
			npm ERR! node-sass@4.11.0 postinstall: `node scripts/build.js`
			npm ERR! Exit status 1
			npm ERR!
			npm ERR! Failed at the node-sass@4.11.0 postinstall script.
			npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
		解决方案：npm install node-sass@4.11.0 --ignore-scripts
	（3）出错：ModuleBuildError: Module build failed: Error: `sass-loader` requires `node-sass` >=4. 
		解决方案：npm install node-sass@latest 或者 npm i node-sass -D
	
4、npm run dev  在web项目目录下启动web项目
```