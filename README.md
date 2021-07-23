# O projeto

O projeto consiste em uma fonte de tensão ajustável, que deve ser ligada em uma entrada de 127 V de corrente alternada a 60 Hz e deve fornecer entre 3V a 12V e 100 mA
de corrente contínua

## A fonte

Uma fonte conforme a especificação precisa de algumas etapas e componentes para funcionar. São elas:

### - O transformador
  é o que transforma a tensão de 127 V de entrada em uma tensão menor, para que passe pelos demais componentes. Para
  essa fonte, foi utilizado um transformador que fornece uma tensão de saída de 15 V, próxima dos 12 V que queremos.
  Para o circuito no Falstad, que pede a relação entre espiras de entrada e de saída, foi feito um cálculo simples:
  ![image](https://user-images.githubusercontent.com/37711709/126833504-75abd2b7-06bf-4442-9d79-10b56d16cb23.png)
  onde Vsec é a tensão que queremos na saída e Vprim é a tensão de entrada.
  Agora que temos valores menores para trabalhar, podemos nos preocupar em deixar a corrente contínua
 
### - A retificação
  é a primeira etapa para transformar AC em DC. A retificação faz com que a corrente alternada se torne uma corrente polarizada, removendo
  os "vales" da tensão de entrada e deixando apenas cristas.  
  
 ![image](https://user-images.githubusercontent.com/37711709/126834291-d438e1ff-30fb-4e94-9e6a-74ddc0e0cbf7.png)
  
  Senoide da fonte antes da retificação
  
  A retificação nessa fonte é feita por meio de uma ponte de diodos - que fazem com que a corrente flua em apenas um sentido (caso a sua tensão máxima não seja rompida)
  ![image](https://user-images.githubusercontent.com/37711709/126835671-2c83ff85-1724-4511-8bfe-9ac3e551dd7d.png)
  
  onda após a retificação
  
  É importante notar que cada diodo consome 0,7 V da tensão, portanto nossa tensão anterior de 15 V, nesse
  ponto, já caiu levemente para 13,6 V (apenas dois diodos são usados por vez)
  
  Agora, o objetivo é deixar essa tensão com apenas cristas o mais estável possível
  
### - A filtragem
  é a etapa em que a tensão é filtrada para transformar a corrente em DC - corrente contínua - com menos oscilações.
  O principal responsável por essa etapa é o capacitor. Funciona da seguinte forma:
  O capacitor, em paralelo com o circuito que temos até agora, é carregado quando os diodos deixam a corrente passar, e, na falta
  de corrente, os momentos baixos do gráfico anterior, age como uma fonte para o resto do circuito.
  Para essa finalidade, quanto maior fosse a capacitância do capacitor, melhor seria, pois ele forneceria
  tensão suficiente para que o ripple, a variação de tensão, fosse mínima. Mas na prática, não se pode
  usar um capacitor tão grande, tanto pelo custo quanto pelo tamanho. O quão grande precisa ser o capacitor então?
  O suficiente para que o ripple fique em até 10% da tensão. Descobrimos a capacitância a partir da seguinte fórmula
  
  ![image](https://user-images.githubusercontent.com/37711709/126838852-3a9e1ae3-3735-4a21-8904-9ac5a3a5807f.png)

  que nos diz que o capacitor precisa ter 600 µF. O capacitor comercial mais próximo e acima disso, e, portanto, ainda melhor que o calculado,
  é o de 1000 µF, sendo que ele foi escolhido para a fonte.
  
### - A regulação
  etapa em que a corrente recebe _tweaks_ para ficar conforme a especificação. Nessa etapa, são usados o potenciômetro, o diodo zener e um transistor
  
