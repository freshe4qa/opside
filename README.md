# Opside Testnet

Official documentation:
>- [Validator setup instructions](https://docs.opside.network)

Explorer:
>- [https://pre-alpha.opside.info](https://pre-alpha.opside.info)

### Minimum Hardware Requirements
 - 4+ CPUs;
 - 16GB+ RAM
 - 500GB of storage (SSD or NVME)

## Форма для доступа к тестнету
```
https://docs.google.com/forms/d/e/1FAIpQLSdMNJQjHHgCJdgTBeHAR9GrcFvMg16r660-O0go25RskBgSLg/viewform
```

## Проверка на доступ к тестнету

Для того, чтобы убедиться что вы были отобраны в тестнет вам нужно перейти в дискорд проекта в ветку for-validators и в формате:
```
@Opside Faucet <ВАШ EVM АДРЕС, КОТОРЫЙ ВЫ ПИСАЛИ В ФОРМУ>
```
Пример:

```
@Opside Faucet 0x23252ferg...
```

Если вы прошли - то ответ бота будет в таком виде:

![image](https://github.com/freshe4qa/opside/assets/85982863/b5871c11-848b-42a7-9eda-15c50ee1ec3e)

Если нет:

![image](https://github.com/freshe4qa/opside/assets/85982863/3af1f4a2-181a-434f-92a4-8c1af7564967)

### Подготовка сервера
Добавляем новый профиль для ноды
```
adduser opside

#ИНФОРМАЦИЮ О ПРОФИЛЕ ЗАПОЛНЯТЬ НЕ НУЖНО, ОТСАВЛЯЕМ ВСЕ ПОЛЯ ПУСТЫМИ
#ДОБАВЛЯЕМ ПРАВА ПРОФИЛЮ

usermod -aG sudo opside

#ПЕРЕХОДИМ В ПРОФИЛЬ НОДЫ

sudo su - opside
```

Скачиваем нужные файлы для запуска ноды
```
wget -c https://pre-alpha-download.opside.network/testnet-auto-install-v2.tar.gz 
tar -C ./ -xzf testnet-auto-install-v2.tar.gz
chmod +x -R ./testnet-auto-install-v2
cd ./testnet-auto-install-v2
```

Устанавливаем клиент валидатора
```
./install-ubuntu-en-1.0.sh
```

Во время установки клиента вас попросят ввести адрес для получения вознаграждения валидатора и пароль (Адрес - пароль - Снова тот же адрес - Снова тот же пароль). Вы можете указывать любой адрес из вашего Metamask.
Далее у вас появится окно с мнемонической фразой ключа вашего валидатора, обязательно запишите ее.
После этого вам потребуется ввести мнемоническую фразу которую вы получили в диалоговое окно клиента, и в итоге вы увидите окно об успешном создании ключей валидатора.

![image](https://github.com/freshe4qa/opside/assets/85982863/3d30453d-c40a-47bc-8826-8694dd54187d)

Нажимаем любую клавишу и ваша нода запустится

![image](https://github.com/freshe4qa/opside/assets/85982863/e174e48a-70fc-4863-bdad-88deaac9ae8e)

Установка ноды закончена.
Дальнейшие действия по депозиту монет в вашего валидатора нужно выполнять только после полной синхронизации ноды.
Проверить логи вашей ноды можно при помощи команд:

```
# Логи клиента
opside-chain/show-geth-log.sh

# Логи консенсуса
opside-chain/show-beaconChain-log.sh

# Логи валидатора
opside-chain/show-validator-log.sh
```

Проверить высоту синхронизации можно с помощью команды:
```
opside-chain/show-geth-log.sh
```

Высота синхронизации вашей ноды будет показана в формате:

![image](https://github.com/freshe4qa/opside/assets/85982863/4c02eafc-4335-476e-a8e2-fbeab44bc319)

Обратите внимание на запись number
Это и есть высота синхронизации вашей ноды, которую нужно сравнить с высотой сети в эксплорере

![image](https://github.com/freshe4qa/opside/assets/85982863/741efa8d-7147-47db-b749-92140cf94340)

После полной синхронизации переходим к депозиту токенов в вашего валидатора

### Депозит токенов
Открываем файл deposit и копируем информацию
```
#ЗАМЕНИТЕ ИМЯ ФАЙЛА НА ТО, КОТОРОЕ У ВАС
#ФАЙЛ НАХОДИТСЯ В ДИРРЕКТОРИИ /home/opside/testnet-auto-install-v2/validator_keys/

sudo cat /home/opside/testnet-auto-install-v2/validator_keys/deposit_data-<***>.json

#КОПИРУЕМ ВЕСЬ ВЫВОД
```

Переходим на сайт для депозита и соглашаемся со всеми пунктами https://opsi.de/validator/deposit

![image](https://github.com/freshe4qa/opside/assets/85982863/dbb37571-63a0-4d67-b015-83a82434d3a5)

Подключаем кошелек Metamask который вы писали в форме и добавляем сеть

![image](https://github.com/freshe4qa/opside/assets/85982863/ab0b8cb1-d972-426e-9464-a6019386f848)

После подключения продолжаем подтверждать что мы выполнили все нужные действия

![image](https://github.com/freshe4qa/opside/assets/85982863/b9c38a77-f7dc-40f8-8628-1e208a7d0ec3)

После этого у вас откроется окно, где вы должны внести информацию полученную из открытого вами файла (Нужно заменить пункт Upload на Input)

![image](https://github.com/freshe4qa/opside/assets/85982863/a150884c-2106-4989-9f13-60e0fe94820a)

После того как вы вставили вывод из вашего файла - нажимаем продолжить и соглашаемся со всеми пунктами

![image](https://github.com/freshe4qa/opside/assets/85982863/88273d0b-67ff-4904-8a0f-9e1926e202da)

После этого вам нужно выполнить депозит

![image](https://github.com/freshe4qa/opside/assets/85982863/823c2922-d88e-4421-8e0c-927cc3cbb1dd)

![image](https://github.com/freshe4qa/opside/assets/85982863/544b0e03-4b96-4fdd-bb26-c2de7bfce5db)

![image](https://github.com/freshe4qa/opside/assets/85982863/0100e2a7-5826-43cd-a9ca-74dbc85502c7)
