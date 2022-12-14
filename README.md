# Final Exam 2420

## Question 1 
### How could you update most of the software on your Ubuntu OS?

Youre able to update most software using the command 
<br>
```sudo apt update``` <br>


## Question 2
### Fix the code in vim 

I used o and i to start edits on the vim file. <br>
I used x to make deletions within the file. <br>
I used wq to write quit the file. <br> 

<img width="744" alt="Screenshot 2022-12-08 at 12 25 45 PM" src="https://user-images.githubusercontent.com/88999663/206560943-2652570b-8575-4b9f-9a5f-86c5b546a4b6.png">

## Question 3

Make a new user <br> 

<img width="497" alt="Screenshot 2022-12-08 at 12 37 05 PM" src="https://user-images.githubusercontent.com/88999663/206562535-c5968702-55bd-4e6e-9b47-3d8938221454.png">


```
man journalctl
```
```
/boot
```

<img width="854" alt="Screenshot 2022-12-08 at 1 39 31 PM" src="https://user-images.githubusercontent.com/88999663/206573005-114d4a40-b2a6-46b7-9a10-75ece681507c.png">


```
/priority
```

<img width="1388" alt="Screenshot 2022-12-08 at 1 42 30 PM" src="https://user-images.githubusercontent.com/88999663/206573449-44f26833-7a21-4751-ba35-52ceb9c9a43c.png">

```
/output
```
<img width="761" alt="Screenshot 2022-12-08 at 1 44 08 PM" src="https://user-images.githubusercontent.com/88999663/206573863-2745d49e-8c86-4c3d-ab2b-4468f017a799.png">

```
journalctl --output=json-pretty --boot=all 
```
<img width="995" alt="Screenshot 2022-12-08 at 1 47 05 PM" src="https://user-images.githubusercontent.com/88999663/206574235-b8bc58fa-010c-4fd0-9ed4-158c4f0b2876.png">

## Question 4 

### Script 
```#!/bin/bash

users=$(grep ":[[:digit:]]\{4\}:" /etc/passwd)

part4="$part4$(echo "$users" | awk -F: '{print $1": "$3": "$7}')\n\n"
part4="$currentLogin logged in users:\n"
part4="$part4$(who | awk '{print $1}')\n"

echo -e "$part4" | tee /etc/motd
```
Script working: <br>
<img width="695" alt="Screenshot 2022-12-08 at 12 54 07 PM" src="https://user-images.githubusercontent.com/88999663/206565962-b46e75b1-ede5-40dc-aafe-da4a950cce70.png">

<br>
Script saving to /etc/motd file <br>
<img width="606" alt="Screenshot 2022-12-08 at 12 55 10 PM" src="https://user-images.githubusercontent.com/88999663/206566111-b207cc3e-4bfe-4eff-8f28-47d5e946746b.png">
<img width="1437" alt="Screenshot 2022-12-08 at 12 55 00 PM" src="https://user-images.githubusercontent.com/88999663/206566127-cd035ec1-4088-4b96-875b-fcd22b4ed9dd.png">


## Question 5

create a vim file in <br>
```/etc/systemd/system```
<img width="870" alt="Screenshot 2022-12-08 at 1 09 32 PM" src="https://user-images.githubusercontent.com/88999663/206567945-10d99c4f-1fd3-481f-a82a-16a0c9567f36.png">
<br>
### Enter the following code <br>
```[Unit]
Description=Find users

[Service]
Type=simple
ExecStart=/bin/bash /home/andrew-1/final
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
### Use the following code to start your service 

```
sudo systemctl enable script_1.service
```
Then use: <br>

```
sudo systemctl start script_1.service
```

To see the status use: <br>

```
sudo systemctl status script_1.service
```
<img width="1014" alt="Screenshot 2022-12-08 at 2 06 38 PM" src="https://user-images.githubusercontent.com/88999663/206577404-10268015-1164-459d-870f-a036f5ed40dc.png">


## Question 6
### Timer

```
[Unit]
Description=Timer for running service

[Timer]
OnBootSec=1min
OnUnitActiveSec=1d

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl enable find_users.timer
```
```
sudo systemctl start find_users.timer
```
```
sudo systemctl status find_users.timer
```
<img width="998" alt="Screenshot 2022-12-08 at 1 56 33 PM" src="https://user-images.githubusercontent.com/88999663/206575857-67c808b2-86ce-462d-86cd-9fba6a094821.png">
