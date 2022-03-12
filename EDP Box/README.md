# A porta HAN

## Pedido de acesso e suporte do seu atual contador

`ATENÇÃO: Não se conhece qualquer obrigação legal ou regulatória do Operador de Rede de Distribuição ter de providenciar este acesso. Portanto, considere como uma eventual cortesia.`

Em primeiro lugar, verifique se o seu contador de energia elétrica consta da seguinte lista de equipamentos com porta HAN: [Novos Equipamentos](https://www.e-redes.pt/sites/eredes/files/2019-04/Novos_Equipamentos.pdf)

### Caso o seu modelo `NÃO` corresponda exatamente a algum dos supracitados:

Deverá aguardar pela substituição programada do seu contador de energia elétrica, aquando da sua obsolescência total.

### Se o seu modelo `corresponde exatamente` a algum dos supracitados:

**ALERTA: Não se dão quaisquer garantias de funcionamento.**

Este repositório contém apenas e só uma prova de conceito de integração, validada experimentalmente com sucesso em alguns modelos (27/03/2021):

* Janz C3801 (R4LRFGPRS) - 1 caso de sucesso
* Sagemcom CX2000-9 - 2 casos de sucesso
* LANDIS+GYR ZCXe110CR - 4 casos de sucesso
* KAIFA MA109P - 1 caso de sucesso
* ZIV 5CTME2C [configuração alternativa: Hardware Serial; gpio 1 e 3; mN2; Tasmota Dev > 2021/03/30] - 2 casos de sucesso

Ainda assim, se pretender prosseguir, o acesso a esta porta requerá um pedido formal à E-Redes S.A.

Deverá seguir as instruções que estão neste link: <https://www.e-redes.pt/pt-pt/redes-do-futuro-redes-inteligentes/servicos-redes-inteligentes/acesso-porta-serie-de-comunicacao>

Deverá ter reunir a seguinte informação:

1. Identificação pessoal do titular do contrato de energia elétrica:
   * Nome completo
   * NIF
   * Morada do local de consumo
2. Código do Ponto de Entrega (CPE). Consta na sua fatura de eletricidade;
3. Pretenção de acesso à porta HAN no exterior da EDP Box, através de um chicote terminado em ficha RJ12, para ligação de um periférico do `tipo A - sem ligação à rede BT`, conforme o pinout definido na `secção 3.1` da `DEF-C44-509/N`;
4. Questões sobre eventuais custos, condições e procedimentos.

Haverá uma provável deslocação de um técnico especializado à sua instalação para deselagem, instalação de um chicote exterior e nova selagem do contador inteligente.

## Interface físico

Esta prova de conceito é baseada numa EDP Box da marca Janz, modelo C3801 (R4LRFGPRS), com a sua porta HAN ativada e disponível externamente. Exemplo:

![janz_c3801](./img/janz_c3801.png)
> Fonte: edpdistribuicao.pt

A porta de comunicação tem um formato físico RJ12, de 6 pinos e 6 coneções (6P6C):

![rj-12](https://upload.wikimedia.org/wikipedia/commons/3/3c/Rj25_connector.jpg)
> Fonte: wikipedia.com

| # do pino | Função |
|----------|----------|
| 1| GND |
| 2| A+ (não usada) |
| 3| B- |
| 4| B- (não usada) |
| 5| A+ |
| 6| +5 Volt |

A disponibilidade de alimentação a partir da porta HAN está limitada a uma intensidade de corrente máxima de 150 mA. Considerando também que a função primordial da porta HAN é providenciar comunicação de dados, **é altamente recomendável que seja utilizada alimentação dos dispositivos a conectar a partir de uma fonte de alimentação externa.**

## Impedância de linha

A linha de comunicação, representada pelo chicote exterior a instalar pela E-Redes S.A., *poderá* eventualmente ser terminada com uma resistência de 120 Ohm, por forma a balancear todo o cirtuito com a impedância do cabo. Essa resistência será em paralelo com os terminais `A+` e `B-` do conversor TTL vs RS-485.

## Mais info

[Voltar](../README.md)

[Como se comunica com a EDP Box](./COMUNICACAO.md)
