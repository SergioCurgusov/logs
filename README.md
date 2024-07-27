Настраиваем центральный сервер для сбора логов
Цель:

Научится проектировать централизованный сбор логов;
Рассмотреть особенности разных платформ для сбора логов.

Что нужно сделать?

    в вагранте поднимаем 2 машины web и log
    на web поднимаем nginx
    на log настраиваем центральный лог сервер на любой системе на выбор

    journald;
    rsyslog;
    elk.

    настраиваем аудит, следящий за изменением конфигов нжинкса

    Все критичные логи с web должны собираться и локально и удаленно.

    Все логи с nginx должны уходить на удаленный сервер (локально только критичные).

    Логи аудита должны также уходить на удаленную систему.

    Формат сдачи ДЗ - vagrant + ansible

Решение:

Всё настроено. Пришлось немного изменить Vagrantfile (немного упростил). Автоматизация с помощью ansible.
Прилагаю Vagrantfile и playbook.yml


