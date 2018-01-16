# Задание на JS
В первом задании вы подготовили бэкенд, во втором — вёрстку. Цель третьего задания — реализовать одностраничное приложение «Яндекс Переговорки», которое будет использовать все наработки из предыдущих заданий. Приложение должно обладать всей функциональностью, изображённой на макете из второго задания.

Необходимо реализовать следующие переходы между макетами:

* При клике по свободному «слоту» в списке переговорок происходит переход на форму создания встречи с заполненным временем проведения и названием переговорки; если пользователь меняет время, выбранная переговорка заменяется на блок рекомендаций — о нём ниже.
* При клике по кнопке «Создать встречу» также происходит переход на форму создания встречи, но без заполненных полей (блок рекомендаций отсутствует и появляется только после ввода времени проведения встречи).

Для блока рекомендаций необходимо реализовать функцию getRecommendation (описание интерфейса), которая будет подбирать подходящие переговорки для встречи, учитывая:

* количество участников и вместимость переговорок;
* близость переговорки ко всем участникам встречи (первыми в списке должны быть переговорки, для которых суммарное количество пройдённых всеми участниками этажей будет минимальным). Если все подходящие переговорки заняты, необходимо проверить, возможно ли освободить какую-то из них:
  а) Может быть, можно перенести встречу из неё в другую переговорку (например, меньших размеров).
  б) Если переговорки заняты не на весь период времени, стоит попробовать освободить одну из них, перенеся встречи в другие подходящие переговорки. Например, есть встреча с 11:00 до 12:00 и есть две подходящие переговорки А (занята с 11:00 до 11:30) и B (занята c 11:30 до 12:00). В таком случае можно перенести получасовую встречу из A в B, чтобы освободить А, или перенести встречу из B в A, чтобы освободить B. Вариант выбираем так, чтобы суммарное количество пройдённых всеми участниками этажей было минимальным.

Если не удалось найти никаких вариантов, необходимо выбрать подходящие переговорки, которые освободятся раньше других.

Всевозможные сценарии обработки некорректных данных, введённых пользователем, и системных ошибок, не описанных во втором задании, мы предлагаем продумать самостоятельно и спроектировать в качестве необязательного задания.

Мы не ограничиваем вас в выборе технологий, фреймворков и библиотек. Пожалуйста, для каждого выбранного инструмента напишите небольшое обоснование — зачем он нужен в вашем проекте и почему именно он.

Мы будем оценивать реализацию функциональности, а также:

* оформление кода;
* архитектуру приложения;
* организованную вами инфраструктуру для разработки;
* наличие и качество тестов;
* performance.



## Запуск
```
npm i
npm run dev
```

Опубликованная главная страница: https://alivander.github.io/shri-2018-task-3/public/index.html


# Процесс

1. Изучаем ТЗ.
2. Забираем файлы из первого задания.
3. Забираем файлы из второго задания (не только папку build, но и оригинальные файлы на случай, если нужно будет доработать верстку).
4. Объединяем package.json этих заданий в один.
5. Для просмотра в браузере оставляем сервер Express, а Browser-sync оставляем только для слежения за изменением файлов, их минификации и обновления в build.
6. Ищем способы получения данных с сервера. Узнаем про XMLHttpRequest на сайте https://learn.javascript.ru/ajax-xmlhttprequest. Пробуем получить данные. Не сразу, но получается.
7. Следующая задача - подставить эти данные в верстку. Читаем про шаблонизаторы, но: во-первых, времени осталось очень мало, во-вторых, не хочется тянуть на клиенте еще дополнительные библиотеки. Мне кажется их наличие увеличит длительность отрисовки страницы, так как перед ней будет нужно дождаться их загрузки. Выбираем другой путь - создаем шаблоны в разметке, в них выбираем нужные теги с помощью querySelector() и заполняемых их данными с помощью innerHTML, setAttribute и appendChild.
8. На 15.01 подстановка еще не реализована в полном объеме и не реализована функция getRecommendation. Но я отправила работу на проверку, так как боюсь что прием работ может закрыться в любой момент. После отправки продолжу работать над третьим заданием до 19.01 - есть вероятность, что на момент просмотра будет готово немного больше, чем на момент отправки. Планирую закончить примерно 19.01, но мне сложно предположить точнее.


## Общий процесс работы над заданиями

О Школе разработки интерфейсов я узнала в декабре от других участников интенсива Базовый HTML и CSS в HTML Academy. Я только что его закончила и даже успела сверстать адаптивный макетик на целых 247 строк css. Так что к заданиям я приступала имея в запасе только знания о фиксированной верстке с каплей семантики и доступности, css без методологий, существовании медиа-запросов и 6 строчек javascript (var, querySelector, classList, addEventListener, if ... else, preventDefault).

По идее я не должна здесь такое писать, скорее наоборот - все знаю, все умею. Но я не могу. Я просто в шоке))

Это было безумно интересно, слышать со стороны "Ты хоть ТЗ видела?", понимать что "миссия не выполнима" и все равно каждый день садиться и разбирать новый материал, пытаться выполнить такое сложное, но такое интересное задание. Не какой-то лендинг, а "настоящее" приложение. Я смотрела доклады на YouTube, лекции Яндекса, продвинутые интенсивы HTML Academy (с торрентов - каюсь). Представляете, теперь я не могу смотреть лекции на скорости меньше, чем 1.5 X) Вошло в привычку) Я читала статьи, документации, форумы, порой пытаясь просто получить пинок в нужном направлении. Я облазила большую часть сервисов Яндекса, выискивая в коде те или иные приемы реализации. Я страдала, верстая трехмесячный календарь, и боготворила людей, которые набирают эти тысячи тегов, пока не узнала о шаблонизаторах и template. Сейчас у меня началось обучение на Продвинутом HTML и CSS в HTML Academy, а я уже знаю как работать с консолью, настроить автоматизацию, имею предствление о БЭМ, базах данных и даже сервере и его взаимодействии с клиентом. И колличество строчек Javascrip, которые я знаю, потихоньку перевалило за несколько десятков.

И все благодаря тому, что существует такая Школа и возможность в нее попасть.

Я очень хочу к Вам попасть. Нет, ну правда) Мне нравится разработка и для меня это единственная возможность поучится оффлайн у профессионалов и поработать в команде. Я была бы согласна поработать за еду и опыт и в своем регионе, но если вбить в локальный поиск "верстальщик", то он не выдаст ни единой вакансии. Про "фронтедер" даже не заикаюсь. Мне просто не у кого учится. От слова "совсем". Я убеждена, что никакие лекции, доклады и интесивы не могут заменить опыт, получаемый от командной работы. Поэтому я хотела бы выжать максимум информации из первого этапа Школы и затронуть как можно больше технологий на втором.
Я понимаю, что сейчас знаний у меня не так уж много. Но я столько успела освоить за эти четыре недели в перемешку с праздниками. А до старта занятий еще целых 7 недель - Javascript меня ждет!)

В любом случае, каким бы ни было ваше решение, огромное вам спасибо за то, что так мотивируете расти и развиваться!
