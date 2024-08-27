1)	Создаем Файл с домашними животными с помощью команды cat 
cat> “House Animal” 

* Dog

* Cat

* Hamster

Затем ctrl+d

2)	Cоздаем подобным образом файл с Вьючными животными
cat> “Pack Animal”
 
* Horse 

* Camel

* Donkey

Затем ctrl+d

![1 cat](https://github.com/user-attachments/assets/bae9524a-b1fc-4e25-a1e0-161af6770dd9)

3)	Объединяем 2 файла в один с помощью команды Cat 
*      cat “House Animal” “Pack Animal” > “Human Friends” 

4)	Проверим файл -> cat “Human Friends” => В файле находятся все вышенаписанные животные в двух прошлых файлах:
* Dog

* Cat

* Hamster

* Horse

* Camel

* Donkey

6)	Переименуем файл с помощью команды mv
*      mv “Human Friends” “Animal Friends” 

**Для создания директории и перемещения файла в нее в терминале ОС Linux можно использовать команды:**

1)	Создание директории с помощью команды mkdir 
*      mkdir first_directory

2)	Перемещаем файл в директорию: 
*      mv “Animal Friends” first_directory/

![image](https://github.com/user-attachments/assets/ca689eb3-7239-42a5-8456-876379bd4b57)

