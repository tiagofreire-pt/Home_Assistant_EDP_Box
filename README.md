# Âmbito

A integração de contadores inteligentes com sistemas de domótica permite potenciar automações, controlo e análises com base na informação disponível das grandezas elétricas e estados do equipamento. Nomeadamente, tensão, intensidade de corrente, potência ativa, fator de potência, frequência, estado do disjuntor controlador de potência, *et al*.

A `E-Redes S.A.` (anteriormente `EDP Distribuição S.A.`) surge neste contexto enquanto Operadora da Rede de Distribuição de baixa tensão. Independentemente do comercializador de energia elétrica com quem tem contrato de fornecimento e de estar em mercado regulado ou liberalizado.

# Objetivo

Pretende-se partilhar o conceito de integração de dispositivos EDP Box com um hub de domótica a executar [Home Assistant Core](https://www.home-assistant.io/).

Esta integração é possível graças à porta de comunicação HAN que está disponível internamente nos contadores inteligentes. É também proposto neste repositório um procedimento para requisitar formalmente o acesso a esta porta e determinar o suporte do seu contador atual.

São propostas duas alternativas distintas possíveis para integração:

1. Integração indireta com Home Assistant, usando um microcontrolador ESP8266 com firmware Tasmota, através de MQTT.
2. Integração direta com Home Assistant Core, através do seu componente nativo para protocolo MODBUS.

# Conteúdos

1. [A EDP Box e a sua porta HAN](EDP%20Box/README.md)
   1. [Pedido de acesso e suporte do seu atual contador](EDP%20Box/README.md#pedido-de-acesso)
   2. [Interface físico](EDP%20Box/README.md#interface-físico)
   3. [Impedância de linha](EDP%20Box/README.md#impedância-de-linha)
   4. [Comunicação](EDP%20Box/COMUNICACAO.md)
2. [Tasmota e script de configuração para MODBUS - Para método indireto](Tasmota/README.md)
   1. [Descarga e instalação do firmware no ESP8266](Tasmota/README.md)
   2. [Ligação física entre o contador inteligente e o ESP8266](Tasmota/LIGACOES_INDIRETO.md)
   3. [Configuração do perfil de GPIO](Tasmota/LIGACOES_INDIRETO.md#configuração-do-perfil-de-gpio)
   4. [Configuração de MQTT](Tasmota/LIGACOES_INDIRETO.md#configuração-de-mqtt-no-tasmota)
   5. [Configuração do script para Smart Meter Interface (SMI)](Tasmota/CONFIGURAÇÃO-SCRIPT-SMI.md)
3. [Home Assitant Core e a sua configuração - Para método direto e indireto](Home%20Assistant/README.md)
   1. [Ligação física entre o contador inteligente e o hub com Home Assistant Core](Home%20Assistant/LIGACOES_DIRETO.md)
   2. [Ficheiro de configuração](Home%20Assistant/README.md#configuração-do-home-assistant-core)
   3. [Personalizar as entidades geradas - método direto](Home%20Assistant/README.md#personalizar-as-entidades-geradas)
   4. [Aplicação das configurações](Home%20Assistant/README.md#aplicação-das-configurações)

# Requisitos mínimos

## Transversais

* Contador inteligente com porta HAN ativada, suportando o protocolo de tramas MODBUS.
* Acesso exterior à porta HAN, previamente instalado pela E-Redes S.A.;
* Raspberry Pi 3 B+ ou superior (alternativamente, Home Assistant Core em outra máquina física ou virtualizada);
* Home Assistant Core instalado (versão inicial de prova de conceito: 0.106.6. **Recomendada a versão 2021.9.6 ou superior**);
* Mosquitto MQTT Broker instalado (versão 5.0 ou superior, como add-on oficial em Home Assistant Core. Ou qualquer outro broker MQTT à sua escolha);
* Acessórios de ligação variados.

## Exclusivamente para o 1º método (indireto)

* Conversor TTL vs RS-485 (por exemplo, "TTL to RS485 For Arduino")
* Wemos D1 Mini

## Exclusivamente para o 2º método (direto)

* Conversor USB - TTL vs RS-485 (por exemplo, "Waveshare Industrial USB to RS485")
* Cabo extensor USB "A macho" - "A fêmea" (recomendado)

# Fontes

[EDP Box - HAN protocol specification (DEF-C44-509/N) - Julho 2020](https://www.e-redes.pt/sites/eredes/files/2020-07/DEF-C44-509.pdf)

[Descrição dos requisitos e respetiva aplicabilidade em função do tipo de módulo HAN - Abril 2021](https://www.e-redes.pt/sites/eredes/files/2021-04/Requisitos%20dos%20m%C3%B3dulos%20HAN.pdf)

[Contadores de energia elétrica - Especificação funcional (DEF-C44-506/N)](https://www.e-redes.pt/sites/edd/files/normative_docs/DEF-C44-506N.pdf)

[Novos Equipamentos](https://www.e-redes.pt/sites/eredes/files/2021-03/Contadores_Site_E_REDES_2021_02.pdf)

# Notas importantes

A porta de comunicação HAN está no interior das EDP Box. A manipulação, danos, prejuízos ou acesso não autorizado a esta porta é da total responsabilidade do próprio.

Todas as marcas registadas, nomes de produtos ou de marcas, referidas neste documento, são propriedade registada do respectivo detentor.

# Versionamento

* 13 de Março de 2020: primeira integração publicada e validada, através de USB.
* 4 de Julho de 2020: segunda integração validada e publicada, através de MQTT e WIFI.
* 10 de Outubro de 2020: atualização para contadores trifásicos (@nikito7) e Tasmota 8.5.1.
* 11 de Abril de 2021: suporte para contadores ZIV.
* 20 de Maio de 2021: todos os contadores existentes funcionam.
* 13 de Setembro de 2021: atualização do método directo, conforme a revisão à integração `modbus`.

# A fazeres

Método direto (atualizado em 13/09/2021):

* [X] Potência ativa
* [X] Estado do DCP
* [X] Totalizadores de energia
* [ ] Religação do DCP

Método indireto (atualizado em 05/07/2020):

* [X] Tarifa
* [X] Estado do DCP
* [X] Totalizadores de energia
* [ ] Religação do DCP
