MYSQL дополнительный репозиторий
1)	Сначала нужно перейти в режим суперпользователя с помощью
   *      sudo su
   
3)	Добавим новый ключ репозитория с помощью команды указанной ниже
 *     **wget -O- https://repo.mysql.com/RPM-GPG-KEY-mysql-2022 | sudo apt-key add –**

![image](https://github.com/user-attachments/assets/cb50f19c-dd58-47f7-97eb-e895faac072c)

3)	 Добавим репозиторий MySQL в систему с помощью команды:
*      echo "deb http://repo.mysql.com/apt/ubuntu/ $(lsb_release -sc) mysql-8.0" | sudo tee /etc/apt/sources.list.d/mysql.list

4)	Обновим пакеты с помощью команды -> sudo apt update

   ![image](https://github.com/user-attachments/assets/b4e56e3b-a759-4fdc-a68f-b8cb2dd774d7)

5)	Установим любой пакет из репозитория MySQL
В нашем случаем вводим
*      snap install mysql-shell

   ![image](https://github.com/user-attachments/assets/b46f41d1-a83f-455c-bc0b-23a348d9be69)


**Для установки и удаления deb-пакета с помощью dpkg выполняем следующее: 
**
1)	Скачаем deb-пакет, например, Midnight Commander (MC), с помощью команды:
*      wget http://archive.ubuntu.com/ubuntu/pool/universe/m/mc/mc_4.8.25-2ubuntu2_amd64.deb
2)	Установим пакет
   *      sudo dpkg -i mc_4.8.25-2ubuntu2_amd64.deb
3)	Удалим с помощью команды
   *      sudo dpkg -r mc
(повторяем команду чтобы проверить точно ли удалилось) 

![image](https://github.com/user-attachments/assets/a9e8bd8b-de0a-4cba-93b2-9593031f4433)

