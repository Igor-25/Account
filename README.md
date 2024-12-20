REST WebAPI сервис для работы с учетными записями.

Особенности:
1.	При поиске, для удобства работы в Swagger, поля со значением "string" считаются пустыми (только при поиске). Как только поле меняем на другое, оно учитываться в поиске. Учитываются поля: фамилия, имя, отчество, телефон, электронная почта.
2.	При разных mail, mobile, web валидацию проходят только обязательные поля. Уникальность сохраняется в любом случае.
3.	Имя находиться в поле firstName.
4.	При web сценарии пустое поле почты то же уникально. При этом, так как поле почты не является обязательным, то оно не проходит валидацию, но при этом уникально даже если пустое. Т.е. почту в любом случае нужно вводить, так как если ее не ввести один раз, поле становиться пустым и будет уникально пустым (недоработка).
5.	Начало тестов AccountsRepositoryTests возвращает базу в исходное состояние.

Техническое задание: 
Разработать REST WebAPI сервис для работы с учетными записями. Методы сервиса должны выполнять следующий функционал:

1.	Создание пользователя
2.	Получение существующего пользователя по ID
3.	Поиск пользователя по нескольким полям Модель пользователя: Пользователь содержит следующие атрибуты: — ID — Фамилия — Имя — Отчество — Дата рождения — Номер паспорта — Телефон — Электронная почта — Адрес Требования к заданию:
4.	При создании пользователя поля должны пройти валидацию: — Номер паспорта должен иметь формат XXXX XXXXXX — Телефон должен иметь формат 7ХХХХХХХХХХ — Электронная почта должна иметь правильный формат
5.	Пользователь может быть создан из разных приложений. Тип приложения определяется по обязательному HTTP-заголовку X-Device. В зависимости от переданного заголовка меняется набор обязательных полей для создания пользователя:   — mail – обязательны только имя и электронная почта — mobile – обязательный только номер телефона — web – обязательно ввести все поля, но необязательно электронную почту и адрес.
6.	Электронная почта и телефон должны быть уникальными, создание пользователя с повторениями должно возвращать ошибку.
7.	Поля, по которым можно искать пользователя: фамилия, имя, отчество, телефон, электронная почта. Должен быть функционал поиска по одному, либо по нескольким полям из этого списка. Дополнительные требования:
8.	Основной стек для реализации: .NET 8, ASP.NET Core, EF Core, SQL Server
9.	Логика приложения должна быть покрыта Unit или интеграционными тестами. Использовать NUnit или XUnit.
10.	Должны присутствовать миграции БД, а также первоначальные данные для проверки работоспособности проекта.
11.	Проект должен запускаться сразу, без внесения каких-либо изменений в проект.
