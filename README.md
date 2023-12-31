## Комп'ютерні системи імітаційного моделювання
## СПм-22-5, **Ні Олег В'ячеславович**
### Лабораторна робота №**3**. Використання засобів обчислювального інтелекту для оптимізації імітаційних моделей

<br>

### Варіант 6, модель у середовищі NetLogo:
[Rabbits Grass Weeds](https://www.netlogoweb.org/launch#http://www.netlogoweb.org/assets/modelslib/Sample%20Models/Biology/Rabbits%20Grass%20Weeds.nlogo)

<br>

#### Вербальний опис моделі:
Модель передбачає наявність трьох ключових складових у природній спільноті: трава – слугує джерелом харчування для кроликів; кролики – споживають траву як свою основну їжу; бур'ян – рослини, що можуть конкурувати з травою за ресурси, але не є основною їжею для кроликів. Ця екосистемна модель дозволяє вивчати взаємодію цих компонентів та застосовувати її для розуміння екологічних концепцій, таких як динаміка популяцій, взаємодія хижак-жертва та вплив конкуренції між рослинними видами.

#### Керуючі параметри:
- **number-of-rabbits** - кількість кроликів в початковому стані середовища моделювання;
- **birth-threshold** - кількість енергії, необхідна кожному кролику для того, щоб мати можливість розмножуватися;
- **grass-grow-rate** - темп, з яким трава зростає в середовищі протягом кожного ігрового циклу;
- **grass-energ**y - кількість енергії, яку кролик отримує, споживаючи траву;
- **weeds-grow-rate** - швидкість зростання бур'яну в кожному ігровому циклі;
- **weeds-energy** - кількість енергії, яку кролик отримує, споживаючи бур'ян.

#### Показники роботи моделі:
- **поточна кількість трави** - це кількість трав'янистої рослини, доступної у даний момент часу для харчування для кроликів;
- **поточна кількість бур'яну** - кількість рослин, що можуть конкурувати з травою за ресурси, яка присутня в даний момент у середовищі;
- **поточна популяція кроликів** - це кількість кроликів, які проживають в даному середовищі в даний момент.

<br>

### Налаштування середовища BehaviorSearch:

**Обрана модель**:

Візьмемо модифікований варіант моделі з роботи №2. Ключові зміни:
- **отруєння кроликів бур'янами:** кролик може отруїтися під час поїдання бур'яну з певною вірогідністю. Отруєний кролик не може харчуватися, рухатися, розмножуватися, він залишається хворим протягом трьох ігрових тактів модельного часу;
- **розділення на самців та самок:** введено поділ кроликів на статеві категорії: самці та самки;
- **поява нових кроликів залежить від здоров'я та наявності партнера:** поява нащадків вимагає наявності ситого й здорового кролика протилежної статі в одній із сусідніх клітин. Випадковим чином народжується потомство з ймовірністю 50%;
- **"вік" кроликів та їх природна смертність:** кожен кролик має певний "вік" - кількість тактів, після яких він "помирає";
- **можливість народжувати тільки самкам:** кролики чоловічої статі можуть лише втрачати енергі. Лише кролики жіночої статі можуть народжувати потомство.

**Параметри моделі** (вкладка Model):

Параметри та їх можливі діапазони були автоматично вилучені середовищем BehaviorSearch із вибраної імітаційної моделі, для цього є кнопка «Завантажити діапазони параметрів із інтерфейсу моделі»:

<pre>
["grass-grow-rate" [0 1 20]]
["weeds-grow-rate" [0 1 20]]
["grass-energy" [0 0.5 10]]
["weed-energy" [0 0.5 10]]
["number" [0 150 500]]
["birth-threshold" [5 1 20]]
</pre>

Збільшення нижнього порогу енергії, необхідного для репродукції кроликів з 0 до 5, відображає більш реалістичну ситуацію. Така зміна враховує той факт, що для успішної репродукції кролики повинні мати певний рівень енергії, який дозволяв би їм не лише проживати, але й витрачати енергію на процес розмноження. Це збільшення енергетичного порогу для репродукції може призвести до змін у динаміці популяції кроликів, оскільки тепер репродуктивний процес стає доступним лише для тих особин, які мають достатньо енергії. Така модифікація може вплинути на швидкість збільшення популяції та регулювання кількості новонароджених кроликів у моделі.

**Використовувана міра**:

Міра фітнес-функції визначена на основі чисельності кроликів у середовищі імітаційної моделі в NetLogo. Ця оцінка отримана з встановлень графіків самої моделі.

<pre>count rabbits</pre>

Середня кількість кроликів у середовищі підраховується протягом усього періоду симуляції, що триває 500 тактів. Ця величина змінюється кожен такт, починаючи з 0 такту симуляції (параметр "Step limit"). Для досягнення цього використовується параметр "Measure if" зі значенням "true". Іноді, особливо на початку використання деяких моделей, є сенс не враховувати певні такти через хаотичність. Для цього можна вказати специфічні умови у параметрі "Measure if". Параметри "Setup" та "Go" вказують на відповідні процедури ініціалізації та запуску у логіці моделі. В процесі роботи BehaviorSearch самостійно запускає ці процедури замість користувача. Варто зауважити, що у цій роботі параметр зупинки за умовою ("Stop if") не використовується.

**Вкладка налаштувань параметрів моделі**:

<img width="661" alt="image" src="https://github.com/olehni1/ksim_lab_3/assets/150624205/8914cf3d-71e8-43d8-9ead-a66a1c06b397">

<br>
<br>

**Налаштування цільової функції** (вкладка Search Objective):

Головною метою відбору параметрів у імітаційній моделі є досягнення максимального значення середньої популяції кроликів у їх середовищі (тобто пошук таких налаштувань моделі, за яких середнє значення популяції кроликів буде найвищим). Це досягається через використання параметра "Goal" із значенням "Maximize Fitness". Важливо відзначити, що нас цікавить не лише значення популяції у конкретний момент симуляції, а й її середнє значення протягом всієї тривалості симуляції, яка складає 500 кроків. Для цього використовується параметр "Collected measure" зі значенням MEAN_ACROSS_STEPS. Щоб уникнути спотворень результатів через випадковість в самій моделі, кожну симуляцію повторюють 10 разів, і результати обчислюються як середнє значення цих декількох запусків.

**Вкладка налаштувань цільової функції**:

<img width="662" alt="image" src="https://github.com/olehni1/ksim_lab_3/assets/150624205/6cd461e3-3800-4788-bb13-f125b8aedbe3">

<br>
<br>

**Налаштування алгоритму пошуку** (вкладка Search Algorithm):

На даному етапі було створено модель, налаштовані її параметри та обрано міру ефективності, яка формує основу функції пристосованості. Ця міра дозволяє оцінити "якість" кожної альтернативи рішення, яка перевіряється BehaviorSearch. У процесі дослідження використовуватимуться два алгоритми: Випадковий пошук (RandomSearch) і Стандартний генетичний алгоритм (StandardGA). Для цих алгоритмів потрібно вказати "Evaluation limit" (кількість ітерацій пошуку, у випадку GA - це буде кількість поколінь) та "Search Space Encoding Representation" (спосіб кодування варіанта рішення). Немає загальноприйнятого "найкращого" способу кодування, тому необхідно визначити, які підходять для конкретної моделі. Параметр "Use fitness caching" впливає лише на продуктивність.

**Вкладка налаштувань пошуку** (Random Search):

<img width="662" alt="image" src="https://github.com/olehni1/ksim_lab_3/assets/150624205/c33aad3d-9eb6-49f7-87b1-edf68440a713">

<br>
<br>

**Вкладка налаштувань пошуку** (StandardGA):

<img width="661" alt="image" src="https://github.com/olehni1/ksim_lab_3/assets/150624205/4d241a16-f368-43a1-8531-98594307c1c5">

<br>

### Результати використання BehaviorSearch:

Результат пошуку параметрів імітаційної моделі, використовуючи **генетичний алгоритм**:  

<img width="1005" alt="image" src="https://github.com/olehni1/ksim_lab_3/assets/150624205/d4bddc33-fde6-46a0-9661-58e8cf33823a">

<br>
<br>

Результат пошуку параметрів імітаційної моделі, використовуючи **випадковий пошук**:

<img width="1008" alt="image" src="https://github.com/olehni1/ksim_lab_3/assets/150624205/6fde33a2-53c1-48fd-8f23-db0eb88b7ac4">

