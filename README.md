# O projeto

O projeto consiste em uma fonte de tensão ajustável, que deve ser ligada em uma entrada de 127 V de corrente alternada a 60 Hz e deve fornecer entre 3V a 12V e 100 mA
de corrente contínua

## A fonte

Uma fonte conforme a especificação precisa de algumas etapas e componentes para funcionar. São elas:

### - O transformador
  é o que transforma a tensão de 127 V de entrada em uma tensão menor, para que passe pelos demais componentes. Para
  essa fonte, foi utilizado um transformador que fornece uma tensão de saída de 17 V, mais próxima dos 12 V que queremos.
  Agora que temos valores menores para trabalhar, podemos nos preocupar em deixar a corrente contínua
 
### - A retificação
  é a primeira etapa para transformar AC em DC. A retificação faz com que a corrente alternada se torne uma corrente polarizada, removendo
  os "vales" da tensão de entrada e deixando apenas cristas.  
  
 ![image](https://user-images.githubusercontent.com/37711709/126834291-d438e1ff-30fb-4e94-9e6a-74ddc0e0cbf7.png)
  
  Senoide da fonte antes da retificação
  
  A retificação nessa fonte é feita por meio de uma ponte de diodos - que fazem com que a corrente flua em apenas um sentido (caso a sua tensão máxima não seja rompida)
  
  ![image](https://user-images.githubusercontent.com/37711709/126835671-2c83ff85-1724-4511-8bfe-9ac3e551dd7d.png)
  
  onda após a retificação
  
  É importante notar que cada diodo consome 0,7 V da tensão, portanto nossa tensão anterior de 17 V, nesse
  ponto, já caiu levemente para 15,6 V (apenas dois diodos são usados por vez)
  
  Agora, o objetivo é deixar essa tensão com apenas cristas o mais estável possível
  
### - A filtragem
  é a etapa em que a tensão é filtrada para transformar a corrente em DC - corrente contínua - com menos oscilações.
  O principal responsável por essa etapa é o capacitor. Funciona da seguinte forma:
  O capacitor, em paralelo com o circuito que temos até agora, é carregado quando os diodos deixam a corrente passar, e, na falta
  de corrente, os momentos baixos do gráfico anterior, age como uma fonte para o resto do circuito.
  Para essa finalidade, quanto maior fosse a capacitância do capacitor, melhor seria, pois ele forneceria
  tensão suficiente para que o ripple, a variação de tensão, fosse mínima. Mas na prática, não se pode
  usar um capacitor tão grande, tanto pelo custo quanto pelo tamanho. A partir de testes no Falstad é possível concluir que um capacitor
  de 1000 µF é adequado para um ripple pequeno, além de ser um valor comercialmente comum e barato.
  
### - A regulação
  etapa em que a corrente recebe _tweaks_ para ficar conforme a especificação. Nessa etapa, é utilizado o diodo zener. Em diodos comuns, quando se atinge a tensão de ruptura, eles passam a deixar uma corrente extremamente grande passar por eles no sentido inverso. No diodo zener, quando se atinge uma tensão chamada tensão zener, ele passa a permitir a passagem de correntes de forma a manter constante a tensão entre seus terminais, agindo como um curto circuito. Isso tem como efeito, no circuito, "cortar" a tensão extra que tinhamos para o valor de sua tensão zener. Como queremos uma tensão de 12 V, podemos usar o modelo comercial de Zener de 12 V. O zener precisa ser ligado em série com um resistor que vai consumir a tensão excedente gerada nesse ramo do circuito para que não queime

### - O circuito final no Falstad
![image](https://user-images.githubusercontent.com/37711709/126852283-be6da977-5270-4caf-abfb-50f89dc9fec8.png)

[link para o circuito no Falstad](https://tinyurl.com/yhf42j27)

A montagem, que contou com muita tentativa e erro, foi feita no simulador, o que forneceu os valores necessários de cada componente. Alguns outros componentes foram usados no circuito, e estão listados abaixo

  - Transistor: é usado para adequar a corrente que vai para o potenciômetro
  - Potenciômetro: é usado para controlar a tensão no terminal de saída, variando de 3V a 12V
  - Resistor de 2.2KΩ: regula a voltagem do circuito

### - A montagem no software Eagle
  
 ### - Componentes e preços
 Abaixo vai uma tabela com os componentes usados, suas especificações, preços e links
 
 |Nome do Componente |Especificações|Preço R$ |
 |-------------------|--------------|------|
 |Transformador|trafo que transforma entradas de 110 ou 220 V em 15 V, com corrente de 1A|[41,31](https://www.baudaeletronica.com.br/transformador-trafo-1a-15v.html)|
 |Capacitor eletrolítico|1000uF / 16V|[0,46](https://www.baudaeletronica.com.br/capacitor-eletrolitico-1000uf-16v.html)|
 |Resistor 2.2k|2.2 kΩ, 2W de potência|[0,38](https://www.baudaeletronica.com.br/resistor-2k2-5-2w.html)|
 |Resistor 560|560 Ω, 2W de potência|[0,39](https://www.baudaeletronica.com.br/resistor-560r-5-2w.html)|
 |Potenciômetro|Potenciômetro linear de 5000Ω|[1,99](https://www.baudaeletronica.com.br/potenciometro-linear-de-5k-5000.html)|
 |Diodo Zener|1N4744A, de 15V e 1 W|[0,20](https://www.baudaeletronica.com.br/diodo-zener-1n4744-15v-1w.html)|
 |Diodo retificador|1N5404, de 3A|4 x [0,34](https://www.baudaeletronica.com.br/diodo-1n5404.html)|
 |Transistor NPN BC337|tensão máxima de 45V e corrente máxima IC de 500mA|[0,20](https://www.baudaeletronica.com.br/transistor-npn-bc337.html)|
 
