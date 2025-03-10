# A/B-контест от Samokat.tech

Боремся с фродом на стороне продавцов маркетплейса

Одна из проблем при привлечении продавцов на площадку — это регистрация неблагонадежных продавцов-мошенников.  
  
Распространённая и самая известная на рынке схема мошенничества: мошенник берёт данные ИНН из открытых источников, регистрирует на него компанию на площадке маркетплейса. Далее выставляет ходовой товар на продажу, например iPhone 14, на 50% дешевле рынка. Когда покупатель оформляет заказ на маркетплейсе, продавец пишет покупателю, что у него есть другой сайт, где можно купить товар ещё дешевле. Покупатель соглашается и оплачивает заказ по ссылке продавца в обход площадки. После этого продавец пропадает. Покупатель остается без товара. Такие продавцы очень сильно портят репутацию маркетплейса, и необходимо их выявлять как можно быстрее, лучше всего в процессе регистрации.  
  
Для этого ML-команда предложила к использованию модель по автоопределению продавцов-мошенников, которую нам предлагается внедрить в процесс регистрации продавца.  
  
Мы хотим ввести новый функционал, но как data-driven компания не можем это сделать без тестирования и проверки качества новой функциональности через A/B-тест.

**Задание**

Ответьте, пожалуйста, на следующие вопросы:

Как определить, какой продавец мошенник, а какой — нет? Какие ещё могут быть схемы мошенничества?

Какие продуктовые фичи могут помочь нашим клиентам избежать неприятных ситуаций с мошенничеством?

Через какую механику мошенник узнает контакты покупателя? Что можем сделать, чтобы усложнить жизнь фродерам?

**Опишите методологию и дизайн теста. Почему сделали такой выбор?**

Определите основную метрику (дополнительные метрики) и принцип разделения на группы.

Рассчитайте, какой эффект можно статистически значимо отследить. Укажите его.


**Описание файла с данными**

registration_date - дата регистрации (дата получения мерчант айди, продавец зарегистрировался на площаке)

activation_date - дата активации (продавец прошел все этапы регистрации и может продавать)

merchant_id - айди продавца

ind_frod - индекс мошенника

type - форма организации бизнеса

---

**Стек:**
Python (pandas, numpy, seaborn, matplotlib, scipy.stats, requests, urllib.parse), A/B-тестирование

**Результаты:**

- Провел EDA, избавился от выбрасов и поработал с аномалиями в данных. Исследовал данные в разных разрезах (по мошенникам/немошенникам, по форме организации бизнеса), рассчитал конверсию в акктивацию продавцов, долю фродеров.
- Составил дизайн A/B-теста. В качестве основной метрики взял долю фродеров среди активных продавцов, контр-метрики - конверсию в активацию. Статистический тест: t-test Уэлча, определил MDE, рассчитал через моделированние необходимый объем выборки и период проведения теста.
- Провел A/A-тест, смоделировал 10000 выборок и убедился, что можно проводить эксперимент.
- Сделал выводы и дал рекомендации в качестве ответов на вопросы из ТЗ.
