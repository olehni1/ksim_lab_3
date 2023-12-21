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

**Параметри моделі** (вкладка Model)

Параметри та їх можливі діапазони були автоматично вилучені середовищем BehaviorSearch із вибраної імітаційної моделі, для цього є кнопка «Завантажити діапазони параметрів із інтерфейсу моделі»:
<pre>
["grass-grow-rate" [0 1 20]]
["weeds-grow-rate" [0 1 20]]
["grass-energy" [0 0.5 10]]
["weed-energy" [0 0.5 10]]
["number" [0 150 500]]
["birth-threshold" [5 1 20]]
</pre>
