# Подготовка для варианта с Git Bash и Visual Studio Code

## Git

### Установка

Скачать [тут](https://git-scm.com/downloads)

Или через пакетные менеджеры: 
```
choco install git
sudo apt install git
brew install git
```

*Для Windows: в инсталляторе оставить все опции по умолчанию*

### Настройка

Нужно ввести следующие команды в терминале (для Windows — в Git Bash, CMD или PowerShell)

```bash
# Настройка имени и почты пользователя. Эта информация будет прикрепляться к каждому коммиту
git config --global user.name "YOUR_NAME"
git config --global user.email "your@email.com"
```


## VS Code

### Установка

VS Code можно взять здесь <https://code.visualstudio.com/Download>  


### Настройка

1. (Опционально) Включи автосохранение в VS Code - больше не придется нажимать `Ctrl/Cmd + S` после каждого изменения. Ставим галочку `Auto Save` в меню  `File`

2. Настрой VS Code как редактор по умолчанию для гита(Если не было настроено раннее):

   В терминале (для Windows - в Git Bash):

   `code ~/.gitconfig`

   Откроется файл конфигурации гита в VS Code. Добавь в конец:

   ```
   [core]
   	editor = code --wait
   [merge]
   	tool = vscode
   [mergetool "vscode"]
   	cmd = code --wait $MERGED
   [diff]
   	tool = vscode
   [difftool "vscode"]
   	cmd = code --wait --diff $LOCAL $REMOTE
   ```


## GitHub

1. [Заведи аккаунт на GitHub](https://github.com/join)

2. Сгенерируй ssh-ключ (Чтобы в дальнейшем не нужно было каждый раз вводить пароль) Для этого в терминале (Git Bash на Windows) введи:

   `ssh-keygen -t rsa -b 4096`

   Оставь все опции по умолчанию (`Enter` после каждого вопроса)
   После этого в директории `~/.ssh` будет создано 2 файла: `id_rsa` и `id_rsa.pub`

3. Теперь нужно добавить содержимое `id_rsa.pub` на GitHub. Просмотреть его можно, например, открыв через VS Code (Эта команда пишется в git bash): 

   `code ~/.ssh/id_rsa.pub`

   Его нужно вставить на этой странице в поле "Key"

   <https://github.com/settings/ssh/new> 
   
   В поле "Title" можно написать что угодно, это просто название ssh-ключа.
   
   После этого нажми `Add SSH key` и ключ будет добавлен
   
