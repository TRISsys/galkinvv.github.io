###NVIDIA
#### Maxwell (750, 945-980), GM???
##### Msi 750 2GB (чёрный)
Сопротивление менее 0.1 Ом как по линии питания памяти, так и по линии питания процессора. Снят GPU. На плате КЗ исчезло. Проверено что на снятом GPU КЗ по линии питания памяти.

#### Fermi (6??, 650-730, 7??), GK???
##### Evga 680 2GB GDDR5 (чёрный)
Пришла с прогаром транзистора по питанию памяти и ШИМом памяти с дыркой. После удаления транзистора, дросселей и конденсатора осталось 2Ом на входе по 12в (греется один из конденсаторв в районе С559) м 0.1Ом на питании паямти. Поиск места КЗ указал на район C672, хотя он сам не виноват. Основное подозрение на чип паямти на обратной стороне от него.

##### Msi 680 2GB GDDR5 (чёрный)
После старта все напряжения есть, но даже при наличии интегрированного видео - 1 длинных 2 коротких. После этого иногда определялась в nvflash. BIOS был нулевого размера. Перепршит BIOS. После этого не пищит, как будто стартует. После запуска Xorg даже показывает изображение, но с уклоном в синий (нет красного). Бублик работал, но периодически вырубалась (изображение пропадает, вентиляторы крутятся быстрее). Иногда система не стартует, особенно если подключен монитор. при подключении  к другому монитору по dvi синевы нет, а вырубания просиходят в случайном месте, независимо от нагрузки. после вырубания напряжения нет ни на памяти, ни на gpu. БП не просаживается.
Возле линии Analog red обнаружен повреждённый белый элемент, половина которого марирована чёрным.
Имеет скол и в отличие от соседних не нулевое, а бесконченое сопротивление.
обнаружен и заменен расколотый резистор на линии детектирования присутствия доп питания. теперь стартует с подключеным монитором, тесты пройдены, работает.

##### Palit GTX650 1024M GDDR5 (тёмно-коричневый)
Замыкание по линии 12v с разъёма pcie, сопротивления порядка 0.1Ом. В питании GPU напряжение с pcie не используется, используется только для питания памяти. Более чем 2-лапых элементов немного, все не вызвали подозрений. Наибольшие подозрения вызвал бОльший конденсатор непосредственно в районе прихода 12v с платы. был обнаружен пробитый конденсатор на линии 12v c pcie (рядо с pcie), заменен на больший. отремонтировано.

##### ASUS GTX650Ti 1GBDDR5 (чёрный)
Артефакты в 3d (unexpected spikes). Дебаггинг показал что по всей видимости некорректно работают шейдеры на последнем по индексу ядре из 4х.

#### Fermi (420 - 625, 6??), GF???
##### Gainward 570 1280 GDDR5 (чёрный)
В текстовом режиме некоторые символы мусорные. При загрузке драйвера сыпет ошибки и падает драйвер.

##### Zotac GTX560 (чёрный)
Работает, но сильно греется даже при хорошем теплоотводе. Вероятно надо скальпировать. Скальпировано, собрано без крышки; теперь температура не превышает 75 (при запуске без корпуса). Работает. скальпирована удачно, собрана без крышки и продана.

##### Gainward GTX465 (коричневый)
Работает, но в редких случаях не инициализируется. на плате множество снятых конденсаторов, но работает 

##### Palit GTX550Ti 1GB GDDR5 (коричневый)
Вначале были артефакты шрифтов в текстовом режиме. Но потом вообще перестала определяться: при старте запускается с интегрированным видео, хотя все напряжения есть

##### Palit GTX 560Ti 2GB GDDR5 (красный)
При загрузке драйвера сыпет ошибки и тормозит драйвер, который с другой картой работает нормально. По словам продавца - проблемы под нагрузкой. Плата пратически идентична Palit GTX460 Sonic

##### Zotac GTX465 1GB GDDR5 (чёрный)
Получена из сервиса, где была донором. Есть пайка и снятые элементы, по крайней мере 3. КЗ по дополнительному питания 12v в одном из разъёмов. КЗ вызвано прогаром дорожек под транзистором. После устранения транзистора вместе со всеми дрожками под ним - осталось 3 фазы мз 4х, КЗ нет, но и старта gpu нет. Сопротивление на gpu 0.3Ом, работоспособность gpu не ясна.

##### Gainward GTX460 (красная)
Обуглились элементы с нулевым сопротивлением и обозначением SLB (видимо примерно в роли предохранителеей). Обнаружено КЗ всех лапок транзисторов соответстующей фазы. перепаяна соотвествующая фаза с заменой подозрительных элементов. починено.

##### Palit GTX460 Sonic (красная)
До выпаяивания ШИМ. Разные симпотомы сменяли друг друга:
 * питание gpu было несколько минут, потом исчезало. gpu был горячий. Все фазы работали нормально.
 * не было питания на gpu

До выпаивания gpu:
 * замкнуто 3.3v видеоплаты, напрямую приходящие с PCIe, на одну ногу кварца, очень странно
 * странный шум по вольтажу на 2-х управляющих ногах ШИМа. Ичтоник шума - дорожка идущая по верхней стороне платы и уходящая в плату
Кварц рабочий, но не активировался. Проверялось при выпаянном ШИМ.

Выпаян gpu.
Замыкание на плате на кварц исчезло. На gpu найдены контакты, сопротивлени которых до ножки кварца ~4Ом.

На карте жжёные дорожки под чипом, gpu потенциально рабочий

#### Tesla (9300 - 405) G9?, GT???
##### XFX GTX280 1GB GDDR3 (чёрный)
Был красный светодиод, до выпаивания транзистора Q502, который по идее отвечает за детектирование наличия дополнительно питания. После этого светодиод стал зелёный, но не определялась: система загружается со встроенным видео. Но 1 раз за пустилсь и через пару секунд монитор погас. При измерении есть питание на GPU, видеопамяти и 5v DVI. Быстро становится тёплая в зоне основных транзисторов питания.

##### Leadtek GTS260 896MB GDDR3 (чёрный)
Дорожки такия же как на 280. Продавалась как в неизветсном состоянии. При длительном миспользовании проблем не выявлно кроме возможно редких зависаний, возможно не от неё. Работает.

##### Asus GTS250 1GB GDDR3 (cиний)
При старте на памяти нет питания. Нет контакта на предохранителе на 8А рядом с разъёмом дополнительного питания. При замыкании предохранителя есть старт, идёт ток порядка 1А. Предположительно это была единственная проьлема. Дополнительное питание используется только для памяти. Подозрительно низкое сопортивление до земли с ключа транзистора - плеча, отвечающего за соединение с землёй. Но может с ним и всё впорядке, т.к. непосредственно рядом с ШИМ памяти UP6101BU8 находится резистора между LGATE и GND. предохрантель заменен на ВП1 с аналогичными параметрами. починено. Тест на MSI 9642 был нестабилен, предположительно из-за нехватки питания с разъёма то мат. платы. На нормальной плате с тем же БП проблем нет - работает стабильно. продана

##### Asus GTS250 1GB GDDR3 (cиний)
карта от студента миэта. который снял с нее множество элементов, втч шим, твердотельные конденсаторы, транзисторы. все поставлено назад, кроме пробитых транзисторов. Отсутствует шим памяти, включение без него привело к предположительному выходу из строя двух транзисторов рядом.на шим памяти есть донор.

##### Asus GTS250 512MB GDDR3 (cиний)
Получена из сервиса. КЗ по питанию после дросселей, причём как по питанию GPU, так и по питанию памяти. Большие чёрные элементы eS8, на обратной стороне gpu - конденсаторы, не выпаивались. Исследование падение напряжений при токе порядка 1А, поданного на замкнутые элементы указывает на то что область замыкания близка к конденсаторам на обратной стороне gpu. Причём касается это как линии питани gpu (проверилось на самых больших конденсаторах под gpu) так и линии питания памяти (проверилось на вторых по размеру конденсаторах под gpu). НА обратной стороне чипа 1 сбитый элемент. Ясно, что это не причина КЗ, но надо иметь ввиду. Основная гипотеза - КЗ под gpu.

##### Zotac GTS250 512MB GDDR3 (синий)
На второй-третий раз исследований внезапно вырубился БП по защите. Что до этого - неизвестно.
При последующих включениях бывал сильный запах. Иcтоник не был найден, было найдено просаживание по 3.3v pcie.
Выпаяна линейная система питания, потенциально проблемные конденсаторы. КЗ по питанию после линейной системы - осталось.

Сопротивление ооочень маленькое, при подаче 2 ампер ничего не греется. Замеры падений напряжений по дорожкам указывают на дырку в плате с оратной стороны gpu, предположительно кз в шарах или подложке. Есть сколы, но небольшие. Ранее в районе gpu в термопасте была найдена мелкая странная крошка металла (или кремния).

##### PNY 9800 512MB GDDR3 (зелёный)
Редко были замечены трудноразличимые артефакты в виде точек. Долго работала и продолжает работать. Из тестов артефакты можно увидеть только в LightMark. продана

### AMD/ATI
#### Radeon HD 6xxx Series
##### MSI R6850 1GDDR5(коричневая)
Получена с описанием "не работет поле того как подключили монитор на горячую". Стартует, показывает по VGA, но не определяет edid монитора. Проблема оказалась в драйвере fglrx. C radeon разрешение по VGA подхватывется. Так что карта полностью работает, никаких проблем нет.

##### XFX HD6770 1GDDR5(чёрная)
Карта стартует нестабильно, обычно вырубается (исчезает напряжение на gpu и памяти) почти сразу после старта.  При запуске с закороченным BIOS на gpu стабильно 1.25v и можно прошить по сети. При запуске с незакороченным BIOS напряжение растёт до 1.3 (в это время карта работает) а потом падает в ноль. Перепрошивка BIOS на меньшее напряжение не дала результата

##### MSI AMD HD6870 1GDDR5(коричневая)
При попытке использовать ATI-драйвера - виснет через разное небольшое время. Обнаружен отвал конденсатора C304 рядом с микросхемой линейного стабилизатора uP7701u8, расположенного между VOUT и FB ногами. Замеры ёмкости - 0.6nF при 0.560 между щупами. 3d иногда запускается, но через некоторое время карта останавливается, исччезает напряжение на gpu, из-за того что перестаёт подаваться сигнал enable на основной ШИМ. Дальнейшие измерения показали что его исчезновение по всей видимости вызвано открытием транзистора Q210. Внезапно проблема перестала проявляться, карта работает, вероятно проблема в какой-то защитной схеме, которая выключает сигнал Enable. Тестирует Женя.

#### Radeon R600 (HD 2xxx, HD 3xxx) Seriesse
##### HIS HD 3450 (синяя, мелкая)
Всегда работала и работает
