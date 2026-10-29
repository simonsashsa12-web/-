
git --version
git config --global user.name "Симоненко А.А."
git config --global user.email "agrofox.stalker@yandex.ru"
git clone https://github.com/username/donstu_fio.git
cd donstu_fio
echo "Это учебный репозиторий для вуза." > main.txt
echo "Здесь будут заметки по дисциплинам." > notes.txt

git add .
git commit -m "ПРИВЕТ"
git pull origin main
echo "Добавлена новая строка." >> main.txt
git status
git add main.txt
git commit -m "обновление main.txt"

echo "Ещё одна заметка." >> notes.txt
git add notes.txt
git commit -m "добавлены заметки"
git log --oneline
# Скопируй хеш коммита ПЕРЕД «обновление main.txt» (предпоследний)
git checkout <хеш_коммита>

# Чтобы вернуться к последнему состоянию:
git checkout main
# или git checkout master, если ветка так называется
git checkout -b feature-branch

# Добавить новый файл
touch new_feature.txt
echo "Это новый функционал." > new_feature.txt

# Изменить существующий файл (добавить, удалить, изменить строки)
# Пример: добавляем строку
echo "Строка из feature-ветки." >> main.txt
# Если нужно удалить строку — отредактируй main.txt вручную в редакторе

git add .
git commit -m "изменения в feature-ветке: новый файл и правка main.txt"
git checkout main
# или git checkout master

# Добавить новый файл
touch main_only.txt
echo "Файл только в main." > main_only.txt

# Изменить main.txt иначе, чем в feature-ветке (это важно для конфликта)
echo "Строка только из main." >> main.txt
# При необходимости удали/измени другие строки вручную в редакторе

git add .
git commit -m "изменения в main: новый файл и правка main.txt"
git merge feature-branch
git log --graph --oneline --all
git checkout feature-branch
git reset --hard HEAD~1
