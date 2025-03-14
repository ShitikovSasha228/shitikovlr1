 <h1> Шитиков Александр Дмитриевич </h1>
 <h2> К-ИСП-39-1 </h2> 
 <h3>Лабороторная работа 1</h3> 
     
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

Командой <code>sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo</code>

![image](https://github.com/user-attachments/assets/6c347c14-8ee4-4a21-9828-825f13f3fe46)
