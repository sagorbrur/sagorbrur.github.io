---
title: "Gentle intro about Screen in ubuntu"
date: 2022-10-21
categories:
  - ubuntu
  - linux
classes: wide
excerpt: This blog describe about the basic use cases of screen
---

Do you feel that your present execution will run in background and you are able to terminate the terminal?

Then __screen__ you all need. Here I will note some basic use cases of __screen__ command for ubuntu. In case I forgot and need all the basics in one place. :D

## Installation
```
$ sudo apt update
$ sudo apt install screen
```

## screen management
- Creating a screen session
    ```
    screen -S myscreen
    ```

- Detaching a screen session
    ```
    clt + a d
    ```
- Display all your detached, attached screen
    ```
    screen -ls
    ```
- Opening any detached screen
    ```
    screen -r myscreen
    ```
- Killing any screen
    ```
    screen -ls
    # copy the screen id you want to kill
    screen -X -S screen_id quit
    screen -X -S 25421 quit
    ```

## References
- [https://linuxize.com/post/how-to-use-linux-screen/](https://linuxize.com/post/how-to-use-linux-screen/)
- [https://stackoverflow.com/questions/1509677/kill-detached-screen-session](https://stackoverflow.com/questions/1509677/kill-detached-screen-session)


