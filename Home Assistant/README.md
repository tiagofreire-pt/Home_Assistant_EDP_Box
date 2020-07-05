# Configuração do Home Assistant Core

# Método indireto

## Ficheiro de configuração

Deverá transpôr o conteúdo do ficheiro [configuration.yaml](./configuration-indireto.yaml) para o seu, na sua instalação de Home Assistante Core.

Esta configuração permitirá obter as seguintes entidades de consumo e estados, em valores instantâneos (à data de 05/07/2020):

* Tensão (V)
* Intensidade de corrente (A)
* Potência ativa (W)
* Frequência (Hz)
* Fator de potência (pu)
* Totalizador de energia consumida na tarifa 1 - Vazio
* Totalizador de energia consumida na tarifa 2 - Ponta
* Totalizador de energia consumida na tarifa 3 - Cheia
* Tarifa atual
* Estado do Disjuntor Controlador de Potência - DCP


## Aplicação das configurações

Deverá re-iniciar a sua instalação do Home Assistant Core e, posteriormente, poderá configurar um cartão do `lovelace`, conforme a seguinte proposta:

```yaml
entities:
  - entity: sensor.edp_box_tensao
  - entity: sensor.edp_box_corrente
  - entity: sensor.edp_box_potencia_ativa
  - entity: sensor.edp_box_fator_de_potencia
  - entity: sensor.edp_box_frequencia
show_header_toggle: false
title: Contador
type: entities
```

# Método direto

## Ligação física entre o contador inteligente e o hub com Home Assistant Core

Deverá garantir a ligação ao contador, seguindo [estas instruções](./LIGACOES_DIRETO.md).

## Ficheiro de configuração

Deverá transpôr o conteúdo do ficheiro [configuration.yaml](./configuration-direto.yaml) para o seu, na sua instalação de Home Assistante Core.

Esta configuração permitirá obter as seguintes entidades de consumo e estados, em valores instantâneos (à data de 16/06/2020):

* Tensão (V)
* Intensidade de corrente (A)
* Fator de potência (W)
* Frequência da rede eléctrica (Hz)
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
title: Contador
type: entities
```

# Mais info

[Voltar](../README.md)
