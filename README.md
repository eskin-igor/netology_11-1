# netology_11-1

## Домашнее задание к занятию «Базы данных, их типы»

## Задание 1. СУБД

Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.
Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1.  Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.
1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?
1.2.  Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.
1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?
1.3.  Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.
1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?
1.4.  Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.
1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?
1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

Приведите ответ в свободной форме.

## Решение 1:

1.1. Реляционная СУБД.
1.2. Для CRM и Landing page - Реляционная СУБД.
1.3. Документо-ориентированные или Реляционные СУБД.
1.4. Графовые или Реляционные СУБД.

## Задание 2. Транзакции

2.1.  Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.
2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

Приведите ответ в свободной форме.

## Решение 2:

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.

Начало пополнения счета телефона (в дальнейшем СТ) на необходимую сумму с любого другого счета (в дальнейшем ЛДС), имеющего возможность пополнить счет телефона на необходимую сумму СТ. Начало транзакции. Соединение с базой данных ЛДС. Чтение баланса ЛДС. Ввод необходимой возможной суммы для перевода на СТ.
Далее произойдет уменьшение баланса ЛДС на введенную сумму.
Сохранится новый баланс ЛДС.
Далее будет соединение с базой данных СТ и чтение баланса СТ.
Увеличение баланса СТ на введенную сумму из пункта 1.
Сохранится новый баланс СТ. Далее, при успешном выполнении всех действий выше, происходит COMMIT всех изменений и конец транзакции. В ином случае все действия отменяются (ROLLBACK).

## Задание 3. SQL vs NoSQL

3.1.  Напишите пять преимуществ SQL-систем по отношению к NoSQL.
3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

Приведите ответ в свободной форме.

## Решение 3:

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.

Надежность и безопасность. Структурированная модель данных и наличие ограничений и правил безопасности делают SQL очень надежным и безопасным.
Удобство использования и структура. SQL базы данных довольно просты в использовании за счет строгой структуры и возможности использовать стандартный SQL язык.
Эффективность и масштабируемость. SQL базы данных легко масштабируются и обрабатывают большие объемы данных. Типичная база данных SQL масштабируется по вертикали. Это означает, что за счет увеличения или уменьшения производительности CPU, RAM и SSD, можно увеличить или уменьшить нагрузку на сервер по необходимости.
Structured Query Language (SQL) - структурированный язык запросов. Является относительно простым и доступным языком разработки баз данных, так как в его синтаксисе для названия операций, фильтров и других модификаторов используются в основном обычные английские слова.
Еще выделил бы удовлетворение транзакционных требований ACID, независимость от конкретных СУБД и возможность переноса с одной вычислительной системы на другую.

## Задание 4. Кластеры

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.
На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?

Приведите ответ в свободной форме.

## Решение 4:

Буду выбирать на основе необходимых потребностей для стабильной и корректной работы. Критерии:
Согласованность и целостность данных.
Общее использование ресурсов.
Безопасность и отказоустойчивость.
Масштабируемость.
Производительность и нагрузка.
Лучше всего справится клиент-серверная модель (трехуровневая или многоуровневая архитектура). А точнее кластер серверов с балансировщиком, так как 1000 машин будет производить большое количество вычислений при работе с огромным количеством данных. Данная модель сможет удовлетворить потребности критериев, описанных выше.


Задания,помеченные звёздочкой, — дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже разобраться в материале.
