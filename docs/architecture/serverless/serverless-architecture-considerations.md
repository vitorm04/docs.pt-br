---
title: Considerações de arquitetura sem servidor - Aplicativos sem servidor
description: Entenda os desafios de arquitetar aplicativos sem servidor, desde a gestão estadual e o armazenamento persistente até a escala, o registro, o rastreamento e os diagnósticos.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522433"
---
# <a name="serverless-architecture-considerations"></a>Considerações sobre a arquitetura sem servidor

Adotar uma arquitetura sem servidor vem com certos desafios. Esta seção explora algumas das considerações mais comuns a serem consideradas. Todos esses desafios têm soluções. Como em todas as opções de arquitetura, a decisão de ficar sem servidor só deve ser tomada depois de considerar cuidadosamente os prós e contras. Dependendo das necessidades do seu aplicativo, você pode decidir que uma implementação sem servidor não é a solução certa para determinados componentes.

## <a name="managing-state"></a>Gerenciar estado

As funções sem servidor, como acontece com os microserviços em geral, são apátridas por padrão. Evitar o estado permite que o servidor seja efêmero, dimensione e forneça resiliência sem um ponto central de falha. Em algumas circunstâncias, os processos de negócios exigem estado. Se o seu processo requer estado, você tem duas opções. Você pode adotar um modelo diferente do sem servidor ou interagir com um serviço separado que forneça estado. Adicionar estado pode complicar a solução e dificultar a escala e potencialmente criar um único ponto de falha. Considere cuidadosamente se sua função absolutamente requer estado. Se a resposta for "sim", determine se ainda faz sentido implementá-la sem servidor.

Existem várias soluções para adotar o Estado sem comprometer os benefícios dos sem servidor. Algumas das soluções mais populares incluem:

- Use um armazenamento de dados temporário ou cache distribuído, como o Redis
- Armazenar estado em um banco de dados, como SQL ou CosmosDB
- Manuseie o estado através de um motor de fluxo de trabalho como funções duráveis

A questão é que você deve estar ciente da necessidade de qualquer gestão estatal dentro dos processos que você está considerando implementar com o serverless.

## <a name="long-running-processes"></a>Processos de longa duração

Muitos benefícios do sem servidor dependem dos processos serem efêmeros. Tempos de execução curtos tornam mais fácil para o provedor sem servidor liberar recursos à medida que as funções terminam e compartilham funções entre hosts. A maioria dos provedores de nuvem limita o tempo total que sua função pode executar para cerca de 10 minutos. Se o seu processo pode demorar mais tempo, você pode considerar uma implementação alternativa.

Existem algumas exceções e soluções. Uma solução pode ser dividir seu processo em componentes menores que individualmente levam menos tempo para serem executados. Se o seu processo for longo por causa das dependências, você também pode considerar um fluxo de trabalho assíncrono usando uma solução como funções duráveis. Funções duráveis pausam e mantêm o estado do seu processo enquanto aguarda um processo externo para terminar. O manuseio assíncrono reduz o tempo de funcionamento do processo real.

## <a name="startup-time"></a>Tempo de inicialização

Uma preocupação potencial com implementações sem servidor é o tempo de inicialização. Para conservar recursos, muitos provedores sem servidor criam infra-estrutura demanda. Quando uma função sem servidor é acionada após um período de tempo, os recursos para hospedar a função podem precisar ser criados ou reiniciados. Em algumas situações, partidas frias podem resultar em atrasos de vários segundos. O tempo de inicialização varia entre provedores e níveis de serviço. Existem algumas abordagens para abordar o tempo de inicialização se é importante minimizar para o sucesso do aplicativo.

- Alguns provedores permitem que os usuários paguem por níveis de serviço que garantem que a infra-estrutura esteja "sempre acesa".
- Implemente um mecanismo de manutenção vivo (ping o ponto final para mantê-lo "acordado").
- Use orquestração como Kubernetes com uma abordagem de função contêinerizada (o host já está funcionando, então girar novas instâncias é extremamente rápido).

## <a name="database-updates-and-migrations"></a>Atualizações e migrações de banco de dados

Uma vantagem do código sem servidor é que você pode liberar novas funções sem ter que reimplantar todo o aplicativo. Essa vantagem pode se tornar uma desvantagem quando há um banco de dados relacional envolvido. Alterações nos esquemas de banco de dados são difíceis de sincronizar com atualizações sem servidor. Desafios adicionais são colocados quando as coisas dão errado e as mudanças devem ser revertidas. A integridade dos dados é uma das razões pelas quais uma prática recomendada para microsserviços e funções sem servidor é que eles possuem seus próprios dados. É possível implantar mudanças como uma única unidade de computação e dados. A realidade é que muitos sistemas legados apresentam um grande banco de dados back-end que deve ser conciliado com a arquitetura sem servidor.

Uma abordagem popular para resolver a versão do esquema é nunca modificar propriedades e colunas existentes, mas, em vez disso, adicionar novas informações. Por exemplo, considere uma mudança para passar de uma bandeira booleana "concluída" para uma lista completa para uma "data completa". Em vez de remover o campo antigo, a alteração do banco de dados será:

1. Adicione um novo campo "data completa".
1. Transforme o campo booleano "concluído" em uma função computada que avalia se a data concluída é após a data atual.
1. Adicione um gatilho para definir a data concluída para a data atual quando o Boolean concluído estiver definido como verdadeiro.

A seqüência de alterações garante que o código legado continue a ser executado "como está", enquanto funções sem servidor mais novas podem tirar proveito do novo campo.

Para obter mais informações sobre dados em arquiteturas sem servidor, consulte [Desafios e soluções para gerenciamento de dados distribuídos](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Scaling

É um equívoco comum que sem servidor signifique "sem servidor". Na verdade, é "menos servidor". O fato de haver uma infra-estrutura de apoio é importante para entender quando se trata de dimensionamento. A maioria das plataformas sem servidor fornece um conjunto de controles para lidar com a forma como a infra-estrutura deve ser dimensionada quando a densidade de eventos aumenta. Você pode escolher entre uma variedade de opções, mas sua estratégia pode variar dependendo da função. Além disso, as funções são normalmente executadas um host relacionado, de modo que as funções no mesmo host têm as mesmas opções de escala. Portanto, é necessário organizar e traçar estratégias que as funções são hospedadas em conjunto com base nos requisitos de escala.

As regras geralmente especificam como escalar (aumentar os recursos do host) e dimensionar (aumentar o número de instâncias de host) com base em parâmetros variados. Os gatilhos para escalas podem incluir agendamento, taxas de solicitação, utilização da CPU e uso de memória. O desempenho mais alto muitas vezes tem um custo maior. As abordagens mais baratas e baseadas no consumo podem não ser dimensionadas tão rapidamente quando a taxa de solicitação aumenta repentinamente. Há uma troca entre pagar antecipadamente "custo de seguro" versus pagar estritamente "à medida que você vai" e arriscar respostas mais lentas devido a aumentos repentinos na demanda.

## <a name="monitoring-tracing-and-logging"></a>Monitoramento, rastreamento e registro

Um aspecto muitas vezes negligenciado do DevOps é monitorar aplicativos uma vez implantados. É importante ter uma estratégia para monitorar funções sem servidor. O maior desafio é muitas vezes correlação, ou reconhecer quando um usuário chama múltiplas funções como parte da mesma interação. A maioria das plataformas sem servidor permite o registro de consoles que podem ser importados para ferramentas de terceiros. Há também opções para automatizar a coleta de telemetria, gerar e rastrear IDs de correlação e monitorar ações específicas para fornecer insights detalhados. O Azure fornece a plataforma avançada [Application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) para monitoramento e análise.

## <a name="inter-service-dependencies"></a>Dependências inter-serviço

Uma arquitetura sem servidor pode incluir funções que dependem de outras funções. Na verdade, não é incomum em uma arquitetura sem servidor ter vários serviços chamados uns aos outros como parte de uma interação ou transação distribuída. Para evitar um acoplamento forte, recomenda-se que os serviços não se referenciam diretamente. Quando o ponto final de um serviço precisa ser trocado, as referências diretas podem resultar em uma grande refatoração. Uma solução sugerida é fornecer um mecanismo de descoberta de serviços, como um registro, que forneça o ponto final apropriado para um tipo de solicitação. Outra solução é aproveitar serviços de mensagens, como filas ou tópicos de comunicação entre serviços.

## <a name="managing-failure-and-providing-resiliency"></a>Gerenciar a falha e fornecer resiliência

Também é importante considerar o *padrão do disjuntor*: Se, por algum motivo, um serviço continuar falhando, não é aconselhável chamar esse serviço repetidamente. Em vez disso, um serviço alternativo é chamado ou uma mensagem retornada até que a saúde do serviço dependente seja restabelecida. A arquitetura sem servidor precisa levar em conta a estratégia de resolução e gerenciamento de dependências entre serviços.

Para continuar o padrão do disjuntor, os serviços precisam ser tolerantes a falhas e resistentes. A tolerância a falhas refere-se à capacidade do seu aplicativo de continuar a funcionar mesmo depois de exceções inesperadas ou estados inválidos serem encontrados. A tolerância a falhas é tipicamente uma função do próprio código e como ele é escrito para lidar com exceções. Resiliência refere-se ao quão capaz o aplicativo é em se recuperar de falhas. A resiliência é muitas vezes gerenciada pela plataforma sem servidor. A plataforma deve ser capaz de girar uma nova instância de função sem servidor quando a existente falhar. A plataforma também deve ser inteligente o suficiente para parar de girar novas instâncias quando cada nova instância falhar.

Para obter mais informações, consulte [Implementando o padrão do Disjuntor](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Implantações de versões e verde/azul

Um grande benefício do serverless é a capacidade de atualizar uma função específica sem ter que reimplantar todo o aplicativo. Para que as atualizações sejam bem sucedidas, as funções devem ser versidas para que os serviços que as chamam sejam encaminhados para a versão correta do código. Uma estratégia para implantar novas versões também é importante. Uma abordagem comum é usar "implantações verde/azul". A implantação verde é a função atual. Uma nova versão "azul" é implantada na produção e testada. Ao testar passes, as versões verde e azul são trocadas para que a nova versão entre ao vivo. Se algum problema for encontrado, eles podem ser trocados de volta. A versão de suporte e as implantações verde/azul exigem uma combinação de autoria das funções para acomodar alterações de versão e trabalhar com a plataforma sem servidor para lidar com implantações. Uma abordagem possível é usar proxies, que são descritos no capítulo da [plataforma sem servidor do Azure.](azure-functions.md#proxies)

>[!div class="step-by-step"]
>[Próximo](serverless-architecture.md)
>[anterior](serverless-design-examples.md)
