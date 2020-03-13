# Configuração do Home Assistant Core

## Ficheiro de configuração

Deverá transpôr o conteúdo do ficheiro [configuration.yaml](./configuration.yaml) para o seu, na sua instalação de Home Assistante Core.

Esta configuração permitirá obter as seguintes entidades de consumo e em valores instantâneos:

* Tensão
* Intensidade de corrente
* Fator de potência
* Frequência da rede eléctrica
* Tarifa
* Estado do Disjuntor Controlador de Potência (DCP)

## Personalizar as entidades geradas

Para personalizar os sensores gerados com essa configuração, é proposto um código e conteúdo para colocar no seu ficheiro [customize.yaml](./customize.yaml)

## Aplicação das configurações

Deverá re-iniciar a sua instalação do Home Assistant Core e, posteriormente, poderá configurar um cartão do `lovelace`, conforme a seguinte proposta:

```yaml
entities:
  - entity: sensor.voltage_l1
  - entity: sensor.current_l1
  - entity: sensor.tariff
  - entity: sensor.power_factor
  - entity: sensor.frequency
  - entity: sensor.switch_control_state
show_header_toggle: false
title: EDP Energy Box
type: entities
```

# Mais info

[Voltar](../README.md)
