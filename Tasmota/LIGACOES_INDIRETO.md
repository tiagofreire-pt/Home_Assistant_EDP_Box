# Ligações

Dos pinos Nº 1 `GND`, Nº 5 `(A+)` e Nº 3 `(B-)` existentes na porta HAN, deverão ser ligados os seus correspondentes no chicote, instalado pela EDP Distribuição S.A., aos respectivos terminais `GND, `A+` e `B-` do conversor TTL vs RS-485:

![tasmota-rs485](./img/tasmota-rs485.png)
>

Entre os terminais `A+` e `B-` do conversor TTL vs RS-485, é recomendado ser instalada em paralelo uma resistência de 120 Ohm. [Mais info aqui](../Energy%20Box#impedância-de-linha).

Deverá também acautelar a correta configuração do broker MQTT (IP, username, password, tópico MQTT, et al), nos menus de configuração do Tasmota.

## Mais info

[Configuração do script para Smart Meter Interface (SMI)](./CONFIGURAÇÃO-SCRIPT-SMI.md)

[Voltar](./README.md)

