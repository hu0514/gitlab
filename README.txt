����gitlab���¾���
docker pull gitlab/gitlab-ce:latest

ʹ��docker run �������� 
docker run -d --hostname=test.huliyuan.com --name gitlab --restart always -p 80:80 -p 443:443 -p 8022:22 -v /data/gitlab/config:/etc/gitlab -v /data/gitlab/logs:/var/log/gitlab -v /data/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce:latest

ʹ��docker-compose ��������
����docker-compose.yml������ �������� docker-compose up -d (ȷ����docker-compose.yml��ͬһĿ¼)

���ڱ�������22�˿�ӳ�䵽8022�� ���޸������ļ�Ȼ����������ʹ��git��ַ��¡ ����ֻ��ʹ��http��ַ��¡
�޸������ļ�/data/gitlab/config/gitlab.rb ��370��
�޸�ǰ
#  gitlab_rails['gitlab_shell_ssh_port'] = 22
�޸ĺ�
gitlab_rails['gitlab_shell_ssh_port'] = 8022
����dockers���� 
docker restart gitlab
