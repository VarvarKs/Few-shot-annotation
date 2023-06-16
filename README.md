<h1 align="center">Few-shot для мультиклассовой разметки</h1>

<h3>Keywords:</h3> <p>data annotation, nlp, chatgpt, few-shot, spell checking</p>
<hr>
<h3>Описание проекта</h3>
	<p>Системе проверки правописания нужно отличать правильные незнакомые слова от ошибок. Решено разметить слова, которые система проверки не знает, методом few-shot, полученный результат будет использован для пополнения словарной базы спел-чекера/дообучения одной из существующих NER моделей.
<h3>Переменные окружения</h3>
    
Для работы программы нужен `ChatGPT API KEY`. Чтобы определить переменную среды для использования в одном рабочем процессе, можно использовать `env` ключ в файле рабочего процесса.
