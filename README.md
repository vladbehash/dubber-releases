# dubber — для тестеров / for testers

[Русский](#русский) · [English](#english)

## Русский

dubber переводит и озвучивает YouTube-видео и стримы прямо во время просмотра: расширение Chrome плюс
«бекенд» — программа на вашем компьютере, которая слушает, переводит и озвучивает. Всё работает локально,
ничего никуда не отправляется.

### Что нужно

- Windows 10/11, Chrome (или Edge). Linux и macOS пока не поддерживаются: они в планах (ADR 0011), а до тех
  пор на них работает только удалённый бекенд.
- Видеокарта NVIDIA с памятью от 6 ГБ (8+ лучше; 12+ даёт лучший перевод).
- ~15 ГБ на диске и хороший интернет для первой установки (модели ~10 ГБ).
- Права администратора не нужны.

### Установка

1. Скачайте из последнего релиза два файла: **`dubber-extension.zip`** и **`dubber-setup.exe`**:
   https://github.com/vladbehash/dubber-releases/releases/latest
2. Распакуйте zip в постоянную папку (не удаляйте её потом — Chrome читает расширение оттуда).
3. Chrome → `chrome://extensions` → включите **Режим разработчика** (справа сверху) → **Загрузить
   распакованное** → выберите распакованную папку. В панели расширений появится dubber; закрепите его.
   Chrome будет при каждом запуске предупреждать о расширении в режиме разработчика — это нормально, у нас
   пока нет публикации в магазине.
4. Запустите `dubber-setup.exe`. SmartScreen скажет «Windows защитила ваш компьютер» — установщик не подписан;
   нажмите **Подробнее → Выполнить в любом случае**. Откроется окно установщика со списком компонентов и их
   прогрессом: окружение Python, Ollama, Deno и модели качаются параллельно, около 20 ГБ, 15–30 минут. Окно
   можно закрыть: расширение покажет, что установка идёт, а бэкенд запустится сам, когда она закончится. Всё
   ставится в одну папку установки (на Windows `%LOCALAPPDATA%\dubber`), ничего в систему. Если установка
   не прошла, нажмите **Повторить**; если и это не помогло, пришлите нам лог из папки `logs`.
5. Откройте видео на YouTube, нажмите на иконку dubber и включите **Озвучивать вкладку**. Бекенд запустится
   сам (первый раз ~1 минута: в попапе видно, что загружается). Видео встанет на паузу с надписью «Перевожу…»
   и пойдёт, когда будет готово. Через 10 минут без перевода бекенд сам выключится и освободит видеокарту.

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
  `%LOCALAPPDATA%\dubber`). Присылайте их вместе со ссылкой на видео и временем.
- Попап → вкладка «Настройки» показывает, что с бекендом: не установлен, остановлен, ошибка с логом. Пока
  бекенд работает, в системном трее есть его значок: оттуда можно открыть логи или остановить его.
- Переустановка поверх — повторный запуск `dubber-setup.exe`. Удаление — «Программы и компоненты» → dubber
  backend (удаляет всю папку с моделями).

### Обновление

Когда выйдет новый релиз, попап покажет «Доступно обновление бекенда» с кнопкой — бекенд обновится сам.
Расширение обновляется вручную: скачайте новый `dubber-extension.zip`, распакуйте поверх той же папки и нажмите
«Обновить» на `chrome://extensions`.

## English

dubber dubs YouTube videos and live streams while you watch: a Chrome extension plus a **backend** — a program on
your computer that listens, translates and voices. Everything runs locally; nothing is sent anywhere.

### Requirements

- Windows 10/11, Chrome (or Edge). Linux and macOS are not supported yet: they are planned (ADR 0011); until
  then only a remote backend works there.
- An NVIDIA GPU with 6 GB of memory or more (8+ is better; 12+ gives the best translation).
- ~15 GB of disk and a decent connection for the first install (~10 GB of models).
- No admin rights needed.

### Install

1. From the latest release, download **`dubber-extension.zip`** and **`dubber-setup.exe`**:
   https://github.com/vladbehash/dubber-releases/releases/latest
2. Unzip into a folder you will keep (Chrome loads the extension from it).
3. Chrome → `chrome://extensions` → turn on **Developer mode** (top right) → **Load unpacked** → pick the unzipped
   folder. Pin dubber in the toolbar. Chrome warns about developer-mode extensions at every start — expected, there
   is no store listing yet.
4. Run `dubber-setup.exe`. SmartScreen will say "Windows protected your PC" (the installer isn't signed): **More
   info → Run anyway**. The installer's window lists every component with its progress: the Python environment,
   Ollama, Deno and the models download side by side, about 20 GB, 15–30 minutes. The window can be closed: the
   extension shows that the install is running, and the backend starts by itself once it is done. Everything goes
   into one install folder (`%LOCALAPPDATA%\dubber` on Windows), nothing system-wide. If the install fails, press
   **Retry**; if that does not help, send us the log from the `logs` folder.
5. Open a YouTube video, click the dubber icon and turn on **Dub this tab**. The backend starts by itself (the
   first time ~1 minute; the popup shows it loading). The video pauses with "Translating…" and plays once the dub
   is ready. After 10 minutes without a dub the backend exits and frees the GPU.

### What to expect

- The hardware profile (Full / Medium / Light) is picked from the free GPU memory; the popup lets you change it.
  When the backend can't keep up with the video, the popup says so and suggests what to do.
- Source languages: any of the twelve (Ukrainian, Portuguese, Turkish and Polish included) or auto-detect. Dub
  into: Russian, English, Korean, Japanese, Chinese, Spanish, German, French (no Ukrainian, Portuguese, Turkish
  or Polish voice yet).
- Each speaker is voiced by a voice like their own; there is no voice picker.
- Live streams play ~14 s behind the live edge.

### When something is off

- Backend logs: `logs\` (the newest file) and `cache\ollama.log` in the install folder (`%LOCALAPPDATA%\dubber`
  on Windows). Send them with the video link and the time.
- The popup's Settings tab shows the backend's state: not installed, stopped, failed with the log. While the
  backend runs, its icon sits in the system tray: open the logs or stop it from there.
- Reinstall over the existing one: run `dubber-setup.exe` again. Uninstall: Apps & features → dubber backend
  (removes the whole folder, models included).

### Updating

When a new release is out, the popup shows "Backend update available" with a button — the backend updates by
itself. The extension is updated by hand: download the new `dubber-extension.zip`, unzip over the same folder and
press "Reload" on `chrome://extensions`.

---

