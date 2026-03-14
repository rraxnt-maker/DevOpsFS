---
tags:
  - карточки/dewops
---
[[DevOps_practice.pdf]]



*В начале представиться перед gitом*
?
git config user.name "Твое Имя"
git config user.email "твой-email@пример.com"
<!--SR:!2026-03-16,4,270-->

*Клонировать по SSH себе на комп Github репозиторий*
?
git clone https://github.com/ВАШ_АККАУНТ/ИМЯ_РЕПОЗИТОРИЯ.git
<!--SR:!2026-03-16,4,270-->

*добавить все файлы для коммита*
?
git add . можно git add filename
git commit -m "закоммитить все что изменил"
<!--SR:!2026-03-16,4,270-->

*Запушить изменения онлайн*
?
git push
git push --force принудительно если конфликты
<!--SR:!2026-03-18,4,279-->

*Подкачать все изменения в git репозитории*
?
git pull
<!--SR:!2026-03-16,4,270-->

*Запушить изменения онлайн*
?
git push
git push --force принудительно если конфликты

*Добавление изменений в последний коммит без создания нового* 
git commit --amend


git pull --rebase
git rebase --continue
git rebase --skip 

рабочая директория -  для написания кода и тд
индекс (stage) - подготовленные файлы для коммита
репозиторий - список всех версий и посмотреть их изменения и тд.
![[diagramm1.png]]
untracked -(git add)--> staged -(git commit)->unmodified -> moified
![[diagramm2.png]]

`git checkout name` - переключимся на коммит 
`git checkout -b branch name` - 
`git stash`- временный комит помогает не пушить не готовую работу
`git switch branch_name`- переключиться на другую ветку  
