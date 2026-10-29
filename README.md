bash
# === ПОДГОТОВКА (выполнить 1 раз, если ещё не сделано) ===
git --version
git config --global user.name "Твоё Имя"
git config --global user.email "email@example.com"


# === ПУНКТ 3: локальная копия удалённого репозитория ===
# Замени ссылку на свою (из кнопки Code на GitHub)
git clone https://github.com/username/donstu_fio.git
cd donstu_fio


# === ПУНКТ 4: добавить файлы и первый коммит ===
echo "Это учебный репозиторий для вуза." > main.txt
echo "Здесь будут заметки по дисциплинам." > notes.txt

git add .
git commit -m "мой первый коммит"


# === ПУНКТ 5: файл на удалённом репозитории и git pull ===
# ⚠️ ВАЖНО: этот шаг делается вручную на сайте GitHub:
# 1. Зайди в репозиторий на GitHub.
# 2. Нажми Add file → Create new file.
# 3. Создай файл online_note.txt, напиши: Этот файл создан на сайте GitHub.
# 4. Нажми Commit changes.
# Только после этого выполняй команду ниже:
git pull origin main
# Если ветка называется master, используй: git pull origin master


# === ПУНКТЫ 6–7: изменения, статус, новые коммиты ===
echo "Добавлена новая строка." >> main.txt
git status
git add main.txt
git commit -m "обновление main.txt"

echo "Ещё одна заметка." >> notes.txt
git add notes.txt
git commit -m "добавлены заметки"


# === ПУНКТ 8: откат к предыдущему коммиту ===
git log --oneline
# ⚠️ ВСТАВЬ СЮДА хеш коммита ПЕРЕД «обновление main.txt» (предпоследний) вместо <хеш_коммита>
git checkout <хеш_коммита>
# Чтобы вернуться к последнему состоянию:
git checkout main
# или git checkout master, если ветка так называется


# === ПУНКТ 9: новая ветка, изменения, коммит ===
git checkout -b feature-branch

touch new_feature.txt
echo "Это новый функционал." > new_feature.txt
echo "Строка из feature-ветки." >> main.txt
# При необходимости отредактируй main.txt вручную (удалить/изменить строки)

git add .
git commit -m "изменения в feature-ветке: новый файл и правка main.txt"


# === ПУНКТ 10: переключение на main, изменения, коммит ===
git checkout main
# или git checkout master

touch main_only.txt
echo "Файл только в main." > main_only.txt
echo "Строка только из main." >> main.txt
# При необходимости отредактируй main.txt вручную иначе, чем в feature-ветке (для конфликта)

git add .
git commit -m "изменения в main: новый файл и правка main.txt"


# === ПУНКТ 11: слияние веток и разрешение конфликта ===
git merge feature-branch
# ⚠️ Если возник конфликт в main.txt:
# Открой main.txt и вручную удали маркеры конфликта:
# <<<<<<< HEAD
# Строка только из main.
# =======
# Строка из feature-ветки.
# >>>>>>> feature-branch
# Оставь нужные строки, сохрани файл.
# Затем:
git add main.txt
git commit
# Просто сохрани сообщение коммита (это коммит слияния)


# === ПУНКТ 12: дерево истории ===
git log --graph --oneline --all


# === ПУНКТ 13: откат изменений в созданной ветке ===
git checkout feature-branch
git reset --hard HEAD~1
# ⚠️ Внимание: --hard полностью отменяет последний коммит в этой ветке.


# === ПУНКТ 14: отправка на удалённый репозиторий ===
git checkout main
git push origin main
git push origin feature-branch


# === ДОПОЛНИТЕЛЬНО: README (пункт 2) ===
# Создай файл README.md и вставь туда текст (вручную в редакторе)
# Пример содержимого README.md:
# # donstu_fio
# Учебный репозиторий для хранения работ по дисциплинам.
# ## Структура
# - main.txt — основные заметки.
# - notes.txt — дополнительные заметки.
# - new_feature.txt — пример работы с ветками.
# - main_only.txt — файл только в main.
# ## Правила ведения репозитория
# - Каждый значимый этап — отдельный коммит с понятным сообщением.
# - Новые функции — в отдельных ветках.
# - Слияние — только после проверки и разрешения конфликтов.
#
# После создания файла:
git add README.md
git commit -m "добавлен README с описанием и правилами"
git push origin main
