# z99-django

1. Fill out inventory file with target host(s) in group [app_servers] and user credentials/sshkeys, etc..
```
[app_servers]
0.255.255.255 ansible_connection=ssh ansible_ssh_user=username ansible_ssh_pass=password
```
2. Execution of a playbook
```
ansible-playbook -i inventory playbook.yml --ask-become-pass
```
# Verification
Start server manually from /opt/myapp #Should probably make a systemd-unit in production env
```
python3 manage.py runserver 127.0.0.1:8000
```
Http healthceck by server ip gives
curl http://*EXTERNAL_IP*/healthcheck/
```
{"nginx": "running", "django": "running", "postgresql": "running"}
```