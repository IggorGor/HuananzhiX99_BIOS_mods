#### Рекомендуется прошивать биос с помощью S3TurboTool
*(за данную утилиту и новый драйвер анлока особая благодарность ser8989)*

#### Инструкция по разблокировке макс.частоты на все ядра, а не на два (в народе более известно как "анлок")
Не стоит бояться того, что тут много текста. На самом деле всё несложно, я лишь попытался ничего не упустить и быть с вами шаг за шагом.

За основу берём биос с открытым меню "CPU C State Control", например любой из "...phants_vxxx".
1. Запускаем S3TurboTool
2. Нажимаем MMTool5
3. В появившейся утилите "MMTool Aptio" нажимаем "Load Image" и выбираем необходимый биос
4. Переходим на вкладку "CPU Patch", выделяем микрокод "6F 06F2", отмечаем "Delete a Patch Data", нажимаем Apply и соглашаемся
5. Нажимаем "Save Image" и закрываем "MMTool Aptio"
6. В S3TurboTool нажимаем AMIBCP5
7. В появившейся утилите AMIBCP открываем биос
8. Раскрываем список и идём по пути "Common RefCode Configuration > IntelRCSetup > Advanced Power Management Configuration > CPU C State Control"
9. Справа, в столбце Optimal, двойным кликом меняем значение параметров:
    * "Package C State limit" на "C2 state"
    * "CPU C3 report" на "Enable"
    * "CPU C6 report" на "Disable"
10. Закрываем окно AMIBCP и соглашаемся на сохранение внесённых изменений
11. В S3TurboTool нажимаем "Собрать драйвер"
12. Настраиваем необходимые значения отрицательных смещений напряжения. Также выбираем, нужен ли дополнительный сигнал при включении и выводе системы из сна. Нажимаем "Собрать драйвер".
13. В S3TurboTool нажимаем UEFITool
14. В появившейся утилите UEFITool открываем биос
15. Раскрываем список и идём по пути "Intel image > BIOS region > 8C8CE578-...(самый нижний) >"
16. Примерно среди первых 20 значений находим 271DD6F2-...
17. Правый клик по нему, выбираем "Replace as is...", выбираем собранный ранее драйвер (находится в папке S3TurboHack)
18. Выбираем "File > Save image file...", сохраняем
#### На этом биос готов к прошивке

При возникновении трудностей, а также если у Вас есть замечания и пожелания, обращайтесь в Telegram-группу https://t.me/chinese_lga2011_3_x99
Также можете посмотреть видео-инструкцию https://youtu.be/2hfhdrIrXR4
[![Тут текст](https://i.ytimg.com/an_webp/2hfhdrIrXR4/mqdefault_6s.webp?du=3000&sqp=CJ66hf0F&rs=AOn4CLAJOuGec3cIeCnwFcBaDVoE-s15yw)](https://youtu.be/2hfhdrIrXR4)

#### Часто задаваемые вопросы:
(Вопрос:) Я привык использовать v3_payne_xx_xx.ffs или V3_MOF_xxxxxx.ffs, вшил по инструкции и получил кирпич. Почему?

(Ответ:) Потому что эти типы драйверов устанавливаются в другую секцию биоса. Рекомендуется собирать свой драйвер через S3TurboTool.

(Вопрос:) В чём преимущество нового драйвера от S3TurboTool?

(Ответ:) Была решена проблема, при которой анлок сбрасывался при выводе системы из режима сна. Также было уменьшено энергопотребление процессора без нагрузки.

(Вопрос:) Кот, расскажи, какие ещё есть возможности у нового драйвера от S3TurboTool?

(Ответ:) Можно снизить напряжение на процессоре без использования анлока, для этого не выполняем шаги 2-10 инструкции и на 12 шаге снимаем галку "Разблокировка турбо".
