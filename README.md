# conf-automation
SUAI conference automation scripts

# Скрипты для автоматизации процессов подготовки и проведения конференций в ГУАП, а также сбора статей по итогам конференций

Конференции, проводимые в ГУАП:
- Международная Студенческая Научная Конференция (МСНК), участники - студенты. См. например http://msnk.guap.ru
- Научная Сессия ГУАП, участники - аспиранты, преподаватели.

## МСНК

### Основные документы (72-я МСНК ГУАП, апрель 2019):
- Приказ о проведении: http://fs.guap.ru/docs/2018/pr_guap_2018-005-28_05-139-18.pdf
- Пример заполненной формы представления материалов для программы 72-й МСНК ГУАП: https://docs.google.com/document/d/12QSuZgxSY40YRi2Eu5I5scfobLDzEPoOitMiIH-bsqg/edit?usp=sharing
- Пример заполненного отчета конференции: https://docs.google.com/document/d/1Q7KXTWOZm_qa-4k3IHK5LIQNmQeOW1JXoN9BONUmAyo/edit?usp=sharing
- Пример списка представляемых к публикации докладов: https://docs.google.com/document/d/12QSuZgxSY40YRi2Eu5I5scfobLDzEPoOitMiIH-bsqg/edit?usp=sharing
- Внутренняя таблица для учета всех этапов организации конференции (доступ по запросу): https://docs.google.com/spreadsheets/d/1zkLdYvq8qjKB4pOM6h8OwDPHahfrH9n8_GOUtySW-p0/edit?usp=sharing

### Этапы проведения конференции
1. Подача заявок на участие (студенты ГУАП и др. ВУЗов)
2. Формирование программы конференции на основе поданных заявок
3. Проведение заседаний в рамках конференции, заслушивание докладов участников
4. Формирование отчета о проведенных заседаниях
5. Сбор статей (письменных версий докладов) для публикации в сборнике по итогам конференции
6. Формирование перечня представляемых к публикации докладов  

### Вспомогательные документы
 - Гугл-форма (анкета) "Заявка на участие", все поля кроме телефона обязательны для заполнения: 
    1. e-mail участника 
    2. ФИО докладчика (отдельно фамилия, имя и отчетсво при наличии)
    3. Название доклада
    4. ФИО руководителя (фамилия и инициалы)
    5. Организация, направляющая участника на конференцию (по умолчанию ГУАП, но можно вписать другой ВУЗ)
    6. Номер группы (только для студентов ГУАП)
    7. Контактный телефон
 - Гугл-форма (анкета) для подачи статьи для публикации
    1. email автора (должна проводиться верификация электронного адреса)
    2. ФИО основного автора (отдельно фамилия, имя и отчетсво при его наличии)
    3. ФИО соавторов, при наличии (полностью фамилия, имя, отчество; если соавторов несколько - через запятую; напр.: "Иванов Иван Иванович, Сидоров Сидр Сидорович")
    4. Название статьи 
    5. Файл с текстом статьи
    6. Контактный телефон
 - Внутренняя таблица для учета всех этапов организации конференции (см. пример по ссылке выше):
    1. Фамилия студента
    2. Имя студента
    3. Отчество студента
    4. Группа (для студентов ГУАП) или название ВУЗа (для студентов не из ГУАП)
    5. Тема доклада (из заявки на участие)
    6. e-mail
    7. телефон
    8. ФИО руководителя
    9. Дата выступления с докладом
    10. Рекомендация к опубликованию по итогам заслушивания доклада (логическое значение 1 или 0)
    11. Наличие распечатки статьи, поданной для публикации, с подписью руководителя (логическое значение 1 или 0)
    12. Наличие электронной версии статьи, поданной для публикации
    13. Название статьи, поданной для публикации (может отличаться от темы доклада)
    14. Соавторы (полное ФИО каждого соавтора, если соавторов несколько - через запятую)
    15. Дата заполнения гугл-формы "Заявка на участие" (в примере отсутствует)
    16. Дата заполнения гугл-формы для подачи статьи для публикации (в примере отсутствует)
  
### Рабочий процесс
1. Студент заполняет гугл-форму "Заявка на участие"
2. С помощью Google Script введенные студентом данные записываются во внутреннюю таблицу
    - если студент с таким ФИО и номером группы (или ВУЗом для студентов не из ГУАПа) во внутренней таблице уже есть, то информация об этом студенте перезаписывается (обновляется)
    - если студента с таким ФИО и номером группы (или ВУЗом для студентов не из ГУАПа) во внутренней таблице нет, то информация из гугл-формы заносится в конец таблицы
    - данные записываются в таблицу автоматически, т.е. скрипт вызывается по нажатию на кнопку "Отправить" в гугл-форме
    - дата и время заполнения гугл-формы сохраняются в соответствующем поле во внутренней таблице
3. При необходимости во внутреннюю таблицу вручную добавляются данные (записи) о студентах, желающих принять участие в конференции
4. По завершении приема заявок от студентов с помощью Google Script (или Python + Google Sheets API) формируется документ - программа конференции, см. пример формы представления материалов для программы кофнеренции выше
    - скрипт запускается вручную в нужный момент времени, но неплохо было бы предусмотреть интерфейс для запуска скрипта "в один клик" (например, отдельная гугл-форма, при оправке которой будет запускаться скрипт для генерации программы конференции)
5. На кафедре проводятся заседания, заслушиваются доклады и во внутренней таблице вручную заполняются столбцы "Дата выступления с докладом" и "Рекомендация к опубликованию"
6. С помощью Google Script (или Python + Google Sheets API) формируется документ - отчет о проведенных заседаниях в рамках конференции, см. пример отчета о проведенных заседаниях выше
    - в отчет попадают все студенты из внутренней таблицы, для которых заполнено поле "Дата выступления с докладом"
    - если в поле "Рекомендация к опубликованию" во внутренней таблице стоит 1 или "Да" (логическое `true`), то в отчете для этого студента указывается соответствующий текст о рекомендации к опубликованию; если в этом поле пусто или стоит любое другое значение, кроме 1 и "Да", то в отчете для этого студента указывается текст о том, что доклад плохо подготовлен (см. пример)
    - скрипт запускается вручную в нужный момент времени, но неплохо было бы предусмотреть интерфейс для запуска скрипта "в один клик" (например, добавить в гугл-форму для запуска скрипта-генератора программы конференции выбор, какой именно скрипт запустить - генератор программы или генератор отчета)
7. Студенты заполняют гугл-форму для подачи статьи для публикации
8. С помощью Google Script введенные студентом данные записываются во внутреннюю таблицу
    - если студент с таким ФИО и номером группы (или ВУЗом для студентов не из ГУАПа) во внутренней таблице уже есть, то информация об этом студенте перезаписывается (обновляется)
    - если студента с таким ФИО и номером группы (или ВУЗом для студентов не из ГУАПа) во внутренней таблице нет, то информация из гугл-формы заносится в конец таблицы
    - тема статьи может не совпадать с темой доклада, поэтому тема статьи заносится в отдельное поле в таблице
    - в поле "Наличие электронной версии статьи" проставляется значение 1 (число, не строка)
    - данные записываются в таблицу автоматически, т.е. скрипт вызывается по нажатию на кнопку "Отправить" в гугл-форме
    - дата и время заполнения гугл-формы сохраняются в соответствующем поле во внутренней таблице
9. С помощью Google Script (или Python + Google Sheets API) формируется документ - список представляемых к публикации статей, см. пример списка представляемых к публикации докладов выше
    - в список попадают все студенты из внутренней таблицы, для которых оба поля "Наличие электронной версии статьи" и "Наличие распечатки статьи" содержат логическое значение `true` (может обозначаться числом 1 или строкой "Да" в ячейке таблицы)
    - если хотя бы в одном из полей "Наличие электронной версии статьи" или "Наличие распечатки статьи" нет логического значения `true`, то этот студент и его работа в список представляемых к публикации докладов не вносится
    - скрипт запускается вручную в нужный момент времени, но неплохо было бы предусмотреть интерфейс для запуска скрипта "в один клик" (например, добавить в гугл-форму для запуска скрипта-генератора программы конференции выбор, какой именно скрипт запустить - генератор программы конференции, генератор отчета или генератор списка представляемых к публикации статей)

### TODO
- [ ] 1. Изучить существующие бесплатные решения для организации конференций, составить перечень достоинств и недостатков для каждого
- [ ] 2. Изучить существующие бесплатные решения для сбора (подачи) статей для публикации, составить перечень достоинств и недостатков для каждого
- [ ] 3. Написать скрипт на Google Script для внесения данных во внутреннюю гугл-таблицу при заполнении формы "Заявка на участие" (пункт 2 в рабочем процессе)
- [ ] 4. Написать скрипт на Google Script для формирования программы конференции в виде документа в Google Docs (пункт 4 в рабочем процессе)
- [ ] 5. Написать скрипт на Python 3.6 (или выше) с использованием Google Sheets API для формирования программы конференции в виде документа MS Word (файл в формате docx) (пункт 4 в рабочем процессе)
      - Учесть ограничение бесплатной версии Google Sheets API на количество запросов в единицу времени, сделав в скрипте соответствующие задержки
      - Скрипт запускается вручную из командной строки
- [ ] 6. Написать скрипт на Google Script для формирования отчета о заседаниях в виде документа в Google Docs (пункт 6 в рабочем процессе)
- [ ] 7. Написать скрипт на Python 3.6 (или выше) с использованием Google Sheets API для формирования отчета о заседаниях в виде документа MS Word (файл в формате docx) (пункт 6 в рабочем процессе)
      - Учесть ограничение бесплатной версии Google Sheets API на количество запросов в единицу времени, сделав в скрипте соответствующие задержки
      - Скрипт запускается вручную из командной строки
- [ ] 8. Написать скрипт на Google Script для внесения данных во внутреннюю гугл-таблицу при заполнении формы для подачи статьи для публикации (пункт 8 в рабочем процессе)
- [ ] 9. Написать скрипт на Google Script для формирования списка представляемых к публикации докладов (статей) в виде документа в Google Docs (пункт 9 в рабочем процессе)
- [ ] 10. Написать скрипт на Python 3.6 (или выше) с использованием Google Sheets API для формирования списка представляемых к публикации докладов в виде документа MS Word (файл в формате docx) (пункт 9 в рабочем процессе)
      - Учесть ограничение бесплатной версии Google Sheets API на количество запросов в единицу времени, сделав в скрипте соответствующие задержки
      - Скрипт запускается вручную из командной строки

<!-- 
Студенческая конференция:
1. Подготовка программы: анкета для сбора данных в гугл-таблицу
2. Формирование официальной заявки в программу конференции в соответствии с приказом
3. Формирование внутренней таблицы для учета участников (может отличаться от официальной программы)
4. Обновление внутренней таблицы учета по итогам заседаний (вручную)
5. Формирование официальной выписки по итогам заседаний в соответствии с приказом
6. Подготовка публикаций: анкета для сбора данных в гугл-таблицу
6.1. Как быть с соавторами?
6.2. Возможно, для загрузки текста стоит использовать другой интерфейс (электронная почта, специальный сервис в интернете и т.п.)?* 
7. Формирование перечня поданных на публикацию докладов в соответствии с приказом
-->

## Научная сессия ГУАП



## Полезные материалы
- Как запустить скрипт для добавления данных в гугл-таблицу из гугл-формы: https://stackoverflow.com/questions/46902126/triggering-script-in-google-sheets-after-forms-submit
- 
