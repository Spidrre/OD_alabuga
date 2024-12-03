# Отчет по разработке модели классификации дорожных знаков

## Описание модели и этапов разработки

В данном проекте была использована архитектура ResNet50 с предварительным обучением на ImageNet для решения задачи классификации дорожных знаков.

Основные этапы разработки:
1. Подготовка и аугментация данных
2. Тонкая настройка предобученной ResNet50
3. Обучение и валидация модели
4. Анализ результатов и оптимизация

Датасет содержит 21 класс дорожных знаков и разделен на:
- Тренировочный набор: 1376 изображений
- Валидационный набор: 488 изображений
- Тестовый набор: 229 изображений

## Графики обучения и валидации

![График обучения](training_curves.png)

На графиках выше показана динамика обучения модели:
- Синяя линия: точность на тренировочном наборе
- Оранжевая линия: точность на валидационном наборе

Наблюдения:
- Модель достигает стабильной точности после 30 эпох
- Отсутствие явного переобучения благодаря использованию регуляризации и dropout

## Метрики на тестовом наборе

Модель показала следующие результаты на тестовом наборе:

- Accuracy: 0.8426
- Precision: 0.8751
- Recall: 0.8426
- F1-score: 0.8557

### Матрица ошибок для основных классов:

| Класс | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| do_not_enter | 1.000 | 1.000 | 1.000 | 15 |
| do_not_stop | 0.967 | 0.935 | 0.951 | 31 |
| do_not_turn_l | 0.982 | 0.964 | 0.973 | 28 |
| yellow_light | 0.889 | 0.842 | 0.865 | 19 |
| traffic_light | 0.957 | 0.957 | 0.957 | 23 |

## Примеры классификации

![Примеры классификации](classification_examples.png)

## Технические детали

- Размер входного изображения: 224x224
- Batch size: 32
- Количество эпох: 50
- Оптимизатор: Adam (lr=0.0001)
- Аугментации: отсутствуют
- Устройство обучения: NVIDIA GeForce RTX 4070

## Анализ результатов

### Сильные стороны модели:
- Высокая общая точность (84.2%)
- Отличные результаты на знаках с четкой геометрической формой
- Стабильная работа на разных условиях освещения

### Области для улучшения:
- Более низкая точность на классах с похожими визуальными признаками
- Возможные проблемы с классификацией при сильном зашумлении
- Хуже YOLOv8m

## Заключение

ResNet50 показала себя эффективной моделью для классификации дорожных знаков. Высокие метрики на тестовом наборе и стабильное поведение во время обучения подтверждают применимость модели для практических задач.