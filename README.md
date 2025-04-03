 <h1> Шитиков Александр Дмитриевич </h1>
 <h2> К-ИСП-39-1 </h2> 
 <h3>Лабороторная работа 1</h3> 
АИС (Автоматизированной Информационной Системы)  

![image](https://github.com/user-attachments/assets/13bb49c8-541e-4fad-93ad-844ad96b42fe)

     
 <h1> Установка Linux и подготовка рабочей среды </h1> 

Был установлен дистрибутив Linux со следующими параметрами:  
4ГБ ОЗУ  
3 Ядра процессора  
20ГБ памяти виртуальный диск

<h2> is not in the sudoers file. This incident will be reported.</h2>
В процессе работы была выявленна ошибка shitikovad is not in the sudoers file. This incident will
be reported.  

![image](https://github.com/user-attachments/assets/19af23ad-4aa2-47bc-a990-b96315857257)

Для её устранения нужно:    

1) Открыть терминал и ввести туда su root  

![image](https://github.com/user-attachments/assets/6fd4db70-e0a7-4f42-8202-125b9932933b)

2) После ввода пароля вводим visudo  

![image](https://github.com/user-attachments/assets/f5438e07-c903-4367-8721-b368406840a2)


3) В появившемся окне нажимаем 3 раза Enter  

![image](https://github.com/user-attachments/assets/644cb765-2f9f-43cc-af5a-3b81f4931a43)


5) Листаем файл и находим root 

![image](https://github.com/user-attachments/assets/305da484-1310-4f5a-bcbd-903a42eecad1)


6) Нажмимаем клавишу Insert и пишем под ним своё имя пользователя как в примере (отступы делаем при помощи клавиши TAB)

![image](https://github.com/user-attachments/assets/ceb7df46-f910-4263-b746-d83909318503)
   
И всё готово


<h1>Задание</h1>

1. В начале была установлена <code>sudo yum install wget </code>  
   
![image](https://github.com/user-attachments/assets/1e9b133f-5c05-4608-884c-871d5b4f0611)

2. После чего устанавливаем пакет curl

![image](https://github.com/user-attachments/assets/7e277884-f6e8-4efd-834e-0a9dd8435f1a)

3. Командой <code>sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo</code> скачиваем файл репозитория

![image](https://github.com/user-attachments/assets/6c347c14-8ee4-4a21-9828-825f13f3fe46)

4. Устанавливаем Docker командой <code> sudo yum install docker-ce docker-ce-cli containerd.io </code>  

![image](https://github.com/user-attachments/assets/b200fafa-29be-4ac2-93bd-b3cdc38e2f57)

5. запускаем docker

  ![изображение (2)](https://github.com/user-attachments/assets/9bb61a28-d438-46c4-99c7-bf08235ee38e)


6. Командой <code> COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4) </code> получаем последнию весрию докера  

![image](https://github.com/user-attachments/assets/796a9c68-5f58-45a7-8f15-8ae6714d5ee6)

7. Командой <code> sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose </code> загружаем Docker

![image](https://github.com/user-attachments/assets/b21a17a4-92d8-4b9b-871e-10afcaaef959)

8. Делаем докер исполняемым <code> sudo chmod +x /usr/bin/docker-compose </code>

![image](https://github.com/user-attachments/assets/70d0b4eb-04a3-44b0-8228-7d128f83b61f)

Проверяем стал ли он исполняемым 

![image](https://github.com/user-attachments/assets/2844f8da-ab40-4224-9544-5ffe3c2a2a8a)

Успешно

9. Проверяем какая версия установилась при помощи команды <code> docker-compose --version </code>

![image](https://github.com/user-attachments/assets/f2e24714-b0a6-478d-b346-d41a6ef7d588)

11. Клонируем удалённый репозиторий по ссылке, командой <code> git clone https://github.com/skl256/grafana_stack_for_docker.git </code>

![image](https://github.com/user-attachments/assets/4c579fc1-7ec5-4417-96ee-aa2b0d10d441)


12. Переходим в папку **grafana_stack_for_docker** и прописываем команду <code> sudo mkdir -p /mnt/common_volume/swarm/grafana/config </code>

![image](https://github.com/user-attachments/assets/b41a5d6e-be82-49a2-9664-f6a35db9ab85)

13. Команда <code> sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data} создает несколько директорий (папок) внутри указанного пути.
 </code> создаёт структуру каталогов для Grafana 

 ![изображение (3)](https://github.com/user-attachments/assets/6993c152-92e7-4551-b13c-9989c6d1ebc0)

 14. Права на файлы будут не только у root но и обычного потзователя <code> sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana} <code> 

![image](https://github.com/user-attachments/assets/fce7dba6-5102-4b75-bfcd-d8105b45679d)

15. <code> touch /mnt/common_volume/grafana/grafana-config/grafana.ini  </code> если файлgrapani есть то он слегка обновиться, если нет то он создастся по новой

![изображение (4)](https://github.com/user-attachments/assets/1f89e7f4-717f-4ef4-a247-9e5e0c079c71)

16. Копируес все файлы из grafana_stack_for_docker попути  <code> cp config/* /mnt/common_volume/swarm/grafana/config/  </code>

![изображение (5)](https://github.com/user-attachments/assets/4715bebc-3127-4232-a8b0-c7dc87f41318)

17. Переменовываем файл grafana.yaml на docker-compose.yaml <code> mv grafana.yaml docker-compose.yaml </code>

![image](https://github.com/user-attachments/assets/43baf602-faf5-4b81-a339-369450ce79d2)

18. Запускаем докер <code> sudo docker compose up -d </code>

![image](https://github.com/user-attachments/assets/3d642c34-8403-42d2-a1b9-73a6f9f8badc)

19. Открываем файл docker-compose.yaml и редактируем его командой <code> sudo vi docker-compose.yaml </code>

![image](https://github.com/user-attachments/assets/2055ef14-7b00-458f-abfe-110361a9c38c)

20. <code> sudo docker compose up -d </code> запускает в фонойвом режиме
    
![image](https://github.com/user-attachments/assets/f4961eeb-3a32-4016-a005-6e2c9f8e4c92)

22. <code> sudo docker compose stop </code> останавливает без удаления контейнеров
    
![image](https://github.com/user-attachments/assets/b113db53-861f-4137-9fbf-1a32bc78fc36)

    
23. <code> sudo docker compose down </code> для остановки удаляет контейнеры
![image](https://github.com/user-attachments/assets/94f722a1-5b6e-4598-94ec-ddf8d080ac0f)

24. <code> sudo docker compose ps </code> отображает текущее состояние контейнеров

![image](https://github.com/user-attachments/assets/c9b26f9b-e261-4f75-ac49-8a8ab0bbf6c4)

25. Клонируем свой репозиторий из GitHab

![image](https://github.com/user-attachments/assets/75938025-b8ec-4ebf-98fc-2c1e50384357)

26. Копируем файл промитеус в /gafana/config/ <code> sudo cp prometheus.yaml /mnt/common_volume/swarm/grafana/config </code>

![image](https://github.com/user-attachments/assets/43e234a3-99a9-4f24-98be-30bd10ac302e)

<h1> Grapha </h1>

Открываем страницу в браузере и вписываем туда 
**localhost:3000**    
Логин: admin  
Пароль: admin  
![image](https://github.com/user-attachments/assets/7b920513-0466-4aef-964f-91f36a066d55)

Полсле регистрации выбираем DASHBOARDS
![image](https://github.com/user-attachments/assets/ed3a6600-83ca-491d-8fa8-fd1b85c4325d)

Нажимаем 
![image](https://github.com/user-attachments/assets/dfc87129-f4ba-46e1-a304-4169b3e29dac)

В Dadta sourse выбираем Prometheus 
![image](https://github.com/user-attachments/assets/134a6513-4ffc-42b7-a8bc-f67b699cb342)

В этом окне вводим: http://prometheus:9090. И где аутентификация вводим: admin, admin

![image](https://github.com/user-attachments/assets/7af4376c-04a0-41fd-afa2-c980305a2b93)

Затем опять заходим в DASHBOARDS и выбираем Import DashBoard. В строку Load пишем 1860 и нажимаем Load

![image](https://github.com/user-attachments/assets/c6780f80-c3a3-4b19-b0a0-dd7dede88967)

В этом окне выбираем в самом конце выбираем Prometheus 

![image](https://github.com/user-attachments/assets/10ef2b8d-c2f8-4dd0-ad1e-2c0cba2cdfd5)

И наслаждаемся проделанной работой 

![image](https://github.com/user-attachments/assets/2146e185-4c9f-4d30-87ce-4c5f8d92728c)


<h1> Если не выводит информацию на DashBoard </h1>

1) Проверьте файлы docker-compose.yaml и prometheus.yaml, правильно ли они лежат и их содержимое. 
2) На сайте Grapha удалите все DashBoard и создайте по новой.  
   
Примечание: Если вы начнете работать с файлами docker-compose.yaml или prometheus.yaml то выключите докер, или просто перезагрузите VM. 











