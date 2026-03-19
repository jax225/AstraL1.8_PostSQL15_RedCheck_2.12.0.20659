# 🚀 Easy Switcher для Astra Linux SE 1.8 (и не только)

> **Easy Switcher** — легковесный демон для автоматической смены раскладки клавиатуры, аналог Punto Switcher для Linux.  
> Работает на уровне ядра, не зависит от окружения рабочего стола.

---

## 📥 Установка

### 1. Скачать пакет

Перейди на страницу релизов и скачай последнюю версию `.deb`-пакета (сейчас это Easy Switcher v0.4):

🔗 [https://github.com/freemind001/easy-switcher/releases](https://github.com/freemind001/easy-switcher/releases)

Файл: **`easy-switcher.deb`**  
Сохрани в папку `Загрузки`.

### 2. Установка в терминале

```bash
cd ~/Загрузки/

# Установка дополнительных зависимостей
sudo apt update
sudo apt install wget dpkg-dev

# Установка пакета
sudo dpkg -i easy-switcher.deb

# Если возникнут ошибки зависимостей
sudo apt --fix-broken install
```

---

## ⚙️ Настройка

```bash
sudo easy-switcher -c
```

### В процессе настройки:
1. Нажми **Enter**, чтобы начать.
2. Нажми **реальную комбинацию смены раскладки**, используемую в системе, которой вы сейчас переключаете язык в вашей системе:
   - `Ctrl+Shift` (чаще всего)
   - `Alt+Shift`
   - `Super+Space` (Windows + Пробел)
3. Нажми клавишу для **ручной коррекции** (рекомендуется `Pause/Break`).

✅ Конфигурация сохранится в `/etc/easy-switcher/default.conf`

---

## ⚙️⚙️ Тонкая настройка, если пропадает текст при переключении

```
# Необходимо изменить настройки приложения
sudo nano /etc/easy-switcher/default.conf
```


Найдите парамет delay и установите увеличте его значение 

```bash
delay=20 # 30/40/50
```

После каждого изменения параместра нужно перезапускать службу и проверять в текстовом редакторе
sudo nano /etc/easy-switcher/default.conf

```bash
sudo systemctl restart easy-switcher
```

## 🧠 Управление сервисом

```bash
# Запуск
sudo systemctl start easy-switcher

# Остановка
sudo systemctl stop easy-switcher

# Перезапуск
sudo systemctl restart easy-switcher

# Статус
sudo systemctl status easy-switcher

# Автозагрузка
sudo systemctl enable easy-switcher
```

---

## 🎮 РЕЖИМЫ РАБОТЫ

### Режим 1: Исправление последнего слова

| Действие | Результат |
|----------|-----------|
| Напечатал: `Ghbdtn` | 😱 |
| Нажми **`Pause`** | ✅ Превратится в `Привет` |
| **Фишка:** | Работает с последним словом под курсором |

### Режим 2: Исправление всей фразы

| Действие | Результат |
|----------|-----------|
| Напечатал целое предложение: `Ghbdtn vfrcbf hfccrfpf` | 😫 |
| Нажми **`Shift + Pause`** | ✨ Вся предыдущая фраза превращается в `Привет марсия рассказ` |
| **Функция:** | Программа стирает ВСЁ от последнего Enter и печатает заново |

---

## 🧹 Удаление

```bash
sudo dpkg -r easy-switcher
sudo systemctl disable easy-switcher
```

---

## 📋 Логи и диагностика

```bash
# Логи в реальном времени
journalctl -u easy-switcher -f

# Режим отладки (перед этим останови сервис)
sudo systemctl stop easy-switcher
sudo easy-switcher --debug
# Выход: Ctrl+C, затем запустить сервис заново
```

---

## 📌 Примечания

- Программа работает **только с последним словом или фразой** (не с выделением мышкой).
- Используется клавиша `Pause`, так как она редко занята другими приложениями.
- Совместима с **Ubuntu 22.04**, **Astra Linux SE 1.8** и другими дистрибутивами на ядре Linux.
- Разработчик: [freemind001](https://github.com/freemind001/easy-switcher)

---

## 🧪 Проверка после установки

```bash
# Открой любой текстовый редактор
# Напечатай: Ghbdtn vfrcbf
# Нажми Shift + Pause
# Результат: Привет марсия
```

---

