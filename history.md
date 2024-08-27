Чтобы посмотреть историю команд можно ввести команду history 

В Режиме SU 
  
1  wget -O- https://repo.mysql.com/RPM-GPG-KEY-mysql-2022 | sudo apt-key add -
    
2  echo "deb http://repo.mysql.com/apt/ubuntu/ $(lsb_release -sc) mysql-8.0" | sudo tee /etc/apt/sources.list.d/mysql.list

3  sudo apt update 

4  sudo apt install mysql-shell 

5  snap install mysql-shell 
    
6  wget http://archive.ubuntu.com/ubuntu/pool/universe/m/mc/mc_4.8.25-2ubuntu2_amd64.deb
    
7  sudo dpkg -i mc_4.8.25-2ubuntu2_amd64.deb
    
8  sudo apt --fix-broken install
    
9  wget http://archive.ubuntu.com/ubuntu/pool/universe/m/mc/mc_4.8.25-2ubuntu2_amd64.deb
    
10  sudo dpkg -i mc_4.8.25-2ubuntu2_amd64.deb
    
11  sudo dpkg -r mc~
   
12  sudo dpkg -r mc
   
13  history

![image](https://github.com/user-attachments/assets/0447dfc7-c13d-4fe2-8969-44d2beaa15ca)

В режиме обычного пользователя 

310  cat>"House Animal"

311  cat>"Pack Animal"

312  cat "House Animal" "Pack Animal" > "Human Friends"

313  cat "Human Friends"

314  mv "Human Friends" "Animal Friends"
 
315  mkdir first_directory
  
316  sudo su

![image](https://github.com/user-attachments/assets/6e2ddd9b-e39c-4f94-808a-9f1f6ab022aa)
