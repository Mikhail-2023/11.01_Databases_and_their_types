# 11_01_Databases_and_their_types
# Домашнее задание к занятию «`Базы данных, их типы`» - `Колобов Михаил`

### Задание 1. СУБД

### Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать 
правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для
каждой предметной области. 

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему? 
 
1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков.
СУБД должна гарантировать целостность и чёткую структуру данных.

#### Ответ
***Поставленной задачей является работа с данными в табличной форме с информацией по объекту и должна гарантировать целостность и стройную структуру данных, для таких целей подходит реляционная СУБД***

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы? 

#### Ответ
***Для решения этой проблемы можно использовать такие решения которые не поведут к удорожанию проекта и в месте с тем имеют открытый исходный код, а именно, к примеру, для ускорения кэширования можно использовать Memcached***

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к 
маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? 
СУБД должны быть гибкими и быстрыми.

#### Ответ
***Чтобы обеспечить гибкость и быстродействие нужно использовать реляционная СУБД типа PostgresSQL***

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу 
и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

#### Ответ
***Отдел контроля качества постоянно пополняет и изменяет по мере необходимости данные, с учетом что база должна быть простой и интуитивно понятной, а значит тут подойдут СУБД по типу ключ-значение, одним из популярных решений является MongoDB***

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это 
реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов 
по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать
со связями.

#### Ответ
***Графовые NoSQL базы данных являются типичными базами данных которые предназначены для работы с графами, с их узлами, свойствами, и произвольными отношениями между узлами***

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД 
логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

#### Ответ
***Если принести в жертву быстродействие и производительность, потратить время на настройки то возможно реляционная СУБД сможет справиться со всеми задачами***

*Приведите ответ в свободной форме.*

---

### Задание 2. Транзакции

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы 
транзакция завершилась успешно. Ориентируйтесь на шесть действий.

#### Ответ
***Открытие транзакции. Открытие соединения с БД Банка;
Обращение к счету в банке и проверка наличия необходимых к переводу средств;
Введение суммы пополнения (блокировка для списания со счета в банке необходимой суммы);
Списание денег со счета пополняющего;
Зачисление на лицевой счет суммы, равной списанной суммы со счета в банке;
Получение подтверждения от оператора и отправка подтверждения пополняющему
Коммит изменений. Закрытие транзакции.***

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

#### Ответ
***Проводятся те-же самые действия, только без участия человека по запрограммированной команде.***

*Приведите ответ в свободной форме.*

---

### Задание 3. SQL vs NoSQL

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL. 

#### Ответ
***- надежность***
***- целостность***
***- структура не подверженная частым изменениям***
***- соблюдение жестких определений, как именно транзакции взаимодействуют с базой данных***
***- меньше вероятность неожиданного поведения системы***
***- проверенные и обкатанные решения для разных потребностей***

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

*Приведите ответ в свободной форме.*

---

### Задание 4. Кластеры

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу 
выделено 1000 машин. 

На основе какого критерия будете выбирать тип СУБД и какая модель *распределённых вычислений* 
здесь справится лучше всего и почему?

*Приведите ответ в свободной форме.*

#### Ответ
***Исходя из большого количества машин и того, что все машины будут связаны друг с другом и равны между собой, можно выбрать NoSQL с моделью "Сеть" т.к. сетевые базы данных имеют иерархическую структуру, но в отличие от иерархических баз данных, где у одного дочернего элемента может быть только один родитель, сетевой узел может иметь отношения с несколькими объектами***

---
