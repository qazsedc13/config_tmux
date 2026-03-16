# config_tmux

![License](https://img.shields.io/github/license/qazsedc13/config_tmux)
![tmux Version](https://img.shields.io/badge/tmux-%3E%3D2.6-green)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows%20%7C%20OpenBSD-blue)

Собственная конфигурация tmux на основе популярного проекта [Oh my tmux!](https://github.com/gpakosz/.tmux) (24.5k ★). Самодостаточная, красивая и универсальная конфигурация терминального мультиплексера.

---

## 🚀 Основные возможности

- **Двойной префикс**: `C-a` как дополнительный префикс при сохранении стандартного `C-b`.
- **Powerline-тема**: Визуальное оформление в стиле Powerline с информативной статусной строкой.
- **Максимизация панелей**: `<prefix> +` разворачивает текущую панель в новое окно.
- **Мышь**: Toggle режима мыши через `<prefix> m`.
- **Информация в статусе**: Заряд батареи, uptime, SSH/Mosh-сессии, загрузка CPU.
- **Интеграции**: PathPicker, Urlscan/Urlview для работы со ссылками и путями.
- **TPM**: Встроенная поддержка Tmux Plugin Manager для установки плагинов.
- **Copy-mode vi**: Привязки в стиле Vim для режима копирования.

---

## 🛠 Технологический стек

- **tmux**: Терминальный мультиплексер (версия ≥ 2.6).
- **Shell**: POSIX shell для скриптов конфигурации.
- **Зависимости**: awk, perl (Time::HiRes), grep, sed.
- **ОС**: Linux, macOS, OpenBSD, Windows (WSL/Cygwin).

---

## 📋 Предварительные требования

- **tmux**: 2.6+
- **Внешние утилиты**: awk, perl, grep, sed
- **Шрифт**: Powerline-совместимый или patched font
- **TERM**: `xterm-256color` вне tmux
- **ОС**: Linux, macOS, OpenBSD или Windows с WSL

---

## 🚀 Установка

### 1. Клонирование репозитория
```bash
cd
git clone https://github.com/qazsedc13/config_tmux.git
```

### 2. Создание символической ссылки
```bash
ln -s -f config_tmux/.tmux.conf .tmux.conf
```

### 3. Копирование локальной конфигурации
```bash
cp config_tmux/.tmux.conf.local .
```

### 4. Перезапуск tmux
```bash
tmux kill-server
tmux
```

### Альтернативная установка (через install.sh)
```bash
curl -fsSL "https://github.com/gpakosz/.tmux/raw/master/install.sh" | bash
```

---

## 💡 Основные привязки клавиш

| Клавиша | Описание |
| :--- | :--- |
| `<prefix> e` | Открыть `.tmux.conf.local` в редакторе |
| `<prefix> r` | Перезагрузить конфигурацию |
| `C-l` | Очистить экран и историю tmux |
| `<prefix> C-c` | Создать новую сессию |
| `<prefix> C-f` | Переключиться на сессию по имени |
| `<prefix> C-h` / `<prefix> C-l` | Навигация между окнами |
| `<prefix> Tab` | Перейти к последнему активному окну |
| `<prefix> -` | Разделить панель вертикально |
| `<prefix> _` | Разделить панель горизонтально |
| `<prefix> h/j/k/l` | Навигация между панелями (в стиле Vim) |
| `<prefix> H/J/K/L` | Изменение размера панелей |
| `<prefix> <` / `<prefix> >` | Поменять панели местами |
| `<prefix> +` | Максимизировать панель в новое окно |
| `<prefix> m` | Включить/выключить режим мыши |
| `<prefix> F` | PathPicker (выбор файлов) |
| `<prefix> U` | Urlscan/Urlview (работа с URL) |
| `<prefix> Enter` | Войти в copy-mode |
| `<prefix> p` | Вставить из верхнего буфера |
| `<prefix> P` | Выбрать буфер для вставки |

### Copy-mode (vi-режим)
| Клавиша | Описание |
| :--- | :--- |
| `v` | Начать выделение / visual mode |
| `C-v` | Переключить blockwise/visual mode |
| `H` | Перейти к началу строки |
| `L` | Перейти к концу строки |
| `y` | Копировать выделение в буфер |
| `Escape` | Отменить операцию |

---

## ⚙️ Настройка конфигурации

### Переменные для настройки

Отредактируйте `.tmux.conf.local` для персонализации:

| Переменная | Описание |
| :--- | :--- |
| `tmux_conf_theme_left_separator_main` | Основной разделитель слева (Powerline: `\uE0B0`) |
| `tmux_conf_theme_left_separator_sub` | Дополнительный разделитель слева (`\uE0B1`) |
| `tmux_conf_theme_right_separator_main` | Основной разделитель справа (`\uE0B2`) |
| `tmux_conf_theme_right_separator_sub` | Дополнительный разделитель справа (`\uE0B3`) |
| `tmux_conf_theme_status_left` | Левая часть статусной строки |
| `tmux_conf_theme_status_right` | Правая часть статусной строки |
| `tmux_conf_copy_mode_vi` | Включить vi-режим в copy-mode |

### Переменные статусной строки

- `#{battery_bar}` — горизонтальная полоса заряда батареи
- `#{battery_percentage}` — процент заряда
- `#{hostname}` — имя хоста (SSH-aware)
- `#{username}` — имя пользователя (SSH-aware)
- `#{uptime_y}` / `#{uptime_d}` / `#{uptime_h}` — uptime (годы/дни/часы)
- `#{loadavg}` — средняя загрузка CPU
- `#{circled_session_name}` — номер сессии в кружке (⓪–⑳)

**Пример настройки статусной строки:**
```bash
tmux_conf_theme_status_right='#(curl -m 1 wttr.in?format=3 2>/dev/null), %R | #{username}#{root} | #{hostname}'
```

---

## 🔧 Управление tmux

**Перезагрузка конфигурации:**
```bash
# Внутри tmux
<prefix> r
```

**Просмотр сессий:**
```bash
tmux list-sessions
```

**Подключение к сессии:**
```bash
tmux attach -t <session_name>
```

**Установка плагинов TPM:**
```bash
# Внутри tmux
<prefix> I  # Заглавная I
```

**Обновление плагинов:**
```bash
<prefix> u
```

---

## ⚠️ Устранение неполадок

**Статусная строка дублируется:**
Проблема с Unicode/wcwidth. Установите `LC_CTYPE` в UTF-8 locale:
```bash
export LC_CTYPE=en_US.UTF-8
```

**Символы Powerline не отображаются:**
Установите Powerline-шрифт (Source Code Pro, Fira Code, JetBrains Mono) или patched font.

**Конфликт настроек в `.local`:**
Добавьте `#!important` к строке:
```bash
bind c new-window -c '#{pane_current_path}' #!important
```

**Проблемы с WSL/Cygwin:**
Рекомендуется использовать WSL2 + Windows Terminal вместо Cygwin (forking очень медленный).

**tmux не запускается:**
Убедитесь, что версия tmux ≥ 2.6:
```bash
tmux -V
```

---

## 📄 Лицензия

Проект распространяется под лицензиями **MIT** и **WTFPL**.

---

## 📬 Контакты

- **Автор**: [qazsedc13](https://github.com/qazsedc13)
- **Репозиторий**: [config_tmux](https://github.com/qazsedc13/config_tmux)
- **Оригинал**: [gpakosz/.tmux](https://github.com/gpakosz/.tmux)
