# Comunicação

A porta HAN permite comunicação em [RS-485](https://en.wikipedia.org/wiki/RS-485), com modo `full duplex`. Todavia, por especificação da EDP Distribuição, apenas está disponível comunicação com modo `half duplex`.

A comunicação de dados funcionará em modo mestre -> escravo, sendo o escravo a EDP Box e o mestre o hub com Home Assistant Core (método direto) ou com Tasmota (método indireto). 

O protocolo de comunicação em tramas é Modbus e está implementado em Home Assistant na integração nativa [Modbus](https://www.home-assistant.io/integrations/modbus/).


## Mais info

[Voltar](../README.md)

