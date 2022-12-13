1、在github上创建一个项目目录；
2、直接从github上clone到本地  git clone https://github.com/LoveChunHua/SpringBootTest.git;
3、再将需要提交的代码复制到clone文件夹种
4、git add .
   git commit -m "first commit"
   git push -u origin master(便于下次提交直接git push)
   
…or create a new repository on the command line
echo "# rabbitmq" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/LoveChunHua/rabbitmq.git
git push -u origin master


…or push an existing repository from the command line
git remote add origin https://github.com/LoveChunHua/rabbitmq.git
git branch -M master
git push -u origin master