# Лабораторная работа №2
## Отчет по лабораторной работе
### 1. Теоретическая база
Цель работы — научиться работать с предобученными моделями, использовать их эмбеддинги для создания новых моделей и решать задачу классификации текстов. В данной работе использована модель BERT (Bidirectional Encoder Representations from Transformers) для генерации эмбеддингов заголовков видео и построения нейронной сети для их классификации.

Модель BERT:

BERT основан на архитектуре трансформеров и обучен для учета контекста слов с обеих сторон. Это делает его идеальным для задач, где важен смысл текста.
Используется предобученная версия bert-base-uncased из библиотеки Hugging Face для извлечения эмбеддингов заголовков.
Классификация текстов:

Задача заключается в отнесении заголовков видео к одной из заданных категорий.
Для решения используется простая нейронная сеть, построенная на PyTorch.
Оценка качества модели проводится с использованием метрики F1-score.
Ключевые аспекты работы:

Предобработка заголовков видео.
Генерация эмбеддингов с помощью BERT.
Создание и обучение нейронной сети на основе эмбеддингов.
Оценка точности модели на тестовых данных.
2. Описание разработанной системы
Принцип работы системы:
Используется датасет с заголовками видео и их категориями.
Заголовки преобразуются в эмбеддинги с помощью модели BERT.
Эмбеддинги используются в качестве входных данных для нейронной сети.
Нейронная сеть обучается на тренировочной выборке и тестируется на тестовой выборке.
Оценка качества модели проводится с использованием метрики F1-score.
Архитектура:
Входные данные: текстовые заголовки видео.
Предобработка: токенизация заголовков, генерация эмбеддингов через BERT.
Модель: простая нейронная сеть с одним полносвязным слоем.
Функция потерь: CrossEntropyLoss.
Оптимизатор: Adam.
Инфраструктура: PyTorch, GPU (если доступен).
Алгоритм работы:
Загрузка данных: Датасет с заголовками видео и категориями загружается и фильтруется.
Генерация эмбеддингов: Используется токенизатор и предобученная модель BERT для извлечения эмбеддингов (векторное представление заголовков).
Обучение модели: Нейронная сеть обрабатывает эмбеддинги, минимизирует функцию потерь и обновляет веса.
Оценка: После обучения модель тестируется на отложенной выборке, вычисляется F1-score.
3. Результаты работы и тестирования системы
Пример выводов в процессе обучения:

Эпоха 1, Потери: 0.353399395942688
Эпоха 2, Потери: 0.08572502434253693
Эпоха 3, Потери: 0.3152550458908081
F1-Score: 0.0902
Основные результаты:
Использование эмбеддингов BERT позволяет эффективно извлекать семантические признаки текста.
Простая нейронная сеть на основе эмбеддингов показала неудовлетворительное качество на задаче классификации.
Метрика F1-score для тестовой выборки составила 0.0902, что указывает на малую точность классификации. Из чего можно сделать вывод, что у модели проблемы с переобучением. И нужно вводить большое количество эпох и уменьшить степень обучения.
4. Выводы по работе
Использование предобученных эмбеддингов BERT значительно упрощает решение задач классификации текстов, так как позволяет избежать обучения сложных моделей с нуля.
Простая архитектура нейронной сети способна достичь удовлетворительной точности при условии качественного представления входных данных.
Важную роль играет корректная предобработка текста (токенизация, обрезка длины и т.д.), так как она влияет на качество извлекаемых эмбеддингов.
PyTorch предоставляет удобные инструменты для построения и обучения моделей, включая поддержку GPU.
5. Использованные источники
Devlin J., Chang M.-W., Lee K., Toutanova K. BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding [электронный ресурс]. – 2019. – Режим доступа: https://arxiv.org/abs/1810.04805.
Hugging Face Transformers Documentation [электронный ресурс]. – Режим доступа: https://huggingface.co/docs/transformers/index (дата обращения: 25.12.2024).
PyTorch Documentation [электронный ресурс]. – Режим доступа: https://pytorch.org/docs/stable/ (дата обращения: 25.12.2024).
sklearn.metrics Documentation [электронный ресурс]. – Режим доступа: https://scikit-learn.org/stable/modules/model_evaluation.html (дата обращения: 25.12.2024).
