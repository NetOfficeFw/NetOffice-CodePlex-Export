**Почему NetOffice?** [english](Documentation) | [deutsch](Documentation_German)

Обычно для доступа к Microsoft Office в .NET используются основные сборки взаимодействия (PIA) и VSTO. Оба метода имеют недостатки.

* Привязка к одной или определённым версиям Office
* При переносе или установке на другой компьютер могут возникнуть проблемы
* Не предоставляются защитные механизмы управления заместителями объектов COM

NetOffice устраняет эти недостатки и является средством, синтаксически и семантически идентичным сборкам взаимодействия.
{anchor:how}
##### Как работает NetOffice?
NetOffice использует лишь "позднее связывание" COM Interop, но с удобством и простотой "раннего связывания". Изящная архитектура и эффективный дизайн лишь незначительно замедляют работу по сравнению с "ранним связыванием" (не более, чем на 10%). События в NetOffice реализованы посредством техники, которую автор называет "динамическое раннее связывание". 
{anchor:assemblies}
##### NetOffice содержит 16 сборок. Какие из них нужны для конкретного приложения Office?
Все приложения Office используют типы, которые определены в библиотеках компонентов/типов. Библиотеки типов предсталены отдельной сборкой. Каждая сборка зависит от сборки NetOffice.dll. 

+Таблица развёртывания+

|| Приложение Office || Зависимости ||
| ExcelApi.dll | |
| | OfficeApi.dll |
| | VBIDEApi.dll |
| | NetOffice.dll |
| WordApi.dll | |
| | OfficeApi.dll |
| | VBIDEApi.dll |
| | NetOffice.dll |
| OutlookApi.dll | |
| | OfficeApi.dll |
| | NetOffice.dll |
| PowerPointApi.dll | |
| | OfficeApi.dll |
| | VBIDEApi.dll |
| | NetOffice.dll |
| AccessApi.dll | |
| | OfficeApi.dll |
| | DAOApi.dll |
| | VBIDEApi.dll |
| | ADODBApi.dll |
| | OWC10Api.dll |
| | MSDATASRCApi.dll |
| | MSComctlLibApi.dll |
| | NetOffice.dll |
| MSProjectApi.dll | |
| | OfficeApi.dll |
| | MSHTMLApi.dll |
| | NetOffice.dll |
| VisioApi.dll | |
| | NetOffice.dll |
{anchor:deploy}
##### Что нужно для распространения программы на базе NetOffice?
Только скопировать сборки на целевой комьпютер. Регистрация требуется лишь для дополнений COM. Управляемые дополнения COM обычно регистрируются посредством утилиты RegAsm.exe или Windows Installer.
{anchor:addins}
##### Зависят ли дополнения COM от версии Office? 
Нет, и в этом достоинство NetOffice. Доступны примеры для дополнений всех приложений Office. Для поддержки 32- и 64-разрядных приложений понадобятся 2 версии дополнений соответственно.