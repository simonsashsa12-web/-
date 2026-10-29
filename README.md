
git --version
git config --global user.name "Симоненко А.А."
git config --global user.email "agrofox.stalker@yandex.ru"
git clone https://github.com/username/donstu_fio.git
cd donstu_fio
echo "Это учебный репозиторий для вуза." > main.txt
echo "Здесь будут заметки по дисциплинам." > notes.txt

git add .
git commit -m "ПРИВЕТ"
