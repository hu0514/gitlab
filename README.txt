下载gitlab最新镜像
docker pull gitlab/gitlab-ce:latest

使用docker run 生成容器 
docker run -d --hostname=test.huliyuan.com --name gitlab --restart always -p 80:80 -p 443:443 -p 8022:22 -v /data/gitlab/config:/etc/gitlab -v /data/gitlab/logs:/var/log/gitlab -v /data/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce:latest

使用docker-compose 生成容器
下载docker-compose.yml到本地 运行命令 docker-compose up -d (确保和docker-compose.yml在同一目录)

由于本容器将22端口映射到8022上 需修改配置文件然后重启才能使用git地址克隆 否则只能使用http地址克隆
修改配置文件/data/gitlab/config/gitlab.rb 第370行
修改前
#  gitlab_rails['gitlab_shell_ssh_port'] = 22
修改后
gitlab_rails['gitlab_shell_ssh_port'] = 8022
重启dockers容器 
docker restart gitlab
