Подключение и настройка VDS сервера 

1)Создание пары SSH ключей 
ssh-keygen -t ed25519

2)Подключение к серверу 
ssh user@ip_address
Пример
ssh root@80.249.149.94

3)Создать нового пользователя
sudo useradd -m -s /bin/bash username
sudo passwd username

4) Добавить в группу sudo (дать права администратора)
sudo usermod -aG sudo username
Переключиться на другого пользователя
su - username
sudo -i                        Стать root (если есть права)

5) Обновим систему (привыкать делать это регулярно)
sudo apt update && sudo apt upgrade -y

6)Установим простой файрвол
sudo apt install ufw -y
Разрешим SSH (обязательно ДО включения!)
sudo ufw allow 22/tcp
 Включим файрвол
sudo ufw enable

7)Отключить вход по паролю 
sudo nano /etc/ssh/sshd_config
PasswordAuthentication no
sudo systemctl restart sshd
