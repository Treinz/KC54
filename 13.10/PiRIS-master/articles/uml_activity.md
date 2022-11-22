# Диаграмма деятельности (activity)

<!-- https://sites.google.com/site/anisimovkhv/learning/pris/lecture/tema14/tema14_3 -->

При моделировании поведения системы возникает необходимость не только представить процесс изменения ее состояний, но и детализировать особенности алгоритмической и логической реализации выполняемых системой операций. Для описания поведения системы и ее отдельных элементов (поведенческих моделей) в UML предусмотрено четыре вида диаграмм. Три из них ([диаграммы автоматов](../articles/uml_state.md), [последовательности и коммуникации](../articles/uml_sequence.md)) были рассмотрены ранее. Несмотря на то, что эти три вида диаграмм, так или иначе, отображают динамические аспекты системы, они недостаточно формальны для детального описания алгоритмов работы. В структурном подходе для этого применяются блок-схемы, диаграммы EPC и BPMN. В UML аналогом блок-схем являются диаграммы деятельности (активности), схожие с ними по своей семантике и выразительным средствам (набору элементов).

Каждая диаграмма деятельности акцентирует внимание на последовательности выполнения определенных действий, которые в совокупности приводят к получению желаемого результата. Они могут быть построены для отдельного варианта использования, кооперации, метода и т. д. Диаграммы деятельности являются разновидностью диаграмм автоматов, но если на второй основное внимание уделяется статическим состояниям, то на первой – действиям.

Графически диаграмма деятельности, как и диаграмма автоматов, представляется в виде ориентированного графа, вершинами которого являются действия или деятельности, а дугами – переходы между ними. Напомним, что в UML действие – это атомарная операция, выполнение которой не может быть прервано, а деятельность – составная операция, с возможностью ее прерывания. Переход к следующему действию или деятельности срабатывает сразу по их завершении.

Основными элементами диаграммы являются:

- исполняемые узлы;

- объекты;

- переходы;

- управляющие узлы;

- коннекторы;

- группирующие элементы.

1. К исполняемым узлам (англ. executable nodes) относятся действия (англ. action) и деятельности (англ. activity). На блок-схемах их аналогами являются процессы и предопределенные процессы. Обычное использование исполняемых узлов заключается в моделировании одного шага выполнения алгоритма (процедуры) или потока управления. Графически исполняемые узлы отображаются, как простые и составные состояния.

	     	
a) действие	     	б) деятельность
Рис. 14.14. Примеры исполняемых узлов

Внутри фигуры записывается выражение действия (англ. action expression), записываемое на естественном языке, некотором псевдокоде или языке программирования.

2. К объектам относятся непосредственно объекты (англ. object) в традиционном понимании UML, отправка сигнала (англ. send signal), прием сигнала (англ. accept signal) и событие времени (англ. time event).

	     		     		     	
a) объект	     	б) посылка сигнала	     	в) прием сигнала	     	г) событие времени
Рис. 14.15. Примеры объектов

Отображение сигнала на диаграмме может вызвать затруднения - рисовать его как отправку или прием? В частности, сигнал «Заказ сформирован» может рассматриваться как в одном, так и в другом смысле. Если в результате действия генерируется сигнал для последующей обработки (из символа действия исходит стрелка и входит в символ сигнала), то он отображается как «отправка сигнала». Когда сигнал поступает на обработку (из символа сигнала исходит стрелка и входит в символ действия), то он отображается как «прием сигнала».

3. Переход (англ. transition или activity edge), как и на диаграмме автоматов, отображается ассоциацией. На диаграммах деятельности различают следующие виды переходов.

	     		     	
a) поток управления	     	б) объектный поток	     	в) поток прерывания или исключения
Рис. 14.16. Примеры переходов

Поток управления (англ. control flow) представляет собой самый общий вид перехода и задает порядок выполнения операций. Когда на диаграмме необходимо помимо передачи управления отобразить и передачу информации, показывают объектный поток (англ. object flow). В этом случае ассоциации соединяются с символом «объекта» или специальными контактов (англ. pins), прикрепленными к границам действий. К границе действия может быть прикреплено несколько контактов с наименованиями отправляемых/получаемых данных (объектов). Поток прерывания (англ. interruptible flow), как правило, исходит из символа «прием сигнала», расположенного в прерываемой области, и входит в действие - обработчик прерывания. Поток исключения (англ. exception flow) используется так же, как и поток прерывания. Отличие прерывания от исключения состоит в том, что первое - это допустимое альтернативное событие в системе, а второе - ошибка при выполнении действия.

4. Управляющим узлам (англ. control nodes) на диаграмме деятельности соответствуют псевдосостояния на диаграмме автоматов.

Таблица 14.1. Соответствие между управляющими узлами и псевдосостояниями

Обозначение	Наименование
на диаграмме
автоматов	на диаграмме
деятельности
	Начальное псевдосостояние
(англ. initial pseudostate)	Начальный узел
(англ. initial node)
	Конечное состояние
(англ. final state)	Завершение деятельности
(англ. activity final)
	Точка выхода
(англ. exit point pseudostate)	Завершение потока
(англ. flow final)
	Ветвление
(англ. fork pseudostate)	Ветвление
(англ. fork node)
	Соединение
(англ. join pseudostate)	Соединение
(англ. join node)
	Выбор
(англ. choice pseudostate)	Слияние / решение
(англ. merge / decision node)
5. Коннекторы (англ. connectors) выступают в качестве соединителей, применяемых на блок-схемах. Они используются для прерывания потока в одной части диаграммы и продолжении в другой, если диаграмма занимает несколько листов или отображение потока перенасыщает диаграмму. Коннектор представляется в виде круга, внутри которого пишется его идентификатор.

	     	
a) без коннекторов	     	б) с коннекторами
Рис. 14.7. Пример использования коннекторов

6. К группирующим элементам (англ. activity groups) относятся разделы деятельности (англ. activity partitions) и прерываемые регионы (англ. interruptible activity regions). Разделы деятельности обычно используют для моделирования бизнес-процессов или совместной работы нескольких сущностей (актеров, объектов, компонентов, узлов и т.д.). В этом случае диаграмма делится на разделы (области) вертикальными или горизонтальными линиями, в заголовке которых указываются имена сущностей, ответственных за выполнение действий внутри соответствующего раздела. Прерываемый регион группирует действия, обычная последовательность выполнения которых может прервана в результате наступления нестандартной ситуации (например, при оформлении кредита клиент от него отказывается). Он отображается четырехугольником со скругленными углами и штриховым контуром.

 

14.6. Правила и рекомендации по разработке диаграмм деятельности

 

При разработке диаграммы следует придерживаться следующих правил и рекомендаций [26].

1. При построении диаграмм рекомендуется использовать классические принципы моделирования – декомпозиции и иерархического упорядочения. Т.е. при моделировании алгоритма вначале строится контекстная диаграмма с деятельностями, которые после детализируются с помощью соответствующих диаграмм декомпозиции.

2. Количество пересечений линий следует минимизировать. При этом считается, что пересекающиеся линии не имеют логической связи друг с другом. Другими словами потоки данных или управления в местах пересечений не меняют своего направления.

3. Если на диаграмме имеется ветвление / решение на параллельные или альтернативные потоки, то должно указываться и соответствующее соединение / слияние этих потоков.

4. При использовании альтернативных потоков каждый из них должен быть специфицирован с помощью сторожевого условия. Сторожевые условия не должны допускать одновременного срабатывания двух и более переходов.

5. В целях определения зоны ответственности (набора действий) сущностей рекомендуется использовать разделы деятельности.

 

14.7. Примеры построения диаграмм деятельности

 

На следующем рисунке показана упрощенная контекстная диаграмма определения допускаемых скоростей (диаграмма деятельности конструктора – метода инициализации объекта класса ru.iskraPUT.obrData.RachetVdop).



Рис. 14.18. Контекстная диаграмма деятельности конструктора класса RachetVdop

Вместо стереотипного символа, обозначающего деятельность, на диаграмме указан текстовый стереотип «subactivity».

На следующем рисунке показана диаграмма декомпозиции для деятельности «Расчет допускаемых скоростей на перегонах».



Рис. 14.19. Диаграмма декомпозиции «Расчет допускаемых скоростей на перегонах»

Расчет допускаемых скоростей на прямых (слева) и в кривых (справа) участках пути распараллелен. Циклы по однородным участкам прямых и кривым смоделированы с помощью элемента «Слияние / Решение».

Для каждого прямого участка пути определятся допускаемые скорости findVdop() в зависимости от конструкции верхнего строения пути (ВСП), а также заданных марки локомотива и типа вагонов. В качестве исходных данных для работы метода findVdop() принимаются:

- объект normatLoc или normatVag, содержащий нормативные данные об установлении допускаемых скоростей для соответствующей марки локомотива или типа вагонов;

- параметры верхнего строения пути для текущего однородного участка прямой:

o тип рельсов tipRels;

o приведенный износ рельсов privIsnos;

o эпюра шпал epurChpal;

o тип балласта tipBallast.

Для локомотива и вагонов скорости могут определяться параллельно. Результат (скорости) запоминается в соответствующих объектах с помощью метода saveVdopVSP().

Для каждой кривой вначале определяется величина прямой вставки d между текущей кривой и ближайшими кривыми, расположенными справа и слева от нее. Далее определяется тип кривой tipCurve (одиночная, сопряженная или составная) и в зависимости от него выполняется расчет пакета допускаемых скоростей:

- по конструкции ВСП и локомотива;

- конструкции ВСП и вагонов;

- норме непогашенного ускорения;

- норме скорости изменения непогашенного ускорения;

- норме скорости подъема колеса на рельс.

Допускаемые скорости по кривой запоминаются в соответствующих объектах с помощью метода saveVdopCurve().

На следующем рисунке приведен пример диаграммы деятельности с разделами деятельности. На диаграмме упрощенно показан процесс комплексной оценки проектных решений по проектированию новых или реконструкции существующих железных дорог. Для автоматизации процесса используются системы, входящие в программно-технологический комплекс ИСКРА.



Рис. 14.20. Диаграмма деятельности с разделами деятельности

С помощью символов ветвления и соединения показана возможность параллельного выполнения операций и их зависимость друг от друга. Так формирование задания на тягово-экономические расчеты и непосредственно расчеты движения поездов возможны только после выполнения расчета допускаемых скоростей.