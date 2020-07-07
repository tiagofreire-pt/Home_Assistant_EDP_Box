# Configuração do script para Smart Meter Interface (SMI)

Após abrir o web-gui do Tasmota, pelo seu IP local, deverá aceder à página de "Configuração" e "Editar Script".

Deverá ativar a opção de "script ativado" e colar o seguinte script:

```
>D
 
>B
=>sensor53 r
 
>M 1
 
+1,14,m,1,9600,EB,5,50,0104006C,01040079,0104007A,0104007F,01040026,01040027,01040028,0104000B,01040084
 
1,=hVALORES TÉCNICOS
1,010404UUuuxxxx@i0:10,Tensão,V,Voltage_P1,17
1,010404xxxxUUuu@i0:10,Corrente,A,Current_P1,17
1,010408UUuuUUuuxxxxxxxxxxxx@i1:1,Potência ativa,W,Power_P1,16
1,010406xxxxxxxxUUuu@i2:1000,Fator de potência,pu,PFactor_P1,19
1,01040aUUuuxxxx@i3:10,Frequência,Hz,Frequency_P1,17
1,=h&#8205;
1,=hTOTALIZADORES DE ENERGIA
1,010408UUuuUUuuxxxxxxxxxxxx@i4:1000,Vazio (1),kWh,Energy_P1_R1,17
1,010408UUuuUUuuxxxxxxxxxxxx@i5:1000,Ponta (2),kWh,Energy_P1_R2,17
1,010408UUuuUUuuxxxxxxxxxxxx@i6:1000,Cheia (3),kWh,Energy_P1_R3,17
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
  - `0` = desligado
  - `1` = ligado
  - `2` = pronto para re-ligar
* Tarifa atual
  - `1` = Vazio
  - `2` = Ponta
  - `3` = Cheia


Estes dados são pertencentes à fase Nº 1 de consumo, a única em instalações monofásicas. Para instalações trifásicas ou com produção de energia, deverá consultar a documentação citada na página principal.

Após submeter, deverá desligar e religar a alimentação do Wemos D1 mini. Posteriormente ao início da firmware, deverá obter a seguinte visualização correta, como exemplo:

![tasmota_edp_box](./img/tasmota_edp_box.png)
>


# Mais info

[Home Assistant Core e a sua configuração - Para método direto e indireto](../Home%20Assistant/README.md)

[Voltar](./README.md)
