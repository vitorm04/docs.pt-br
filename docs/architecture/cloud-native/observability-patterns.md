---
title: Padrões de observação
description: Padrões de observação para aplicativos nativos de nuvem
ms.date: 09/23/2019
ms.openlocfilehash: 23320144c03278d631b8a1fcc1d1c0954e907296
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184872"
---
# <a name="observability-patterns"></a>Padrões de observação

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Assim como os padrões foram desenvolvidos para auxiliar no layout do código em aplicativos, há padrões para aplicativos operacionais de maneira confiável. Três padrões úteis na manutenção de aplicativos surgiram: log, monitoramento e alertas.

## <a name="when-to-use-logging"></a>Quando usar o registro em log

Não importa o cuidado que estamos, os aplicativos quase sempre se comportam de maneiras inesperadas na produção. Quando os usuários relatam problemas com um aplicativo, é extremamente útil conseguir ver o que estava acontecendo com o aplicativo quando o problema ocorreu. Uma das maneiras mais testadas e verdadeiras de capturar informações sobre o que um aplicativo está fazendo durante sua execução é fazer com que o aplicativo anote o que está fazendo. Esse processo é conhecido como registro em log. Quando ocorrem falhas ou problemas em produção, a meta deve ser reproduzir as condições sob as quais as falhas ocorreram, em um ambiente de não produção. Ter um bom registro em vigor fornece um roteiro para os desenvolvedores seguirem a fim de duplicar problemas em um ambiente que pode ser testado e experimentado.

### <a name="logging-in-cloud-native-applications"></a>Log em aplicativos nativos de nuvem

Cada linguagem de programação tem ferramentas que permitem a gravação de logs e, normalmente, a sobrecarga para a gravação desses logs é baixa. Muitas das bibliotecas de log fornecem o registro em log de diferentes tipos de criticalidades, que podem ser ajustadas em tempo de execução. Por exemplo, a biblioteca Serilog é uma biblioteca de logs estruturada popular para .NET que fornece os seguintes níveis de log

* Detalhado
* Depurar
* Informações
* Aviso
* Erro
* Fatais

Esses diferentes níveis de log fornecem granularidade no registro em log. Quando o aplicativo está funcionando corretamente na produção, ele pode ser configurado para registrar apenas mensagens importantes. Quando o aplicativo está com comportamento inadequado, o nível de log pode ser aumentado para que logs mais detalhados sejam coletados. Isso equilibra o desempenho contra a facilidade de depuração.

O alto desempenho das ferramentas de log e o tunability de detalhes deve incentivar os desenvolvedores a registrarem com frequência. Muitos favorecem um padrão de registrar a entrada e sair de cada método. Essa abordagem pode parecer um exagero, mas não é freqüente que os desenvolvedores desejarão ter menos registro em log. Na verdade, não é incomum executar implantações para a única finalidade de adicionar o registro em log em um método problemático. Erro no lado de um excesso de logs e não há muito pouco. Observe que algumas ferramentas podem ser usadas para fornecer automaticamente esse tipo de registro em log.

Em aplicativos tradicionais, os arquivos de log normalmente eram armazenados no computador local. Na verdade, em sistemas operacionais semelhantes ao Unix, há uma estrutura de pastas definida para manter todos os logs, normalmente `/var/log`sob. A utilidade de fazer logon em um arquivo simples em um único computador é amplamente reduzida em um ambiente de nuvem. Os aplicativos que produzem logs podem não ter acesso ao disco local ou o disco local pode ser altamente transitório, pois os contêineres são embaralhados em relação a computadores físicos.

Aplicativos nativos de nuvem desenvolvidos usando uma arquitetura de microservices também apresentam alguns desafios para agentes baseados em arquivo. As solicitações de usuário agora podem abranger vários serviços que são executados em computadores diferentes e podem incluir funções sem acesso a um sistema de arquivos local. Seria muito desafiador correlacionar os logs de um usuário ou uma sessão entre esses vários serviços e máquinas.

Por fim, o número de usuários em alguns aplicativos nativos de nuvem é alto. Imagine que cada usuário gere uma centena de linhas de mensagens de log ao fazer logon em um aplicativo. Em isolamento, isso é gerenciável, mas multiplique mais de 100.000 usuários e o volume de logs se torna grande.

Felizmente, há algumas alternativas fantásticas para o uso do registro em log baseado em sistema de arquivos. Um servidor de log centralizado para o qual todos os logs são enviados, corrige todos esses problemas. Os logs são coletados pelos aplicativos e enviados para um aplicativo de log central que indexa e armazena os logs. Essa classe de sistema pode incluir dezenas de gigabytes de logs todos os dias.

Também é útil seguir algumas práticas padrão ao criar logs que abrangem muitos serviços. Por exemplo, a geração de uma [ID de correlação](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) no início de uma interação demorada e, em seguida, o registro em cada mensagem relacionada a essa interação, facilita a pesquisa de todas as mensagens relacionadas. Só é necessário localizar uma única mensagem e extrair a ID de correlação para localizar todas as mensagens relacionadas. Outro exemplo é garantir que o formato de log seja o mesmo para todos os serviços, seja qual for o idioma ou a biblioteca de log que ele usa. Essa padronização torna muito mais fácil a leitura de logs. A Figura 7-1 demonstra como uma arquitetura de microserviços pode aproveitar o registro em log centralizado como parte de seu fluxo de trabalho.

![Os logs de várias fontes são incluídos em um repositório de logs centralizado. **Figura 7-1**. ](./media/centralized-logging.png)
 Os logs de várias fontes são incluídos em um repositório de logs centralizado.

## <a name="when-to-use-monitoring"></a>Quando usar o monitoramento

Alguns aplicativos não são de missão crítica. Talvez eles sejam usados apenas internamente e, quando ocorrer um problema, o usuário possa entrar em contato com a equipe responsável e o aplicativo possa ser reiniciado. No entanto, os clientes geralmente têm mais expectativas para os aplicativos que consomem. Se você precisar saber quando ocorrem problemas com seu aplicativo *antes que* os usuários façam, ou antes que os usuários o notifiquem, você precisa monitorar seu estado atual. Implementado corretamente, o monitoramento pode informá-lo sobre condições que resultarão em problemas, permitindo que você resolva as condições subjacentes antes que elas resultem em qualquer impacto no usuário.

## <a name="monitoring-considerations"></a>Considerações sobre monitoramento

Alguns sistemas de registro em log centralizados assumem uma função adicional de coleta de telemetria fora de logs puros. Eles podem coletar métricas, como tempo para executar uma consulta de banco de dados, tempo médio de resposta de um servidor Web e até mesmo médias de carga de CPU e pressão de memória, conforme relatado pelo sistema operacional. Em conjunto com os logs, esses sistemas podem fornecer uma visão holística da integridade dos nós no sistema e do aplicativo como um todo.

Os recursos de coleta de métrica das ferramentas de monitoramento também podem ser alimentados manualmente de dentro do aplicativo. Os fluxos de negócios que são de interesse particular, como novos usuários se inscrevendo ou encomendando, podem ser instrumentados de forma que eles incrementam um contador no sistema de monitoramento central. Isso desbloqueia as ferramentas de monitoramento para não apenas monitorar a integridade do aplicativo, mas a integridade dos negócios.

As consultas podem ser construídas nas ferramentas de agregação de log para procurar determinadas estatísticas ou padrões, que podem ser exibidas em formato gráfico, em painéis personalizados. Frequentemente, as equipes investirão em grandes exibições com montagem de parede que giram pelas estatísticas relacionadas a um aplicativo. Dessa forma, é simples Ver os problemas conforme eles ocorrem.

## <a name="when-to-use-alerts"></a>Quando usar alertas

Se você precisar reagir a problemas com seu aplicativo, precisará de alguma maneira de alertar o pessoal certo. Esse é o terceiro padrão de observação do aplicativo de nuvem nativa e depende do registro em log e do monitoramento. Seu aplicativo precisa ter o registro em log para permitir que os problemas sejam diagnosticados e, em alguns casos, alimentar a ferramentas de monitoramento. Ele precisa de monitoramento para agregar dados de integridade e métricas de aplicativo em um único lugar. Depois que isso tiver sido estabelecido, poderão ser criadas regras que dispararão alertas quando determinadas métricas ficarem fora dos níveis aceitáveis.

## <a name="alerts"></a>Alertas

Você pode criar consultas em relação às ferramentas de monitoramento para procurar condições de falha conhecidas. Por exemplo, as consultas podem pesquisar nos logs de entrada as indicações do código de status HTTP 500, que indica um problema em um servidor Web. Assim que um deles é detectado, um email ou um SMS pode ser enviado para o proprietário do serviço de origem que pode começar a investigar.

Normalmente, um único erro 500 não é suficiente para determinar se ocorreu um problema. Isso pode significar que um usuário digitou sua senha incorretamente ou inseriu alguns dados malformados. As consultas de alerta podem ser criadas para serem acionadas apenas quando um número médio maior que 500 erros forem detectados.

Um dos padrões mais prejudiciais no alerta é acionar muitos alertas para que os seres humanos investiguem. Os proprietários de serviço se tornarão rapidamente dessensibilizamos a erros que foram previamente investigados e considerados benignos. Quando ocorrerem erros verdadeiros, eles serão perdidos no ruído de centenas de falsos positivos. O Parable do [rapaz que chorei Wolf](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) é frequentemente dito a crianças para avisá-los dessa grande perigo. É importante garantir que os alertas que são acionados sejam indícios de um problema real.

>[!div class="step-by-step"]
>[Anterior](monitoring-health.md)
>[Próximo](logging-with-elastic-stack.md)
