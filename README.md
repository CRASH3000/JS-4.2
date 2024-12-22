# Домашнее задание к лекции «Модули и webpack»

**Важно**: задача выполняется в репозитории предыдущего задания (*Рабочее окружение современного проекта*).
**Важно**: ESLint не должен выдавать ошибок.

## Webpack

### Легенда

Ваш проект разросся, и его необходимо разделить на модули. Модули помогают обеспечить изолированность кода и внести порядок в проект. Но для работы с модулями необходимо настроить загрузчик модулей.

### Описание

Используйте следующую структуру, чтобы настроить экспорт в бандл:
- каталог `src`:
  - каталог `css`
    - файл `style.css` (в качестве содержимого используйте `body { color: #999; }`)
  - каталог `js`
    - файл `game.js` (в качестве содержимого используйте код из предыдущего задания)
  - файл `index.html` (шаблон для HTMLWebpackPlugin) (содержимое файла - произвольно, скрипты и стили должны подключаться автоматически, за счёт использования HTMLWebpackPlugin и MiniCssExtractPlugin)
  - файл `index.js` (Webpack entry point)
- файл `webpack.config.js`
- файл `package.json`
- другие файлы

Убедитесь, что после экспорта бандл запускается и работает (создайте для этого скрипт в npm, который запускает HTTP-сервер для каталога `dist`). HTTP-сервер выберите сами.

---

## Import/Export

### Легенда

Вы успешно настроили загрузку модулей с Webpack и сборку приложения. Пришло время всё грамотно разделить на модули!

### Описание

Разделите всё приложение на модули:
1. Модули персонажей. Для каждого типа персонажа используйте отдельный модуль
2. Модули оружий. Для каждого типа оружия используйте отдельный модуль
3. Модуль `game` - отвечающий за работу приложения (содержит функцию `play`)
4. Модуль `index` - отвечающий за запуск приложения (импортирует и запускает игру)

Реализуйте:
1. Описание всех классов из [итогового задания](../5%20Итоговое%20задание/README.md)
2. В модуле `index` код предыдущего задания нужно удалить.
3. Реализацию всех классов оставьте пустой (для текущего задания нужно только наличие классов и разделение их на модули)

Организуйте следующую систему импортов:
1. Файл `Weapon.js` не импортирует ничего
2. Файл `Arm.js` импортирует класс `Weapon` (используется для наследования)
3. Файл `Bow.js` импортирует класс `Weapon` (используется для наследования)
4. Файл `Sword.js` импортирует класс `Weapon` (используется для наследования)
5. Файл `Knife.js` импортирует класс `Weapon` (используется для наследования)
6. Файл `Staff.js` импортирует класс `Weapon` (используется для наследования)
7. Файл `LongBow.js` импортирует класс `Bow` (используется для наследования)
8. Файл `Axe.js` импортирует класс `Sword` (используется для наследования)
9. Файл `StormStaff.js` импортирует класс `Staff` (используется для наследования)
10. Файл `Player.js` импортирует класс `Arm` (используется как начальное оружие игрока) и класс `Knife` (используется для смены оружия)
11. Файл `Archer.js` импортирует класс `Player` (используется для наследования) и класс `Bow` (используется как начальное оружие)
12. Файл `Warrior.js` импортирует класс `Player` (используется для наследования) и класс `Sword` (используется как начальное оружие)
13. Файл `Mage.js` импортирует класс `Player` (используется для наследования) и класс `Staff` (используется как начальное оружие)
14. Файл `Dwart.js` импортирует класс `Warrior` (используется для наследования) и класс `Axe` (используется как начальное оружие)
15. Файл `Crossbowman.js` импортирует класс `Archer` (используется для наследования) и класс `LongBow` (используется как начальное оружие)
16. Файл `Demourge.js` импортирует класс `Mage` (используется для наследования) и класс `StormStaff` (используется как начальное оружие)
17. Файл `game.js` импортирует все классы персонажей (п.п. 11-16)
18. Файл `index.js` импортирует функцию `play`

С самими функциями и классами ничего делать не нужно, нужно только правильно расставить инструкции `import`/`export`.