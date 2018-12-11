---
title: Considerações de arquitetura sem servidor - aplicativos sem servidor
description: Compreenda os desafios da arquitetura de aplicativos sem servidor, do gerenciamento de estado e o armazenamento persistente para dimensionar, registro em log, rastreamento e diagnóstico.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b12a09c0fcef7e7ff954a3f959fb9e3080a6e859
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155058"
---
# <a name="serverless-architecture-considerations"></a>Considerações sobre a arquitetura sem servidor

Adotar uma arquitetura sem servidor vêm com determinados desafios. Essa seção explora algumas das considerações mais comuns a serem consideradas. Todos esses desafios têm soluções. Assim como acontece com todas as opções de arquitetura, a decisão para operar sem servidor deve ser feita somente após considerar cuidadosamente os prós e contras. Dependendo das necessidades do seu aplicativo, você pode decidir por que uma implementação sem servidor não é a solução certa para determinados componentes.

## <a name="managing-state"></a>Gerenciamento de estado

Funções sem servidor, assim como acontece com microsserviços em geral, são sem monitoração de estado por padrão. Evitando estado permite que sem servidor efêmera para escalar horizontalmente e oferecer resiliência sem um ponto central de falha. Em algumas circunstâncias, os processos de negócios exigem estado. Se o processo requer que o estado, você terá duas opções. Você pode adotar um modelo diferente sem servidor, ou interagir com um serviço separado que fornece o estado. Adicionar o estado pode complicar a solução e dificultam a escala e possivelmente criar um ponto único de falha. Considere cuidadosamente se sua função requer absolutamente de estado. Se a resposta for "Sim", determine se ele ainda faz sentido para implementá-lo com sem servidor.

Há várias soluções para adotar o estado sem comprometer os benefícios do uso sem servidor. Algumas das soluções mais populares incluem:

* Usar um repositório de dados temporários ou cache distribuído, como o Redis
* Estado da Store em um banco de dados, como SQL ou cosmos DB
* Lidar com estado por meio de um mecanismo de fluxo de trabalho, como as funções duráveis

O resultado final é que você deve estar ciente da necessidade de qualquer gerenciamento de estado dentro de processos que você está pensando em implementar com sem servidor.

## <a name="long-running-processes"></a>Processos de longa execução

Muitos benefícios do uso sem servidor contam com os processos que estão sendo efêmero. Tempos de execução curtos tornam mais fácil para o provedor sem servidor liberar recursos, como as funções funções end e o compartilhamento entre hosts. A maioria dos provedores de nuvem limitar o tempo total que sua função pode ser executado para cerca de 10 minutos. Se o processo pode levar mais tempo, você pode considerar uma implementação alternativa.

Há algumas exceções e soluções. Uma solução pode ser interromper o processo em componentes menores que individualmente levam menos tempo para ser executado. Se a execução do processo longa devido a dependências, você também pode considerar um fluxo de trabalho assíncrono usando uma solução, como as funções duráveis. As funções duráveis pausam e mantêm o estado de seu processo enquanto ele estiver aguardando em um processo externo para concluir. A manipulação assíncrona reduz o tempo que o processo real é executado.

## <a name="startup-time"></a>Tempo de inicialização

Um problema potencial com implementações sem servidor é o tempo de inicialização. Para conservar os recursos, muitos provedores sem servidor criam infraestrutura "sob"demanda. Quando uma função sem servidor é disparada após um período de tempo, os recursos para hospedar a função talvez precise ser criado ou reiniciado. Em algumas situações, inicializações a frio podem resultar em atrasos de alguns segundos. Tempo de inicialização varia de acordo com os provedores e os níveis de serviço. Há algumas abordagens para o tempo de inicialização de endereço se for importante minimizar a para o sucesso do aplicativo.

* Alguns provedores de permitir que os usuários de pagamento para níveis de serviço que garantem a infraestrutura é "always on".
* Implemente um mecanismo keep-alive (ping o ponto de extremidade para mantê-lo "ativos").
* Use a orquestração, como Kubernetes com uma abordagem de função em contêineres (o host já está em execução para que novas instâncias de bagunçar é extremamente rápido).

## <a name="database-updates-and-migrations"></a>Migrações e atualizações de banco de dados

Uma vantagem de código sem servidor é que você pode liberar as novas funções sem precisar reimplantar o aplicativo inteiro. Essa vantagem pode se tornar uma desvantagem quando um banco de dados relacional está envolvido. Alterações em esquemas de banco de dados são difíceis de sincronizar com atualizações sem servidor. Desafios adicionais são impostos quando as coisas dão errado, e as alterações devem ser revertidas. Integridade dos dados é um dos motivos que uma prática recomendada para microsserviços e funções sem servidor é que eles possuem seus próprios dados. É possível implantar as alterações como uma única unidade de computação e de dados. A realidade é que muitos sistemas herdados apresentam um grande banco de dados back-end que deve ser reconciliado com a arquitetura sem servidor.

Uma abordagem popular para resolver o controle de versão do esquema é nunca modifique as propriedades existentes e colunas, mas em vez disso, adicionar novas informações. Por exemplo, considere uma alteração para mover de um valor booliano "concluído" Sinalizador para obter uma lista de tarefas pendentes para uma "data de conclusão". Em vez de remover o campo antigo, a alteração do banco de dados será:

1. Adicione um campo novo "Data da conclusão".
1. Transforme o campo booliano "concluído" para uma função computada que avalia se a data de conclusão é posterior à data atual.
1. Adicionar um gatilho para definir a data de conclusão para a data atual quando o booliano concluído é definido como true.

A sequência das alterações garante que o código herdado continua em execução "como está", enquanto as funções sem servidor mais recentes podem tirar proveito do novo campo.

Para obter mais informações sobre dados em arquiteturas sem servidor, consulte [desafios e soluções de gerenciamento de dados de distribuídos](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Dimensionamento

É um equívoco comum que, sem servidor significa "sem servidor". Na verdade, é "menor servidor". Há o fato é que uma infraestrutura de backup é importante entender quando se trata de dimensionamento. Plataformas sem servidor mais fornecem um conjunto de controles para manipular como a infraestrutura deve ser dimensionado quando o evento densidade aumenta. Você pode escolher entre uma variedade de opções, mas sua estratégia pode variar dependendo da função. Além disso, funções normalmente são executadas em um host relacionado, para que as funções no mesmo host têm as mesmas opções de escala. Portanto, é necessário organizar e desenvolver uma estratégia funções que são hospedadas juntos com base nos requisitos de dimensionamento.

As regras geralmente especificam como escalar verticalmente (aumentar os recursos de host) e expandir (aumentar o número de instâncias de host) com base nos parâmetros diferentes. Gatilhos para escalas podem incluir o uso de memória, taxas de solicitação, utilização da CPU e agendamento. Maior desempenho geralmente tem um custo maior. As abordagens mais baratas, baseado em consumo não podem dimensionar à medida que quando a taxa de solicitação, de repente, aumenta rapidamente. Há uma compensação entre pagando com antecedência "custo seguro" em vez de pagar estritamente "que você acesse" e arriscar respostas mais lentas devido a aumentos repentinos na demanda.

## <a name="monitoring-tracing-and-logging"></a>Registro em log, rastreamento e monitoramento

Uma vez implantados de aplicativos de monitoramento é geralmente um aspecto desconsiderado do DevOps. É importante ter uma estratégia para o monitoramento de funções sem servidor. O maior desafio que muitas vezes é correlação ou reconhecer quando um usuário chama várias funções como parte da mesma interação. Plataformas sem servidor mais permitem que o console de log que pode ser importado para ferramentas de terceiros. Também há opções para automatizar a coleta de telemetria, gerar e acompanhar as IDs de correlação e monitorar as ações específicas para fornecer informações detalhadas. O Azure fornece o avançado [plataforma do Application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) para monitoramento e análise.

## <a name="inter-service-dependencies"></a>Dependências entre serviços

Uma arquitetura sem servidor pode incluir funções que dependem de outras funções. Na verdade, não é incomum em uma arquitetura sem servidor tenha vários serviços chamam uns aos outros como parte de uma interação ou a transação distribuída. Para evitar acoplamento forte, é recomendável que os serviços não referenciam entre si diretamente. Quando o ponto de extremidade para um serviço precisa alterar, referências diretas pode resultar na refatoração principais. Uma sugestão de solução é fornecer um mecanismo de descoberta de serviço, como um registro, que fornece o ponto de extremidade apropriado para um tipo de solicitação. Outra solução é utilizar serviços de mensagens como filas ou tópicos para a comunicação entre serviços.

## <a name="managing-failure-and-providing-resiliency"></a>Gerenciamento de falhas e fornecendo resiliência

Também é importante considerar as *padrão de disjuntor*: Se, por algum motivo, um serviço continua a falhar, não é aconselhável para chamar esse serviço repetidamente. Em vez disso, um serviço alternativo é chamado ou uma mensagem retornada até que a integridade do serviço dependente seja restabelecida. A arquitetura sem servidor precisa levar em conta a estratégia para resolver e gerenciamento de dependências entre serviços.

Para continuar o padrão de Disjuntor, serviços precisam ser tolerante a falhas e resiliente. Tolerância refere-se à capacidade de seu aplicativo para continuar executando mesmo após exceções inesperadas ou estados inválidos são encontrados. Tolerância a falhas normalmente é uma função do próprio código e como ele escreveu lidar com exceções. Resiliência se refere a como compatíveis com o aplicativo está em recuperação de falhas. Resiliência geralmente é gerenciada pela plataforma sem servidor. A plataforma deve conseguir crie uma nova instância de função sem servidor quando existente falha. A plataforma também deve ser inteligente o bastante para parar de girar novas instâncias quando a falha de cada nova instância.

Para obter mais informações, consulte [Implementando o padrão de disjuntor](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Implantações de controle de versão e verde/azul

Uma grande vantagem do uso sem servidor é a capacidade de atualizar uma função específica sem precisar reimplantar o aplicativo inteiro. Para atualizações para ser bem-sucedido, funções devem ser com controle de versão para que os serviços de chamá-los são roteados para a versão correta do código. Uma estratégia de implantação de novas versões também é importante. Uma abordagem comum é usar "verde/azul implantações." A implantação verde é a função atual. Uma nova versão de "blue" é implantada para produção e testada. Quando o teste é aprovado, as versões de verdes e azuis são trocadas para que a nova versão é fornecido em tempo real. Se ocorrerem problemas, eles podem ser trocados novamente. Suporte a controle de versão e implantações de verde/azul requer uma combinação de criação de funções para acomodar as alterações de versão e trabalhar com a plataforma sem servidor para lidar com implantações. Uma abordagem possível é usar proxies, que são descritos na [plataforma sem servidor do Azure](azure-functions.md#proxies) capítulo.

>[!div class="step-by-step"]
>[Anterior](serverless-architecture.md)
>[Próximo](serverless-design-examples.md)