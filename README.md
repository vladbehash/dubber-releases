# dubber — для тестеров / for testers

[Русский](#русский) · [English](#english)

## Русский

dubber переводит и озвучивает YouTube-видео и стримы прямо во время просмотра. Это расширение Chrome и
«бекенд» — программа, которая слушает, переводит и озвучивает. Бекенд работает **локально** на вашем компьютере
(бесплатно, нужна видеокарта NVIDIA; ничего никуда не отправляется) или **на нашем сервере** (подойдёт любой
компьютер, нужен аккаунт).

### Что нужно

- Chrome или Edge.
- **Локально:** Windows 10/11, видеокарта NVIDIA от 6 ГБ памяти (8+ лучше; 12+ даёт лучший перевод), ~15 ГБ на
  диске и хороший интернет для первой установки (модели ~10 ГБ). Права администратора не нужны. Linux и macOS
  пока не поддерживаются (они в планах) — там работает только сервер.
- **Сервер:** любой компьютер и аккаунт на mydubber.com (вход по коду из письма или через Google). Бесплатно —
  60 минут в месяц на записях; Pro — без ограничения минут и с прямыми эфирами. Сервер пока в тестировании.

### Установка расширения

Пока расширения нет в Chrome Web Store, оно ставится из архива в режиме разработчика.

1. Откройте последний релиз: https://github.com/vladbehash/dubber-releases/releases/latest (туда же ведёт
   кнопка «Установить в Chrome» на mydubber.com) и в разделе **Assets** скачайте **`dubber-extension.zip`**.
2. Распакуйте архив в папку, которую не будете удалять, например `Документы\myDubber-extension` (правой кнопкой
   по zip → **Извлечь всё**). Chrome читает расширение из этой папки: удалите её — расширение пропадёт.
3. Откройте в адресной строке `chrome://extensions` (в Edge — `edge://extensions`) и включите **Режим
   разработчика** (переключатель справа сверху; в Edge — слева).
4. Нажмите **Загрузить распакованное** и выберите распакованную папку — ту, в которой лежит файл
   `manifest.json`. Если Chrome пишет «Не удалось загрузить манифест», вы выбрали папку уровнем выше.
5. dubber появится в списке. Нажмите на значок пазла справа от адресной строки и закрепите dubber, чтобы его
   иконка была всегда под рукой: точка на ней показывает состояние озвучки.
6. Откроется страница первого запуска с выбором **Локально** или **Сервер** — дальше по одному из разделов ниже.

Chrome при каждом запуске будет предупреждать о расширении в режиме разработчика — это нормально, пока нет
публикации в магазине. Закройте предупреждение крестиком; не нажимайте «Отключить» — Chrome выключит расширение.

### Локально: установка бекенда

1. Из того же релиза скачайте **`my-dubber-setup.exe`** (или нажмите **Установить** на странице первого запуска
   — расширение скачает его само).
2. Запустите его. SmartScreen скажет «Windows защитила ваш компьютер» — установщик не подписан; нажмите
   **Подробнее → Выполнить в любом случае**. Откроется окно установщика со списком компонентов и их прогрессом:
   окружение Python, Ollama, Deno и модели качаются параллельно, около 20 ГБ, 15–30 минут. Окно можно закрыть:
   расширение покажет, что установка идёт, а бэкенд запустится сам, когда она закончится. Всё ставится в одну
   папку установки (на Windows `%LOCALAPPDATA%\myDubber`), ничего в систему. Если установка не прошла, нажмите
   **Повторить**; если и это не помогло, пришлите нам лог из папки `logs`.
3. Откройте видео на YouTube, нажмите на иконку dubber и включите **Озвучивать вкладку**. Бекенд запустится сам
   (первый раз ~1 минута: в попапе видно, что загружается). Видео встанет на паузу с надписью «Перевожу…» и
   пойдёт, когда будет готово. Через 10 минут без перевода бекенд сам выключится и освободит видеокарту.

Без аккаунта локальный бекенд работает в профиле «Лёгкий»; вход (хватит и бесплатного плана) открывает
«Средний» и «Полный».

### Сервер

1. На странице первого запуска выберите **Сервер** (или позже: попап → «Настройки» → бекенд «Сервер») и войдите:
   откроется окно mydubber.com, введите email и 6-значный код из письма или войдите через Google.
2. Откройте видео на YouTube, нажмите на иконку dubber и включите **Озвучивать вкладку**.
3. Если видео ещё никто не озвучивал, сервер запускает видеокарту: первый раз ждать 1–2 минуты (до ~20 минут
   при самом первом запуске сервера, пока он скачивает модели), попап показывает ожидание. Видео, которые уже озвучивали,
   начинаются сразу из общего кеша.

### Что ожидать

- Профиль железа выбирается сам по свободной видеопамяти (Полный / Средний / Лёгкий); его можно сменить в
  попапе. Если бекенд не успевает за видео, попап скажет об этом и посоветует, что сделать.
- Языки оригинала: любой из двенадцати (в том числе украинский, португальский, турецкий, польский) или
  автоопределение. Озвучка на: русский, английский, корейский, японский, китайский, испанский, немецкий,
  французский (украинского, португальского, турецкого и польского голоса пока нет).
- Каждый говорящий озвучивается похожим на него голосом; смена голоса на лету недоступна.
- Прямые эфиры работают с задержкой ~14 с от края эфира.

### Если что-то не так

- Логи бекенда: `logs\` (последний файл) и `cache\ollama.log` в папке установки (на Windows
  `%LOCALAPPDATA%\myDubber`). Присылайте их вместе со ссылкой на видео и временем.
- Попап → вкладка «Настройки» показывает, что с бекендом: не установлен, остановлен, ошибка с логом. Пока
  бекенд работает, в системном трее есть его значок: оттуда можно открыть логи или остановить его.
- Переустановка поверх — повторный запуск `my-dubber-setup.exe`. Удаление — «Программы и компоненты» → myDubber
  backend (удаляет всю папку с моделями).

### Обновление

Новый релиз бекенд ставит сам (с 0.1.11): пока ничего не переводится или перед переводом, если бекенд ещё не
запущен; видео в это время ждёт с бейджем «Обновляю бэкенд». Если обновление не прошло, бекенд вернётся на прежнюю
версию. Выключить это можно переключателем «Обновлять автоматически» в настройках — тогда попап предложит
обновиться кнопкой.
Расширение обновляется вручную: скачайте новый `dubber-extension.zip` из последнего релиза, распакуйте поверх той
же папки (с заменой файлов) и нажмите «Обновить» (круглая стрелка) у dubber на `chrome://extensions`.

## English

dubber dubs YouTube videos and live streams while you watch. It is a Chrome extension plus a **backend** — the
program that listens, translates and voices. The backend runs **locally** on your computer (free, needs an NVIDIA
GPU; nothing is sent anywhere) or **on our server** (any computer, needs an account).

### Requirements

- Chrome or Edge.
- **Local:** Windows 10/11, an NVIDIA GPU with 6 GB of memory or more (8+ is better; 12+ gives the best
  translation), ~15 GB of disk and a decent connection for the first install (~10 GB of models). No admin rights
  needed. Linux and macOS are not supported yet (they are planned) — only the server works there.
- **Server:** any computer and an account on mydubber.com (a code by email, or Google). Free: 60 minutes a month of
  recordings; Pro: unlimited minutes and live streams. The server is still in testing.

### Install the extension

Until the extension is in the Chrome Web Store, it is installed from a zip in Developer mode.

1. Open the latest release: https://github.com/vladbehash/dubber-releases/releases/latest (the **Add to Chrome**
   button on mydubber.com leads there too) and under **Assets** download **`dubber-extension.zip`**.
2. Unzip it into a folder you will keep, e.g. `Documents\myDubber-extension` (right-click the zip → **Extract
   All**). Chrome loads the extension from that folder: delete it and the extension is gone.
3. Open `chrome://extensions` (in Edge `edge://extensions`) and turn on **Developer mode** (the switch at the top
   right; on the left in Edge).
4. Click **Load unpacked** and pick the unzipped folder — the one that holds `manifest.json`. If Chrome says
   "Manifest file is missing or unreadable", you picked the folder above it.
5. dubber shows up in the list. Click the puzzle icon next to the address bar and pin dubber, so its icon is always
   one click away: its dot shows the dub's state.
6. A first-run page opens with two choices, **Local** or **Server** — follow one of the sections below.

Chrome warns about developer-mode extensions at every start — expected until the store listing. Close the warning
with its ×; don't click "Disable", or Chrome turns the extension off.

### Local: install the backend

1. From the same release download **`my-dubber-setup.exe`** (or click **Install** on the first-run page — the
   extension downloads it itself).
2. Run it. SmartScreen will say "Windows protected your PC" (the installer isn't signed): **More info → Run
   anyway**. The installer's window lists every component with its progress: the Python environment, Ollama, Deno
   and the models download side by side, about 20 GB, 15–30 minutes. The window can be closed: the extension shows
   that the install is running, and the backend starts by itself once it is done. Everything goes into one install
   folder (`%LOCALAPPDATA%\myDubber` on Windows), nothing system-wide. If the install fails, press **Retry**; if that
   does not help, send us the log from the `logs` folder.
3. Open a YouTube video, click the dubber icon and turn on **Dub this tab**. The backend starts by itself (the first
   time ~1 minute; the popup shows it loading). The video pauses with "Translating…" and plays once the dub is
   ready. After 10 minutes without a dub the backend exits and frees the GPU.

Without an account the local backend runs the Light profile; signing in (the Free plan is enough) unlocks Medium
and Full.

### Server

1. On the first-run page choose **Server** (or later: popup → Settings → backend "Server") and sign in: a
   mydubber.com window opens; enter your email and the 6-digit code we send, or continue with Google.
2. Open a YouTube video, click the dubber icon and turn on **Dub this tab**.
3. If nobody has dubbed the video yet, the server starts a GPU: the first time you wait 1–2 minutes (up to ~20 the
   very first time, while the server downloads its models); the popup shows the wait. Videos already dubbed start at once from the shared
   cache.

### What to expect

- The hardware profile (Full / Medium / Light) is picked from the free GPU memory; the popup lets you change it.
  When the backend can't keep up with the video, the popup says so and suggests what to do.
- Source languages: any of the twelve (Ukrainian, Portuguese, Turkish and Polish included) or auto-detect. Dub
  into: Russian, English, Korean, Japanese, Chinese, Spanish, German, French (no Ukrainian, Portuguese, Turkish
  or Polish voice yet).
- Each speaker is voiced by a voice like their own; there is no voice picker.
- Live streams play ~14 s behind the live edge.

### When something is off

- Backend logs: `logs\` (the newest file) and `cache\ollama.log` in the install folder (`%LOCALAPPDATA%\myDubber`
  on Windows). Send them with the video link and the time.
- The popup's Settings tab shows the backend's state: not installed, stopped, failed with the log. While the
  backend runs, its icon sits in the system tray: open the logs or stop it from there.
- Reinstall over the existing one: run `my-dubber-setup.exe` again. Uninstall: Apps & features → myDubber backend
  (removes the whole folder, models included).

### Updating

The backend installs a new release by itself (since 0.1.11): while nothing is dubbed, or before a dub whose backend
isn't running yet; the video waits meanwhile with an "Updating the backend" badge. A failed update goes back to the
previous version. The "Update automatically" switch in Settings turns it off; the popup then offers the update with a
button. The extension is updated by hand: download the new `dubber-extension.zip` from the latest release, unzip it over the
same folder (replacing the files) and press "Reload" (the round arrow) on dubber's card in `chrome://extensions`.

---

