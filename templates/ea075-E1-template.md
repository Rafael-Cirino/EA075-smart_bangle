# Jardim Doméstico Automatizado

# Automated Home Garden

## Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de graduação _EA075 - Sistemas Embarcados_, oferecida no segundo semestre de 2022, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

Thiago Miguel dos Santos 187607, Eng. Elétrica.
Bruna Erica Santana Santos de Oliveira 167770, Eng Elétrica.

## Descrição do Projeto

O contato com a natureza é essencial para a saúde mental de um indivíduo, desde um caminhar pela floresta até o simples olhar para uma decoração composta por plantas e flores. Tendo em vista a necessidade deste contato, muitas pessoas recorrem ao cultivo de plantas em seus lares, o que é considerado uma terapia [1]. Porém nem todos conseguem manter os cuidados constantes com as plantas e muitas espécies demandam cuidados mais rígidos. Essa é a motivação para o projeto em questão, “Jardim Doméstico Automatizado” é a proposta de um dispositivo que ajude o cultivo de plantas no ambiente doméstico. Seu objetivo é fazer com que mesmo os tutores mais atarefados possam desfrutar de plantas saudáveis em seu ambiente de vivência. Plantas essas que podem ser até mesmo para uso em refeições, como temperos e hortaliças em pequena quantidade. Ou então flores que dão vida ao ambiente.

## Descrição Funcional

> A descrição funcional do projeto é a principal entrega do E1 e pode ser realizada neste próprio arquivo Markdown, com links para diagramas ou outros arquivos que estejam no próprio repositório.

### Funcionalidades

A finalidade deste projeto é manter a planta saudável através dos atuadores de luz em frequências otimizadas para a planta (Luzes ultravioleta, luzes coloridas e infravermelho) [2], e irrigação. O controle é alimentado pela informação de sensores de umidade e luz. Além disso, é aplicado um sensor de temperatura para acompanhamento ambiental, que deve auxiliar o tutor da planta em seus cuidados, alertando em caso de desconforto térmico da planta.

  
  Irrigação: O sistema é capaz de regar a terra a partir da informação de umidade proveniente do sensor específico.

Iluminação: O sistema é capaz de prover doses de luz de acordo com informações dadas pelo usuário em relação à planta e também do sensor de luz presente.

Histórico: O sistema faz um acompanhamento dos atributos de leitura e atuadores para que seja possível um acompanhamento e correlações do desenvolvimento da planta pelo tutor.

Alertas: O acompanhamento contínuo de sensores pode emitir alertas ao tutor de acordo com as seguintes severidades: Umidades extremas (alta e baixa), temperaturas extremas, quantidades de luz extremas.

### Configurabilidade
O usuário pode escolher o perfil da planta escolhida de acordo com a família. Isso ajusta níveis no controle de irrigação e iluminação.

O usuário pode configurar manualmente pontos de operação das variáveis controladas: umidade e iluminação.

### Eventos

Falta de água: Quando o sensor de umidade do solo faz uma leitura abaixo da recomendada.

  

Falta de iluminação: Ocorre quando a integração de iluminação em uma janela de tempo não é suficiente para suprir a planta.

  

Temperaturas extremas: Ocorre quando o sensor de temperatura atinge temperaturas inadequadas para a família selecionada.

### Tratamento de Eventos

Falta de água: Aciona válvula para liberação de água e liga a bomba de água do reservatório.

Falta de Iluminação: Ajusta a intensidade das lâmpadas de iluminação através de PWM [3] com razão de intensidade regulada para a família da planta para cada comprimento de onda: Ultravioleta, azul, magenta e infravermelho.

Temperaturas extremas: Emite um alerta ao usuário através de aplicativo próprio e/ou aplicativos de mensagem.

## Descrição Estrutural do Sistema

Atuadores:

-   Bomba de água
    
-   Válvula solenóide para água
    
-   Lâmpada LED com emissão em Infravermelho
    
-   Lâmpada LED com emissão em Azul
    
-   Lâmpada LED com emissão em Vermelho
    
-   Lâmpada LED com emissão em Ultra Violeta
    

  

Sensores:

-   Sensor de umidade de solo [SEN-13322](https://www.sparkfun.com/products/13322)
    
-   Sensor de temperatura
    
-   Sensor de luz em Infravermelho
    
-   Sensor de luz RGB [ISL29125](https://www.renesas.com/us/en/products/sensor-products/light-proximity-sensors/ambient-light-sensors/ambient-light-digital-sensors/isl29125-digital-red-green-and-blue-color-light-sensor-ir-blocking-filter)
    
-   Sensor de luz em Ultra Violeta ML8511
    
![](https://lh4.googleusercontent.com/s5AMcctccOxjfZiaWESopzCUp4yHrVsN4rbxxCcutV4tQIEsEq_Ftoq7y5zDsDFBGJz5zEVaqXUpR2-Zzu4paWhCk7iW2XiBEZd9p25rY0cTeUHIZFOY_2vd8BIxdcF_nUSO7ek-_FaH6YXSUbT8yL99kvce2QpGIJ9xjSLxRqWSRnAHLtb_WHbPKg)
  

Comunicação

-   Comunicação sem fio WiFi

## Referências

1.  [https://edition.cnn.com/2018/08/03/health/sw-horticultural-therapy/index.html](https://edition.cnn.com/2018/08/03/health/sw-horticultural-therapy/index.html)
    
2.  [https://www.ul.com/services/horticultural-lighting?utm_mktocampaign=lightingglobal_googleads&utm_mktoadid=534750355857&campaignid=13972433958&adgroupid=127913040191&matchtype=b&device=c&creative=534750355857&keyword=horticultural%20light&gclid=CjwKCAjwpqCZBhAbEiwAa7pXeeyfFV-wXcNtfY-oTxTUw52vPz036KG_f6bVc6y8Rdku19TboTax-xoCd2IQAvD_BwE](https://www.ul.com/services/horticultural-lighting?utm_mktocampaign=lightingglobal_googleads&utm_mktoadid=534750355857&campaignid=13972433958&adgroupid=127913040191&matchtype=b&device=c&creative=534750355857&keyword=horticultural%20light&gclid=CjwKCAjwpqCZBhAbEiwAa7pXeeyfFV-wXcNtfY-oTxTUw52vPz036KG_f6bVc6y8Rdku19TboTax-xoCd2IQAvD_BwE)
    
3.  [https://docs.arduino.cc/learn/microcontrollers/analog-output](https://docs.arduino.cc/learn/microcontrollers/analog-output)
    
4.

> Se aplicável, classifique os eventos que são periódicos (procure especificar a periodicidade) e os que são não-periódicos
> (qual o tempo mínimo entre dois eventos sucessivos)?

### Tratamento de Eventos
> Qual comportamento o sistema deve ter para tratar corretamente cada evento?

## Descrição Estrutural do Sistema
> Junto com a descrição do comportamento do sistema, deve-se especificar, em nível de bloco ou sistema, a estrutura necessária 
> para captar os eventos do mundo externo, para alojar e processar o programa de tratamento de eventos, e para atuar sobre o mundo externo.
>
> Para essa descrição recomenda-se a criação de diagramas de blocos.
> Nesse diagrama, devem ser destacados os blocos funcionais que compõem o sistema, incluindo uma síntese das funcionalidades de cada bloco.
> Além disso, deve-se esclarecer também o relacionamento entre estes blocos, incluindo os principais sinais de comunicação entre
> os blocos de forma a assegurar a execução de todas as tarefas que o sistema deve realizar.
> 
> Você sabia? Ferramentas como o `draw.io` permitem integração com o Github.
> 

## Referências
> Seção obrigatória. Inclua aqui referências utilizadas no projeto.
