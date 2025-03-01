# 🎯 Wildberries Data Analysis

## 📊 1. Ключевые метрики для анализа:
На основе данных из Wildberries JSON можно выделить следующие метрики:

### Продажи и популярность товара:
- Количество отзывов (`feedbacks`).
- Рейтинг товара (`rating`).
- Количество доступных цветов (`colors`).
- Оценка рекламных показов (`cpm`, `promoPosition`, `promotion`).

### Конверсия:
- Количество просмотров (`viewFlags`).
- Количество покупок товара(предположим, что оно равно `feedbacks` - количеству отзывов).
- **Формула:** Конверсия = (Количество покупок / Количество просмотров) * 100%.

### Рекламная активность:
- Позиция товара в выдаче (`position`).
- Промо-позиция (`promoPosition`).
- Наличие промо-текста (`promoTextCard`).
- Рекламные расходы (`cpm`).

### Складские данные:
- Объем товара на складе (`totalQuantity`).

---
## 💡 2. Основные мысли(гипотезы) о конверсии товаров на маркетплейсе: 
- Товары, продвигаемые на верхние ряды каталога, имеют наибольшую конверсию в покупку. То есть ранжирование играет ключевую роль в увеличении конверсии товаров.
- У товаров, продвигаемых с помощью рекламы, конверсия в покупку увеличивается.
- Для конверсии в покупку новых товаров существует проблема холодного старта товара, то есть то какое место в рекомендательной системе займет товар. К примеру, при добавлении нового товара, мы имеем низкие или нулевые показатели по рейтингу данного товара, количеству отзывов, количеству просмотров и тд. Соответственно этот товар может вызывать недоверие среди покупателей, что вызовет низкий процент конверсии в покупку.
- На конверсию в покупку влияет наличие отзывов и рейтинга товаров, а именно:
  * большой рейтинг и большое количество отзывов повышает конверсию товара
  * большой рейтинг, но малое количество отзывов неоднозначно повышает конверсию товара. Так как затрагивает малую выборку отзывов покупателей
  * малый рейтинг и малое количество отзывов уменьшает конверсию товара
- Товары, имеющие большее количество цветов и большую размерную сетку, имеют высокую конверсию.

---

## 🛠️ 3. Использование инструментов визуализации:

### ClickHouse:  
- Загрузить данные по товарам и продажам из Wildberries в базу данных ClickHouse.  
- Использовать SQL-запросы для агрегации и фильтрации данных по ключевым метрикам.  

### Redash:  
- Подключиться к базе данных ClickHouse и построить графики:  
  - Конверсия просмотров в продажи.  
  - Динамика изменения рейтинга и отзывов.  
  - Позиции товаров в поисковой выдаче.  

### Superset:  
- Создать интерактивные дашборды для визуализации всех ключевых метрик.  
- Добавить фильтры для детального анализа товаров по категориям, брендам или рекламным кампаниям.  
