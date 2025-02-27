Описание проекта
  Интернет-магазин «В один клик» продаёт разные товары: для детей, для дома, мелкую бытовую технику, косметику и даже продукты. Отчёт магазина за прошлый период показал, что активность покупателей начала снижаться. Привлекать новых клиентов уже не так эффективно: о магазине и так знает большая часть целевой аудитории. Возможный выход — удерживать активность постоянных клиентов. Сделать это можно с помощью персонализированных предложений.

«В один клик» — современная компания, поэтому её руководство не хочет принимать решения просто так — только на основе анализа данных и бизнес-моделирования. У компании есть небольшой отдел цифровых технологий, и вам предстоит побыть в роли стажёра в этом отделе.

  Требуется разработать решение, которое позволит персонализировать предложения постоянным клиентам, чтобы увеличить их покупательскую активность.


В ходе работы был получен следующий вывод:

  Интернет-магазин «В один клик» продаёт разные товары: для детей, для дома, мелкую бытовую технику, косметику и даже продукты. Отчёт магазина за прошлый период показал, что активность покупателей начала снижаться. Возможный выход — удерживать активность постоянных клиентов. Сделать это можно с помощью персонализированных предложений. Было поручено разработать решение, которое позволит персонализировать предложения постоянным клиентам, чтобы увеличить их покупательскую активность.

  В ходе работы были проанализированы данные, предоставленные магазином - проведена предобработка, исправлены недочеты в названиях столбцов, изучены данные, приняты необходимые решения в отношении типов данных - типы данных приведены к нужному виду. Стоит отметить, что данные и изначально были довольно приятными в работе, особенно порадовала возможность пользоваться приличной кириллицей и не держать в голове абстрактные названия столбцов.

  В ходе исследовательского анализа данных графическим путем было дентальнее изучено содержание каждого столбца предоставленных датафреймов, выловлены оставшиеся ошибки и аномалии, некоторые данные были позже переведены из численного в категориальный вид для удобства работы.

  В ходе корелляционного анализа была построена Phik матрица корреляций для всех числовых и категориальных столбцов датафрейма market_total, благодаря которой было установлено, что наиболее коррелирующими признаками с покупательской активностью являются (по убыванию ст. корреляции):

0,75 - 'страниц_за_визит',
0,69 - 'минут_предыдущий_месяц',
0,58 - 'минут_текущий_месяц',
0,54 - 'средний_просмотр_категорий_за_визит',
0,54 - 'маркет_актив_6_мес',
0,51 - 'неоплаченные_продукты_штук_квартал',
0,51 - 'акционные_покупки',
0,50 - 'выручка_препредыдущий_месяц'
  Далее с помощью пайплайнов лучшие результаты показала модель LogisticRegression(C=1, penalty='l1', random_state=42, solver='liblinear'))] с хорошими метриками ROC-AUC и F1 - их значения превышают 0.9, что в целом является хорошим результатом. Дальнейший анализ важности признаков показал, что одними из самых важных критериев оказались акционные покупки, мелкая бытовая техника и электроника, минуты в предыдущем месяце и число страниц посещенных за визит.

  После был найден особый сегмент пользователей, скорее всего снизящий свою активность - черри-пикеры, или по нашему просто скидочники. Данная категория пользователей была изучена отдельно и установлены некоторые ее особенности - так, данные пользователи смотрят меньше страниц (4 против 8 у среднестатистического юзера), держат в корзинах заметно больше товаров в надежде на сочную скидку, смотрят меньше категорий товаров, НО - чаще покупают премиум аккаунт. Организации стоит задуматься над взаимодействием с данным пластом пользователей - организовывать стимулирующие акции, фейковые скидки, программы лояльности - дать людям ощущение квеста и выгоды.

  По полученным данным составим портрет скидочника:

Скидочник смотрит меньше категорий за заход на сайт (2 против 3 у среднего пользователя)
Скидочник смотрит меньше страниц за визит (4 против 8.1 у среднего пользователя)
Скидочник чаще держит покупки в корзине неоплаченными (4.3 против 2.8 у среднего пользователя)
Скидочник имеет повышенный интерес к детским товарам и пониженный к мелкой электронике (Здесь стоит уточнить, что детские товары в целом самые популярные, но у скидочника отрыв от следующей категории двухкратный)
Предложение - на основании товаров, которые лежат в корзине, а я уверен, что магазин может такое отследить, раз знает их число, предлагать на странице как можно больше товаров по скидке, которые могут заинтересовать пользователя. Скорее всего это будут всякие детские товары и домашний текстиль, но подстройка под конкретную корзину всегда приятнее.

  При этом важно, чтобы все было на одной странице, т.к. как становится понятно из 'портрета' выше, много вкладок и категорий он посещать не будет. Также важно, чтобы товары были наиболее интересной категории, т.к. скидочники в среднем посещают не более 2 категорий за раз.
