# Comunicação

A porta HAN permite comunicação em [RS-485](https://en.wikipedia.org/wiki/RS-485), com modo `full duplex`. Todavia, por especificação da `E-Redes S.A.`, apenas está disponível comunicação com modo `half duplex`.

O protocolo de comunicação em tramas é [MODBUS](https://en.wikipedia.org/wiki/Modbus).

A comunicação de dados funcionará em modo mestre -> escravo, sendo o escravo a EDP Box e o mestre o hub com Home Assistant Core (método direto) ou o microcontrolador ESP8266 com Tasmota (método indireto).

## Mais info

[Voltar](../README.md)
