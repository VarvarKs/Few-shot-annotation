<h1 align="center">Few-shot для мультиклассовой разметки</h1>

<h3>Keywords:</h3> <p>data annotation, nlp, chatgpt, few-shot, spell checking</p>
<hr>
<h3>Описание проекта</h3>
	<p>Системе проверки правописания нужно отличать правильные незнакомые слова от ошибок. Решено разметить слова, которые система проверки не знает, методом few-shot, полученный результат будет использован для пополнения словарной базы спел-чекера/дообучения одной из существующих NER моделей.
<h3>Переменные окружения</h3>
    
Для работы программы нужен `ChatGPT API KEY`. Чтобы определить переменную среды для использования в одном рабочем процессе, можно использовать `env` ключ в файле рабочего процесса.

<h3>Результаты</h3>
Методом few-shot получилось сделать разметку фрагмента датасета из отдельных слов (без контекста). 
Выделяемые группы:

	NEW - neologisms
	ORG - organisations, companies, apps
	SLN - slang
	NORM - normal (dictionary) words
	ERR - misspelled words
	PER - people, surnames
	GEO - geopolitical entities`

Пример результата:

	апасов	PER
	тайот	ORG
	халкиопов	PER
	патреон	ORG
	роберта	PER
	жестила	SLN
	балко	PER
	интеренета	ERR


<h3>Оценка результатов</h3>

Распределение групп сущностей в пяти прогонах на 10 000 слов

![image](https://github.com/VarvarKs/Few-shot-annotation/assets/74020946/50c9966f-2ef1-4831-a8e7-9f154cbfcd64)

Распределение довольно однородное. Прогоны четыре и пять явно отличаются, появилась новая сущность VERB, не указанная в спецификациях групп (галлюцинация).
Kappa score для первых трех результатов: ~0,915

Потреряны примерно 15-18% слов в каждом прогоне -- потеря связана с колличеством слов на разметку в одном запросе (при снижении количества слов до 100-150).

Сделана попытка сгенерировать контекст для каждого слова из датасета.
