# Configuração do script para Smart Meter Interface (SMI)

Após abrir o web-gui do Tasmota, pelo seu IP local, deverá aceder à página de "Configuração" e "Editar Script".

Deverá ativar a opção de "script ativado" e colar o seguinte script para contador monofásico:

```js
>D

>BS

smlj=0
tper=60

=>sensor53 r

>S

if upsecs==55
then
smlj=1
endif

>M 1

+1,14,m,1,9600,EB,5,50,0104006C,01040079,0104007A,0104007F,r010400260003,0104000B,01040084

1,=hVALORES TÉCNICOS
1,010404UUuuxxxx@i0:10,Tensão,V,Voltage_P1,17
1,010404xxxxUUuu@i0:10,Corrente,A,Current_P1,17
1,010408UUuuUUuuxxxxxxxxxxxx@i1:1,Potência ativa,W,Power_P1,16
1,010406xxxxxxxxUUuu@i2:1000,Fator de potência,pu,PFactor_P1,19
1,01040aUUuuxxxx@i3:10,Frequência,Hz,Frequency_P1,17
1,=h&#8205;
1,=hTOTALIZADORES DE ENERGIA
1,01040CUUuuUUuu@i4:1000,Vazio (1),kWh,Energy_P1_R1,17
1,01040CxxxxxxxxUUuuUUuu@i4:1000,Ponta (2),kWh,Energy_P1_R2,17
1,01040CxxxxxxxxxxxxxxxxUUuuUUuu@i4:1000,Cheia (3),kWh,Energy_P1_R3,17
1,=h&#8205;
1,=hESTADOS
1,010406uuxxxxxxxx@i5:1,Tarifa,,Tariff_P1,16
1,010406uuxxxxxxxx@i6:1,DCP,,DCP_P1,16


#

```

Este script extrairá as seguintes grandesas elétricas e informações técnicas do contador inteligente, a cada 5 segundos:

* Tensão (V)
* Intensidade de corrente (A)
* Potência ativa (W)
* Frequência (Hz)
* Fator de potência (pu)
* Totalizador de energia consumida na tarifa 1 (kWh)
* Totalizador de energia consumida na tarifa 2 (kWh)
* Totalizador de energia consumida na tarifa 3 (kWh)
* Estado do Disjuntor Controlador de Potência embutido na EDP Box
  * `0` = desligado
  * `1` = ligado
  * `2` = pronto para re-ligar
* Tarifa atual
  * `1` = Vazio
  * `2` = Ponta
  * `3` = Cheia

Estes dados são pertencentes à fase Nº 1 de consumo, a única em instalações monofásicas. Para instalações trifásicas ou com produção de energia, deverá consultar a documentação citada na página principal.

Após submeter, deverá desligar e religar a alimentação do Wemos D1 mini. Posteriormente ao início da firmware, deverá obter a seguinte visualização correta, como exemplo:

![tasmota_edp_box](./img/tasmota_edp_box.png)
>

Script para contador trifásico:

Contributo de [nikito7](https://github.com/nikito7), com mais info aprofundada para contadores trifásicos e com venda de energia à rede, no seu [repositório](https://github.com/nikito7/edpbox)

```js
>D

>BS

smlj=0
tper=60

=>sensor53 r

>S

if upsecs==55
then
smlj=1
endif

>M 1

+1,14,m,1,9600,EB,5,50,0104006C,01040079,0104007A,0104007F,r010400260003,0104006E,01040070,0104000B,01040084
1,=hVALORES TÉCNICOS
1,010404UUuuxxxx@i0:10,Tensão L1,V,Voltage_L1,17
1,010404UUuuxxxx@i5:10,Tensão L2,V,Voltage_L2,17
1,010404UUuuxxxx@i6:10,Tensão L3,V,Voltage_L3,17
1,010404xxxxUUuu@i0:10,Corrente L1,A,Current_L1,17
1,010404xxxxUUuu@i5:10,Corrente L2,A,Current_L2,17
1,010404xxxxUUuu@i6:10,Corrente L3,A,Current_L3,17
1,010408UUuuUUuuxxxxxxxxxxxx@i1:1,Potência Activa,W,Power_P1,16
1,010406xxxxxxxxUUuu@i2:1000,Factor de Potência,pu,PFactor_P1,19
1,01040aUUuuxxxx@i3:10,Frequência,Hz,Frequency_P1,17
1,=h&#8205;
1,=hTOTALIZADORES DE ENERGIA
1,01040CUUuuUUuu@i4:1000,Vazio (1),kWh,Energy_P1_R1,17
1,01040CxxxxxxxxUUuuUUuu@i4:1000,Ponta (2),kWh,Energy_P1_R2,17
1,01040CxxxxxxxxxxxxxxxxUUuuUUuu@i4:1000,Cheia (3),kWh,Energy_P1_R3,17
1,=h&#8205;
1,=hESTADOS
1,010406uuxxxxxxxx@i7:1,Tarifa,,Tariff_P1,16
1,010406uuxxxxxxxx@i8:1,DCP,,DCP_P1,16

#
```

Este script extrairá as seguintes grandesas elétricas e informações técnicas do contador inteligente, a cada 5 segundos:

* Tensão (V)
* Intensidade de corrente (A)
* Potência ativa (W)
* Frequência (Hz)
* Fator de potência (pu)
* Totalizador de energia consumida na tarifa 1 (kWh)
* Totalizador de energia consumida na tarifa 2 (kWh)
* Totalizador de energia consumida na tarifa 3 (kWh)
* Estado do Disjuntor Controlador de Potência embutido na EDP Box
  * `0` = desligado
  * `1` = ligado
  * `2` = pronto para re-ligar
* Tarifa atual
  * `1` = Vazio
  * `2` = Ponta
  * `3` = Cheia

## Mais info

[Home Assistant Core e a sua configuração - Para método direto e indireto](../Home%20Assistant/README.md)

[Voltar](./README.md)
