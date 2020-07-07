# Descarga e instalação do firmware no ESP8266

## Descarga do firmware Tasmota pré-compilado (recomendado)

Deverá descarregar o firmware pré-compilado, [aqui](./tasmota.bin). 

Este firmware pré-compilado é **personalizado** para esta abordagem, sendo baseado no repositório do Tasmota, versão 8.3.1, preparado para memória flash até 1 MB. Compatível com Wemos D1 Mini e outros dispositivos, por exemplo, da marca Sonoff ou NodeMCU.

## Compilação do firmware Tasmota (método alternativo avançado - não recomendado)

Se não pretender usar o firmware pré-compilado disponibilizado neste repositório, poderá mais facilmente compilar o Tasmota usando [esta proposta de ambiente em docker](https://github.com/benzino77/tasmocompiler).

No ponto 3 do TasmoCompiler, para garantir as funcionalidades mais utilizadas em Tasmota, deverá manter ativadas apenas as seguintes opções mínimas:

* Amazon Alexa
* Displays (I2C/SPI)
* Domoticz
* Energy sensors
* Home Assistant
* IO port expander
* Timers
* Web interface

Deverá obrigatoriamente adicionar a configuração seguinte quando lhe o for solicitado no ponto 4 (`Custom parameters`):

```
#ifndef USE_SCRIPT
#define USE_SCRIPT
#endif
#ifndef USE_SML_M
#define USE_SML_M
#endif
#ifdef USE_RULES
#undef USE_RULES
#endif
#define SML_MAX_VARS 12
```

Mais info, [aqui](https://tasmota.github.io/docs/Smart-Meter-Interface/).


## Instalação do firmware no ESP8266 (descarregado ou compilado manualmente)

Recomenda-se a utilização do software [Tasmotizer](https://github.com/tasmota/tasmotizer) para flashar o seu ESP8266. É compatível com Microsoft Windows e GNU/Linux.

Poderá utilizar outro software à sua livre escolha.


# Mais info


[Ligação física entre o contador inteligente, o ESP8266 e o hub com Home Assistant Core](./LIGACOES_INDIRETO.md)

[Voltar](../README.md)
