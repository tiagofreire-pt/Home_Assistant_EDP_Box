# Ligações

Dos pinos Nº 1 `GND`, Nº 5 `(A+)` e Nº 3 `(B-)` existentes na porta HAN, deverão ser ligados os seus correspondentes no chicote, instalado pela EDP Distribuição S.A., aos respectivos terminais `GND, `A+` e `B-` do conversor TTL vs RS-485:

![tasmota-rs485](./img/tasmota-rs485.png)
>

A disponibilidade de alimentação a partir da porta HAN está limitada a uma intensidade de corrente máxima de 150 mA. **Recomenda-se não usar a porta HAN para alimentação de qualquer dispositivo.**

Entre os terminais `A+` e `B-` do conversor TTL vs RS-485, *poderá* eventualmente ser instalada em paralelo uma resistência de 120 Ohm. [Mais info aqui](../Energy%20Box#impedância-de-linha).

**Deverá acautelar todos os requisitos e condições para este tipo de aplicação, segundo o documento fornecido pela `EDP Distribuição S.A.`, vide `Módulos alimentados pela porta HAN`, [aqui](https://www.edpdistribuicao.pt/sites/edd/files/2019-06/Requisitos%20dos%20m%C3%B3dulos%20HAN_2019.05.31.pdf).**

Deverá também acautelar a correta configuração do broker MQTT (IP, username, password, tópico MQTT, et al), nos menus de configuração do Tasmota.

## Mais info

[Configuração do script para Smart Meter Interface (SMI)](./CONFIGURAÇÃO-SCRIPT-SMI.md)

[Voltar](./README.md)

