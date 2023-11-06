# Руформеры

![logo_cr.png](logo_cr.png)  

Список популярных открытых базовых моделей на основе трансформеров для решения задач по автоматической обработке русского языка

## Введение

Репозиторий содержит список популярных открытых моделей русского языка на основе трансформеров.

Архитектура трансформера была предложена в статье начала 2017 года [Attention is All You Need](https://arxiv.org/abs/1706.03762) исследователями из Google Brain и Google Research. Статья была посвящена задаче машинного перевода, однако в 2018-2019 годах появились модификации классического трансформера, такие как BERT, GPT и T5, которые показали отличные результаты во многих других NLP-задачах. Примерно в это же время стали появляться мультиязычные трансформеры, а также трансформеры для обработки русского языка.

Информация о трансформерах для обработки русского языка разбросана по просторам Интернета, поэтому возникла идея её собрать в одном месте и систематизировать. Я вдохновлялся вот этим замечательным каталогом: [блог](https://amatriain.net/blog/transformer-models-an-introduction-and-catalog-2d1e9039f376/), [статья на arxiv](https://arxiv.org/abs/2302.07730).
В нём охвачены модели для английского языка, а также мультиязычные трансформеры. Здесь же я хотел бы собрать наиболее востребованные предобученные базовые модели для русского языка.

Список будет пополняться. Буду благодарен за комментарии, исправления и помощь в обновлении списка.

### Какие модели подходят для включения в список?  

Данный список не стремится быть исчерпывающим. Мне кажется, что полезнее дать информацию о ключевых моделях, а не гнаться за полнотой. Мои критерии для включения в список:

1. **Архитектура**: трансформер (энкодер, декодер или энкодер-декодер).
2. **Обучающие данные**: претрейн модели осуществлялся преимущественно на русскоязычных данных. Именно по этому критерию я (пока?) не включаю в свой список изначально многоязычные модели.
3. **Применение**: базовые языковые модели, которые можно дообучать под широкий круг конкретных задач. Например, модель rubert-tiny2 подходит, потому что это энкодер предложений на русском языке. Такой энкодер можно использовать для различных задач классификации и регрессии. С другой стороны, модель rubert-tiny-sentiment-balanced не подходит, потому что она решает конкретную конечную задачу - сентимент-анализ.
4. **Популярность**: модель должна быть достаточно широко известна. Это, конечно, несколько субъективный критерий. Показателем популярности модели может быть, например, количество скачиваний в huggingface или количество цитирований статьи, где описывается модель.

## Список трансформеров для русского языка

### FRED-T5

**Описание**: семейство моделей (1.7B и large), похожих на ruT5, но с использованием смеси денойзеров (mixture of denoisers)  
**Ссылки**: [HF 1.7B](https://huggingface.co/ai-forever/FRED-T5-1.7B),
[HF large](https://huggingface.co/ai-forever/FRED-T5-large),
[Хабр](https://habr.com/ru/companies/sberdevices/articles/730088/),
[Arxiv](https://arxiv.org/abs/2309.10931)    
**Опубликована**: апрель 2023  
**Архитектура**: энкодер-декодер  
**Количество параметров**: 1.74B, 820M  
**На диске**: 6.96G, 3.28G  
**Длина контекста**: используется относительное позиционное кодирование, длина контекста ограничена лишь доступным объемом памяти  
**Применение**: сильная модель для решения задач вида "text-to-text" на русском языке  

---

### ruBERT (ai-forever)

**Описание**: семейство моделей (base и large) на основе классической архитектуры BERT (Devlin et al., 2019), обученных на 30 гигабайтах русскоязычных данных  
**Ссылки**: [HF base](https://huggingface.co/ai-forever/ruBert-base),
[HF large](https://huggingface.co/ai-forever/ruBert-large),
[Хабр](https://habr.com/ru/companies/sberbank/articles/567776/),
[Arxiv](https://arxiv.org/abs/2309.10931)  
**Опубликована**: 2021  
**Архитектура**: энкодер  
**Количество параметров**: 178M, 427M  
**На диске**: 716M,   
**Длина контекста**: 512 токенов  
**Применение**: задачи классификации и сравнения текстов; следует отметить, что ruRoBERTa-large обычно показывает более хорошие результаты по сравнению с ruBERT  

---

### ruBERT-tiny2

**Описание**: маленький и быстрый BERT для русского языка  
**Ссылки**: [HuggingFace](https://huggingface.co/cointegrated/rubert-tiny2),
[Хабр](https://habr.com/ru/articles/669674/),
[Colab](https://colab.research.google.com/drive/1mSWfIQ6PIlteLVZ9DKKpcorycgLIKZLf?usp=sharing)  
**Опубликована**: июнь 2022  
**Архитектура**: энкодер  
**Количество параметров**: 29M  
**На диске**: 118М  
**Длина контекста**: 2048 токенов  
**Применение**: несложные задачи классификации и сравнения текстов

---

### ruGPT-3

**Описание**: семейство генеративных моделей, основанных на архитектуре GPT-2 и обученных на русскоязычных данных  
**Ссылки**: [HuggingFace](https://huggingface.co/ai-forever/rugpt3large_based_on_gpt2),
[GitHub](https://github.com/ai-forever/ru-gpts?ysclid=lo5qq6e7w5304929210)  
**Опубликована**: октябрь 2020  
**Архитектура**: decoder  
**Количество параметров**: 1.3B, 760M, 355M, 125M  
**На диске**:  
**Длина контекста**:  
**Применение**: генерация текстов на русском языке, чатботы-"болталки"  

---

### ruGPT-3.5

**Описание**:  
**Ссылки**:  
**Опубликована**:  
**Архитектура**:  
**Количество параметров**:  
**На диске**:  
**Длина контекста**:  
**Применение**:  

---

### ru-Longformer-tiny-16384

**Описание**: маленькая модель на основе cointegrated/rubert-tiny2, но с длиной контекста до 16 тысяч токенов  
**Ссылки**: [HuggingFace](https://huggingface.co/kazzand/ru-longformer-tiny-16384),
[Хабр](https://habr.com/ru/companies/ru_mts/articles/761116/),
[Colab](https://colab.research.google.com/drive/1qownYBbct6sZkP3kACXeSDijg0Q1nxBo?usp=sharing)  
**Опубликована**: сентябрь 2023  
**Архитектура**: энкодер  
**Количество параметров**: 34.6М  
**На диске**: 139М  
**Длина контекста**: 16384 токенов  
**Применение**: задачи классификации и сравнения длинных текстов - документов, статей и т.д.  

---

### ruRoBERTa-large

**Описание**:  
**Ссылки**: [Хабр](https://habr.com/ru/companies/sberbank/articles/567776/)  
**Опубликована**:  
**Архитектура**:  
**Количество параметров**:  
**На диске**:  
**Длина контекста**:  
**Применение**:  

---

### ruT5

**Описание**:  
**Ссылки**: [Хабр](https://habr.com/ru/companies/sberbank/articles/567776/)  
**Опубликована**:  
**Архитектура**:  
**Количество параметров**:  
**На диске**:  
**Длина контекста**:  
**Применение**:  

---

### Siberian FRED-T5

**Описание**:  
**Ссылки**:  
**Опубликована**:  
**Архитектура**:  
**Количество параметров**:  
**На диске**:  
**Длина контекста**:  
**Применение**:  
