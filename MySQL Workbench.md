Создание БД в программе MySQL Workbench 

Cоздаем БД и называем ее Human Friends 

Создаем таблицу с домашними животными под названием Pets 

1) Colums Name:
•	Id

•	Name

•	Type

•	BirthDate

•	Commands


![image](https://github.com/user-attachments/assets/8a98ec3c-fe14-4fa4-84a5-1a3749178ed9)

2) Во вкладке Inserts заполняем таблицу данными

   ![image](https://github.com/user-attachments/assets/eba106b8-1f8f-4b9e-b071-16a7f5efed57)

По схожей схеме создаем таблицу PackAnimal (можно скопировать прошлую таблицу) 


![image](https://github.com/user-attachments/assets/9b2bbadb-9246-4d93-a3a7-5f847c8eb389)


**"БАЗА ДАННЫХ"**

подключенном MySQL репозитории создать базу данных “Human Friends”

   CREATE DATABASE IF NOT EXISTS HumanFriends;
   
   USE HumanFriends;


Создать таблицы с иерархией из диаграммы в БД

CREATE TABLE Commands


        (
          id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
          name varchar(30),
          description varchar(255)
        );


      CREATE TABLE AnimalGroup
      (
          id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
          name varchar(30)   
      );

CREATE TABLE IntelligentAnimals
(
    id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    name varchar(30),
    group_id INT,
    FOREIGN KEY (group_id) REFERENCES AnimalGroup (id)
    ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE CampAnimal
(
    id INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    name varchar(30),
    birthDate DATE,
    iq_id INT,
    FOREIGN KEY (iq_id) REFERENCES IntelligentAnimals (id)
    ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE TABLE AnimalCommands
(
    animal_id INT NOT NULL,
    command_id INT NOT NULL,

  PRIMARY KEY (animal_id, command_id),
  FOREIGN KEY (animal_id) REFERENCES CampAnimal (id)
  ON DELETE CASCADE ON UPDATE CASCADE,
  FOREIGN KEY (command_id) REFERENCES Commands (id)
  ON DELETE CASCADE  ON UPDATE CASCADE
);
Заполнить низкоуровневые таблицы именами (животных), командами которые они выполняют и датами рождения

 USE HumanFriends;

INSERT INTO commands(name)
VALUES
 ('Voice!'),
 ('Jump'),
 ('Run!'),
 ('Bow down!'),
 ('Kash!');

INSERT INTO AnimalGroup (name)
VALUES
 ('Pets'),
 ('Pack Animals');

INSERT INTO IntelligentAnimals (name, group_id)
VALUES
('Cat', 1),
('Dog', 1),
('Hamster', 1),
('Horse', 2),
('Camel', 2),
('Donkey',2);

INSERT INTO CampAnimal (name, birthDate, iq_id)
VALUES
 ('Gigachad', '2020-01-01', 1),
 ('Sedric', '2019-11-01', 1),
 ('Sam', '2020-08-24', 3),
 ('Elis', '2021-05-20', 2),
 ('Wendigo', '2021-01-24', 5),
 ('Watch', '2019-12-20', 6),
 ('Pokemon', '2020-07-12', 4);

INSERT INTO AnimalCommands (animal_id, command_id)
VALUES
 (1, 3), (2, 3), (2, 4), (3, 4),
 (4, 5), (5, 1), (5, 4), (6, 2),
 (7, 1);
Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.

   USE HumanFriends;
   DELETE FROM CampAnimal WHERE iq_id = 1;

   CREATE TABLE HorseAndDonkey AS
   SELECT * from CampAnimal WHERE iq_id = 2
   UNION
   SELECT * from CampAnimal WHERE iq_id = 3;


Создать новую таблицу “молодые животные” в которую попадут все животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью до месяца подсчитать возраст животных в новой таблице


   CREATE TABLE YouthfulAnimals AS
      SELECT id, name, birthDate, 
      datediff(curdate(),birthDate) DIV 31 as age, iq_id 
      from CampAnimal 
      WHERE date_add(birthDate, INTERVAL 1 YEAR) < curdate() 
            AND date_add(birthDate, INTERVAL 3 YEAR) > curdate();


Объединить все таблицы в одну, при этом сохраняя поля, указывающие на прошлую принадлежность к старым таблицам.

   SELECT id, name, birthDate, iq_id FROM HorseDonkey
   UNION
   SELECT id, name, birthDate, iq_id FROM YouthfulAnimals;

