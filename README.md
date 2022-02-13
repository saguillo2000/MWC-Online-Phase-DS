# MWC-Online-Phase-DS

Reto de NUWE sobre la fase online para acceder al reto final del Mobile World Congress 2022. En este repositorio se realiza un Exploratory Data Analysis y un modelo predictivo sobre un e-commerce sobre frutas. Los datos que tenemos son los siguientes:


## **mwc22-client_table.csv**                                                                                        
| Variables                |  Descripción                                                                          |
|:-----                    |:-------------------------------------------------------------------------------------:|
| CLIENT ID                | Identificador único del cliente                                                       | 
| CLIENT_SEGMENT           |  Segmento de clientes                                                                 | 
| AVG CONSO                | Consumo medio mensual del cliente calculado a finales de 2020 (en piezas de fruta)    |
| AVG BASKET SIZE          | Tamaño medio de la cesta del cliente calculado a finales de 2020 (en piezas de fruta) |
| RECEIVED_COMMUNICATION   | 1 = Recibió promoción de sus productos / 0 = no la recibió                            |

## **mwc22-orders_table.csv**:

| Variables                |  Descripción                                                                          |
|:-----                    |:-------------------------------------------------------------------------------------:|
| CLIENT ID                | Identificador único del cliente                                                       | 
| NB PRODS                 | Número de 'prods' de la variedad de fruta en el pedido (1 prod = 10 piezas de fruta)  | 
| ORDER ID                 | Identificador único del pedido                                                        |
| FRUIT_PRODUCT            | Variedad de fruta                                                                     |

## **mwc22-client_table+-+test_x.csv**: 
Mismo contenido que **mwc22-client_table.csv** sin los CLIENT_SEGMENT que será la variable a predecir


# 1. Exploratory Data Analysis

Para esta parte del challenge, cabe destacar el uso de la función pivot_table con el objetivo de realizar el siguiente gráfico:

![image](https://user-images.githubusercontent.com/47833532/153759279-63999cd9-6171-4b54-aa99-9328cf99bf91.png)

Dónde se analizan las ventas por piezas de fruta por separado en las ordenes de los clientes. Aparte de algunos porcentajes del uso de las promociones recibidas en los clientes y otros datos descriptivos.


# 2. Predictive Model CLIENT_SEGMENT

En este apartado se ha utilizado un Random Forest para la interpretar los segmentos. Interesante ver la transformación realizada para poder utilizar todos los datos a nuestra disposición en el reto:

![image](https://user-images.githubusercontent.com/47833532/153759450-ce803328-f08f-4f23-b1bc-20e623ff123f.png)

Importante decir que el Order_Id es el recuento de veces que un cliente ha realizado un pedido. A su vez las frutas son todos los 'prods' en todos los pedidos.

En lo referente a resultados del Random Forest vemos lo siguiente en el classification report de sklearn.

<div align="center">
    <img src="https://user-images.githubusercontent.com/47833532/153759562-57d6fb2b-320e-4af5-b408-3ec20e56adc9.png" alt="img3">
</div>

Las conclusiones del modelo de predicción es que el segmento 6 es un segmento de miscelania, es decir si un cliente no encaja en los grupos del 1 al 5 este se introduce al 6.
