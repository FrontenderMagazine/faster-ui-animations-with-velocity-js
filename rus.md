# Более быстрая анимация интерфейсов с Velocity.js

С точки зрения анимационного дизайна сайт Facebook.com феноменально статичен. Он 
намеренно упрощён для более широкого диапазона совместимости и для комфорта 
пользователей. Приложения Facebook для iOS, напротив, очень динамичны. В них 
приоритет отдан анимационному дизайну; они оставляют ощущение живых, воздушных 
приложений.

Цель этой статьи состоит в том, чтобы продемонстрировать, что для такого 
раздвоения нет оснований; вебсайтам могут быть присущи интерактивность и 
высококачественная анимация на том же уровне, который можно увидеть в мобильных 
приложениях.

Перед тем как погрузиться в примеры, давайте сначала разберёмся почему 
анимационный дизайн настолько целесообразен:

* **Улучшенная обратная связь**

UI и UX дизайнерам следует использовать паттерны настолько часто, насколько это 
возможно, так как пользователи ищут их подсознательно. Отзывчивые анимационные 
паттерны являются особенно важными в обеспечении позитивного опыта 
взаимодействия: ощущаете ли вы после нажатия кнопки, что она отреагировала на 
щелчок вашей мыши? После сохранения файла возникает ли у вас убеждение, что ваши 
данные действительно были переданы и сохранены?

* **Бесперебойная передача контента**

Анимационный дизайн позволяет избежать контекстуальных разрывов; 
распространённым примером является возникновение и закрытие модальных окон (как 
альтернатива полному переключению страниц).

* **Заполнение мёртвых зон**

Когда пользователи выполняют неинтересное задание на вашей странице, уровень их 
тонуса можно поднять с помощью звука, цветов и движения. Отвлечение внимания 
пользователя — отличный способ заставить время бежать быстрее.

* **Эстетическое украшение**

Анимационные дизайнеры убивают не один час на оттачивание анимационных переходов 
и настройки плавности по той же эстетической причине, по которой UI-дизайнеры 
корпят над цветами и комбинацией шрифтов на странице: продуманные до мелочей 
вещи кажутся более высококлассными.

В примерах ниже мы будем использовать [Velocity.js][1] — популярный анимационный 
движок, который существенно улучшает скорость UI-анимации. (Поведение 
Velocity.js идентично функции jQuery `$.animate()`, однако превосходит по 
эффективности анимацию jQuery и библиотеки анимации CSS вместе взятые.) В 
частности, в этой статье особое внимание уделено набору [UI pack][2], который 
позволяет быстро внедрить анимационный дизайн на ваши страницы. По желанию вы 
можете также посмотреть [сопроводительный обзор кода][3] для этой статьи (5 
минут), чтобы получить общее представление о том, с чем мы будем работать.

## Обзор набора UI Pack

После подключения набора UI pack (всего 1.8 Кб в архиве ZIP) к вашей странице, 
вы получите доступ к UI-эффектам, сгруппированным в две категории:

### Коллауты

Коллауты — это эффекты, привлекающие внимание к элементу с целью усилить 
интенсивность пользовательского опыта, например, подёргивание элемента для 
индикации ошибки ввода, мигание как свидетельство изменений на странице или 
подпрыгивание элемента когда пользователю пришло новое сообщение. 

<iframe id="cp_embed_Fybjq" src="//codepen.io/anon/embed/Fybjq?default-tab=result&amp;slug-hash=Fybjq&amp;theme-id=0&amp;height=268" scrolling="no" allowtransparency="true" allowfullscreen="true" class="cp_embed_iframe" style="width: 100%; overflow: hidden;" frameborder="0" height="268"></iframe>

### Переходы

Переходы — это эффекты, вследствие которых элемент появляется или исчезает из 
видимости. Каждый переход имеет направление нарастания или убавления. Ценность 
переходов состоит в более богатой визуализации выведения и скрытия контента, чем 
может быть достигнута простым анимированием прозрачности элемента. Взгляните на 
`slideUpIn`, переход, включающий в себя эффект небольшого скольжения:

<iframe id="cp_embed_aLhFC" src="//codepen.io/anon/embed/aLhFC?default-tab=result&amp;slug-hash=aLhFC&amp;theme-id=0&amp;height=268" scrolling="no" allowtransparency="true" allowfullscreen="true" class="cp_embed_iframe" style="width: 100%; overflow: hidden;" frameborder="0" height="268"></iframe>

Если бы вы следили за эволюцией анимационного дизайна интерфейса iOS, вы бы 
отметили, что интерфейс iOS приятен во взаимодействии благодаря наличию более 
дюжины эффектов перехода. UI pack от Velocity.js открывает это разнообразие 
переходов для всех вебсайтов.

Следует отметить, что благодаря производительности Velocity.js и 
оптимизированности UI pack, все эффекты из набора на 100% готовы к полноценному 
использованию в коммерческих целях.

Давайте погрузимся в несколько простых примеров кода.

## Использование набора UI Pack

Коллауты и переходы обозначаются через первый параметр Velocity: вместо 
стандартного обозначения свойства указывается название эффекта. Для сравнения, 
вот синтаксис *обычного* вызова Velocity.js, который ведёт себя так же, как 
`$.animate()` от jQuery:

    $elements.velocity({ opacity: 0.5 });

И на противовес ему ниже приведены вызовы Velocity.js с использованием эффектов 
из набора UI Pack:

    /* Встряска элемента. */
    $elements.velocity("callout.shake");

    /* Переход элемента в видимое состояние с помощью slideUp. */
    $elements.velocity("transition.slideUpIn");

Так же, как и обычные вызовы Velocity.js, UI-эффекты могут быть связаны друг с 
другом и принимать дополнительные условия:

    /* Вызов эффекта встряхивания продолжительностью 2000 мс, затем скольжение 
    вниз и выцветание видимости элемента*/
    $elements
    	.velocity("callout.shake", 2000)
    	.velocity("transition.slideDownOut");

Эффекты из набора UI pack также могут принимать три необязательных уникальных 
условия: `stagger`, `drag` и `backwards`.

### Разбивка на временные интервалы `stagger`

Укажите значение для `stagger` в миллисекундах для последовательной отсрочки 
анимации каждого элемента из комплекта на указанное время. (Добавление значения 
для `stagger` препятствует параллельной анимации элементов, что обычно выглядит 
не очень изящно).

    /* Анимированное появление элементов с периодическими интервалами в 250мс. */
    $divs.velocity("transition.slideLeftIn", { stagger: 250 });

<iframe id="cp_embed_mqsnk" src="//codepen.io/anon/embed/mqsnk?default-tab=result&amp;slug-hash=mqsnk&amp;theme-id=0&amp;height=268" scrolling="no" allowtransparency="true" allowfullscreen="true" class="cp_embed_iframe" style="width: 100%; overflow: hidden;" frameborder="0" height="268"></iframe>

### Задержка анимации `drag`

Установите для `drag` значение `true` чтобы постепенно увеличить 
продолжительность анимации каждого элемента в комплекте. Продолжительность 
анимации последнего элемента будет равна исходному значению анимации, в то время 
как продолжительность анимации предыдущих элементов будет постепенно 
приближаться к этому значению. 

В результате получается эффект плавного перехода для всех элементов. (Если у вас 
когда-либо перехватывало дух от демо анимированной типографики на основе After 
Effects, вам следует знать, что задержка анимации является ключевым, хотя и 
малозаметным компонентом, который лежит в основе их визуального великолепия.)

<iframe id="cp_embed_lxfie" src="//codepen.io/anon/embed/lxfie?default-tab=result&amp;slug-hash=lxfie&amp;theme-id=0&amp;height=268" scrolling="no" allowtransparency="true" allowfullscreen="true" class="cp_embed_iframe" style="width: 100%; overflow: hidden;" frameborder="0" height="268"></iframe>

### Выполнение в обратном порядке `backwards`

Установите для `backwards` значение `true` чтобы анимация начиналась с 
последнего элемента в комплекте. Это средство идеально подходит для эффекта 
перехода выцветания элементов, так как опция `backwards` позволяет зеркально 
повторить поведение плавно появляющихся элементов (такая анимация по умолчанию 
происходит в направлении от первого элемента к последнему).

<iframe id="cp_embed_fEKsw" src="//codepen.io/anon/embed/fEKsw?default-tab=result&amp;slug-hash=fEKsw&amp;theme-id=0&amp;height=268" scrolling="no" allowtransparency="true" allowfullscreen="true" class="cp_embed_iframe" style="width: 100%; overflow: hidden;" frameborder="0" height="268"></iframe>

Вместе эти три дополнительные опции приносят в веб всю мощь пакета программ для 
анимационного дизайна. Если использовать их с толком, результаты получаются 
чудесные, пока в процессе разработки вы не забываете о пользовательском опыте:

## Дизайн для пользовательского опыта

Приправляя страницу элементами анимационного дизайна легко увлечься и [перейти 
границу разумного][4]. Вот некоторые соображения, о которых стоит помнить:

* **Эффекты должны быстро заканчиваться**

Применяя переходы, разработчики часто допускают ошибку, позволяя им продолжаться 
слишком долго, что заставляет пользователей ждать без надобности. Никогда не 
позволяйте украшениям интерфейса негативно влиять на восприятие скорости вашего 
сайта. Если вы применяете эффект плавного появления для большого количества 
контента, пусть общая продолжительность анимации будет небольшой.

* **Используйте уместные эффекты**

К примеру, не стоит использовать эффект игривого подскакивания элементов на 
странице с деловым контентом.

* **Используйте эффекты с толком**

Использование переходов на каждом квадратном сантиметре страницы — это явный 
перегиб.

* **Избегайте чрезмерного повторения**

Избегайте переходов средней и большой продолжительности там, где они будут 
запускаться неоднократно.

* **Экспериментируйте**

Отыщите нужную продолжительность, комбинацию задержки анимации, разбивки на 
временные интервалы и отображения в обратном порядке, которые идеально подойдут 
каждой из ваших уникальных анимаций.

## Преимущества анимации на основе JavaScript

Давайте сделаем шаг назад и определим почему вообще приведение UI-переходов в 
действие с помощью JavaScript является хорошей идеей. Ведь если на то пошло, 
вплоть до настоящего момента наиболее часто такие эффекты применялись с помощью 
готовых CSS-классов из библиотек вроде [Animate.css][5]:

* Поскольку поведение эффектов из набора UI pack является идентичным стандартным 
вызовам Velocity.js, они могут сочетаться и принимать дополнительные условия 
(Что в сыром CSS может быть проблематичным).
* Все эффекты оптимизированы для максимальной производительности (и минимального 
взаимодействия с деревом документа).
* Элементы, анимированные с помощью UI pack, автоматически переключаются на 
`display: none` после перехода выцветания и назад на `display: block` или 
`inline` перед анимацией появления. (Чтобы добиться того же с помощью CSS, 
потребуется несколько вызовов и запутанный код).
* Velocity.js не делает текст расплывчатым. Если вам уже приходилось применять 
эффекты переходов в CSS, вы должны были заметить, что после окончания анимации 
текст может выглядеть нечётким, если не удалить связанный с анимацией класс. В 
Velocity.js это не происходит, поскольку её движок полностью подчищает ненужные 
эффекты переходов после завершения анимации.
* Эффекты работают повсюду, кроме Internet Explorer 8, в котором они вполне 
изящно заменяются на простое выцветание и появление. 

Учитывая все преимущества, в том числе отличную совместимость со всеми 
браузерами и устройствами (в том числе более старых моделей), вы не сможете 
найти оправдание тому, чтобы отложить начало экспериментов с анимационным 
дизайном на ваших сайтах. Приятного времяпровождения!

**Примечание:** Просмотрите [документацию Velocity.js][6] чтобы попробовать все 
эффекты из набора UI pack.

## Ссылки

* [Скачать Velocity на GitHub][7]
* [Галерея демо на основе Velocity][8]

[1]: http://julian.com/research/velocity/
[2]: http://julian.com/research/velocity/#uiPack
[3]: https://www.youtube.com/watch?v=CdwvR6a39Tg&hd=1
[4]: https://www.youtube.com/watch?v=FONN-0uoTHI
[5]: https://github.com/daneden/animate.css
[6]: http://julian.com/research/velocity/#uiPack
[7]: https://github.com/julianshapiro/velocity
[8]: http://codepen.io/collection/tIjGb/