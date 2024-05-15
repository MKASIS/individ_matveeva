---
title: Язык разметки Markdown/Markdown language
subtitle: Эта глава о том, как начать работу с Git. Вначале изучим основы систем контроля версий, затем перейдём к тому, как запустить Git на вашей ОС и окончательно настроить для работы. В конце главы вы уже будете знать, что такое Git и почему им следует пользоваться, а также получите окончательно настроенную для работы систему./This chapter is about getting started with Git. Let's first learn the basics of version control systems, then move on to how to run Git on your OS and finally set it up to work. By the end of this chapter, you'll know what Git is and why you should use it, and you'll have a system that's finally set up to work.



authors:
  - admin
tags: []
categories: []
projects: []
date: '2019-02-05T00:00:00Z'
lastMod: '2019-09-05T00:00:00Z'
image:
  caption: ''
  focal_point: ''
---







    Welcome to Academic!

## О системе контроля версий



Что такое «система контроля версий» и почему это важно? Система контроля версий — это система, записывающая изменения в файл или набор файлов в течение времени и позволяющая вернуться позже к определённой версии. Для контроля версий файлов в этой книге в качестве примера будет использоваться исходный код программного обеспечения, хотя на самом деле вы можете использовать контроль версий практически для любых типов файлов./What is a "version control system" and why is it important? A version control system is a system that records changes to a file or set of files over time and allows you to revert to a specific version later. For file versioning, this book will use software source code as an example, although you can actually use versioning for just about any type of file.



Если вы графический или web-дизайнер и хотите сохранить каждую версию изображения или макета (скорее всего, захотите), система контроля версий (далее VCS) — как раз то, что нужно. Она позволяет вернуть файлы к состоянию, в котором они были до изменений, вернуть проект к исходному состоянию, увидеть изменения, увидеть, кто последний менял что-то и вызвал проблему, кто поставил задачу и когда и многое другое. Использование VCS также значит в целом, что, если вы сломали что-то или потеряли файлы, вы спокойно можете всё исправить. В дополнение ко всему вы получите всё это без каких-либо дополнительных усилий./If you're a graphic or web designer and want to save every version of an image or layout (most likely you will), a version control system (hereinafter referred to as VCS) is just what you need. It allows you to return files to the state they were before the changes, return the project to its original state, see the changes, see who last changed something and caused the problem, who set the task and when, and much more. Using VCS also generally means that if you break something or lose files, you can easily fix it. In addition to everything, you will get all this without any additional effort.



## Локальные системы контроля версий

Многие люди в качестве метода контроля версий применяют копирование файлов в отдельный каталог (возможно даже, каталог с отметкой по времени, если они достаточно сообразительны). Данный подход очень распространён из-за его простоты, однако он невероятно сильно подвержен появлению ошибок. Можно легко забыть в каком каталоге вы находитесь и случайно изменить не тот файл или скопировать не те файлы, которые вы хотели.

Для того, чтобы решить эту проблему, программисты давным-давно разработали локальные VCS с простой базой данных, которая хранит записи о всех изменениях в файлах, осуществляя тем самым контроль ревизий./ Many people use copying files into a separate directory as a version control method (perhaps even a timestamped directory, if they're smart enough). This approach is very common due to its simplicity, but it is incredibly error prone. It's easy to forget which directory you're in and accidentally change the wrong file or copy the wrong files.

To solve this problem, programmers long ago developed local VCSs with a simple database that keeps a record of all changes to files, thus providing revision control.

![png](./2.png)

Одной из популярных VCS была система RCS, которая и сегодня распространяется со многими компьютерами. RCS хранит на диске наборы патчей (различий между файлами) в специальном формате, применяя которые она может воссоздавать состояние каждого файла в заданный момент времени./One popular VCS was the RCS system, which is still distributed with many computers today. RCS stores sets of patches (differences between files) on disk in a special format, using which it can recreate the state of each file at a given point in time

## Централизованные системы контроля версий

Следующая серьёзная проблема, с которой сталкиваются люди, — это необходимость взаимодействовать с другими разработчиками. Для того, чтобы разобраться с ней, были разработаны централизованные системы контроля версий (Centralized Version Control System, далее CVCS). Такие системы, как CVS, Subversion и Perforce, используют единственный сервер, содержащий все версии файлов, и некоторое количество клиентов, которые получают файлы из этого централизованного хранилища. Применение CVCS являлось стандартом на протяжении многих лет./The next big problem people face is the need to interact with other developers. In order to deal with it, centralized version control systems (Centralized Version Control System, hereinafter CVCS) were developed. Systems such as CVS, Subversion, and Perforce use a single server that holds all versions of files, and a number of clients that retrieve files from this centralized repository. The use of CVCS has been the standard for many years.

![png](./3.png)

Такой подход имеет множество преимуществ, особенно перед локальными VCS. Например, все разработчики проекта в определённой степени знают, чем занимается каждый из них. Администраторы имеют полный контроль над тем, кто и что может делать, и гораздо проще администрировать CVCS, чем оперировать локальными базами данных на каждом клиенте./This approach has many advantages, especially over local VCS. For example, all project developers know to some extent what each of them does. Administrators have full control over who can do what, and it's much easier to administer CVCS than it is to manage local databases on each client.

Несмотря на это, данный подход тоже имеет серьёзные минусы. Самый очевидный минус — это единая точка отказа, представленная централизованным сервером. Если этот сервер выйдет из строя на час, то в течение этого времени никто не сможет использовать контроль версий для сохранения изменений, над которыми работает, а также никто не сможет обмениваться этими изменениями с другими разработчиками. Если жёсткий диск, на котором хранится центральная БД, повреждён, а своевременные бэкапы отсутствуют, вы потеряете всё — всю историю проекта, не считая единичных снимков репозитория, которые сохранились на локальных машинах разработчиков. Локальные VCS страдают от той же самой проблемы: когда вся история проекта хранится в одном месте, вы рискуете потерять всё./Despite this, this approach also has serious disadvantages. The most obvious downside is the single point of failure represented by the centralized server. If that server goes down for an hour, during that time no one will be able to use version control to save the changes they are working on, and no one will be able to share those changes with other developers. If the hard drive on which the central database is stored is damaged,
and there are no timely backups, you will lose everything - the entire history of the project, not counting the single repository snapshots that were saved on the developers' local machines. Local VCSs suffer from the same problem: when all project history is stored in one place, you risk losing everything.




## Распределённые системы контроля версий

Здесь в игру вступают распределённые системы контроля версий (Distributed Version Control System, далее DVCS). В DVCS (таких как Git, Mercurial, Bazaar или Darcs) клиенты не просто скачивают снимок всех файлов (состояние файлов на определённый момент времени) — они полностью копируют репозиторий. В этом случае, если один из серверов, через который разработчики обменивались данными, умрёт, любой клиентский репозиторий может быть скопирован на другой сервер для продолжения работы. Каждая копия репозитория является полным бэкапом всех данных.
This is where Distributed Version Control System (DVCS) comes into play. In DVCS (such as Git, Mercurial, Bazaar or Darcs), clients don't just download a snapshot of all files (the state of the files at a particular point in time)—they copy the entire repository. In this case, if one of the servers through which the developers communicated dies, any client repository can be copied to another server to continue working. Each copy of the repository is a complete backup of all data.



![png](./4.png)

Более того, многие DVCS могут одновременно взаимодействовать с несколькими удалёнными репозиториями, благодаря этому вы можете работать с различными группами людей, применяя различные подходы единовременно в рамках одного проекта. Это позволяет применять сразу несколько подходов в разработке, например, иерархические модели, что совершенно невозможно в централизованных системах.
Moreover, many DVCSs can interact with multiple remote repositories at the same time, so you can work with different groups of people using different approaches at the same time within the same project. This allows you to apply several development approaches at once, for example, hierarchical models, which is completely impossible in centralized systems.




