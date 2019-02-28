---
title: 'Usando F# no Azure'
description: 'Guia para o uso de serviços do Azure comF#'
author: sylvanc
ms.date: 09/22/2016
---
# <a name="using-f-on-azure"></a>Usando F# no Azure

F# é uma excelente linguagem para programação em nuvem e é usada com frequência para escrever aplicativos da Web, serviços de nuvem, microsserviços hospedados em nuvem e para processamento de dados escalonável.

As seções a seguir contêm recursos sobre como usar vários serviços com F#.

> [!NOTE]
> Se um serviço específico do Azure não estiver neste conjunto de documentações, veja a documentação do Azure Functions ou do .NET sobre esse serviço. Alguns serviços do Azure são independentes da linguagem e não exigem documentação específica à linguagem e não estão listados aqui.

## <a name="using-azure-virtual-machines-with-f"></a>Como usar máquinas virtuais do Azure com F\#

O Azure oferece suporte a várias configurações de VM (máquina virtual), veja [Máquinas virtuais Linux e Azure](https://azure.microsoft.com/services/virtual-machines/).

Para instalar F# em uma máquina virtual para execução, compilação e/ou geração de script, veja [Como usar F# no Linux](https://fsharp.org/use/linux) e [Como usar F# no Windows](https://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>Usando o Azure Functions com F\#

[Azure Functions](https://azure.microsoft.com/services/functions/) é uma solução para execução facilitada de pequenas partes de código, ou "funções", na nuvem. Você pode escrever apenas o código necessário para o problema atual, sem se preocupar com todo o aplicativo ou com a infraestrutura para executá-lo. As funções são conectadas a eventos no Armazenamento do Azure e a outros recursos hospedados na nuvem. Os dados fluem para suas funções em F# por meio de argumentos da função. Você pode usar a linguagem de desenvolvimento preferida, confiando no Azure para escalar conforme necessário.

O Azure Functions oferece suporte a F# como uma linguagem de primeira classe com execução eficiente, reativa e dimensionável do código F#. Consulte [Referência do desenvolvedor em F# do Azure Functions](/azure/azure-functions/functions-reference-fsharp) para obter uma documentação de referência sobre como usar F# com o Azure Functions.

Outros recursos para usar o Azure Functions e F#:

* [Dimensionar o Azure Functions em F# usando Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Como criar função do Azure em F#](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Usando o provedor de tipos do Azure com o Azure Functions](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>Usar o armazenamento do Azure com F\#

O Armazenamento do Azure é uma camada base de serviços de armazenamento para aplicativos modernos que dependem de durabilidade, disponibilidade e escalabilidade para atender às necessidades dos clientes. F#programas podem interagir diretamente com os serviços de armazenamento do Azure, usando as técnicas descritas nos artigos a seguir.

* [Introdução ao armazenamento de Blobs do Azure usando F#](blob-storage.md)
* [Introdução ao armazenamento de Arquivos do Azure usando F#](file-storage.md)
* [Introdução ao armazenamento de Filas do Azure usando F#](queue-storage.md)
* [Introdução ao armazenamento de Tabelas do Azure usando F#](table-storage.md)

O Armazenamento do Azure também pode ser usado em conjunto com o Azure Functions por meio de configuração declarativa em vez de chamadas de API explícitas. Consulte [Gatilhos e associações do Azure Functions para Armazenamento do Azure](/azure/azure-functions/functions-bindings-storage) que inclui exemplos de F#.

## <a name="using-azure-app-service-with-f"></a>Usar o serviço de aplicativo do Azure com F\#

[Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/) é uma plataforma de nuvem para compilação de aplicativos Web e móveis avançados que se conectam aos dados em qualquer lugar, na nuvem ou localmente.

* [Exemplo de API Web do Azure em F#](https://github.com/fsprojects/azure-webapi-example)
* [Como hospedar F# em um aplicativo Web no Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Como usar o Apache Spark com F# com o Azure HDInsight

[Apache Spark para Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) é uma estrutura de processamento de código-fonte aberto que executa aplicativos de análise de dados em larga escala. O Azure torna o Apache Spark fácil e barato de implantar. Desenvolva seu aplicativo Spark em F# usando [Mobius](https://github.com/Microsoft/Mobius), uma API do .NET para Spark.

* [Implementar aplicativos Spark em F# usando Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Exemplo de aplicativos Spark em F# usando Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>Usar o Azure Cosmos DB com F\#

[O Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) é um serviço do NoSQL para aplicativos altamente disponíveis e distribuídos globalmente.

O Azure Cosmos DB pode ser usado com F# de duas maneiras:

1. Durante a criação de F# Azure Functions que reagir a ou fazer com que as alterações nas coleções do Azure Cosmos DB. Ver [associações do Azure Cosmos DB para o Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), ou
2. Usando o [SDK .NET do Azure Cosmos DB para API do SQL](/azure/cosmos-db/sql-api-sdk-dotnet). Os exemplos relacionados estão em c#.

## <a name="using-azure-event-hubs-with-f"></a>Usar os Hubs de eventos do Azure com F\#

[Os Hubs de Evento do Azure](https://azure.microsoft.com/services/event-hubs/) fornecem ingestão de telemetria de escala de nuvem a partir de sites, aplicativos e dispositivos.

Os Hubs de Eventos do Azure podem ser usados com F# de duas maneiras:

1. Durante a criação de Azure Functions em F# que são disparadas por eventos. Consulte [Gatilhos do Azure Function para Hub de Eventos](/azure/azure-functions/functions-bindings-event-hubs), ou
2. Usando o [SDK do .NET para Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Observe que esses exemplos estão em C#.

## <a name="using-azure-notification-hubs-with-f"></a>Usar os Hubs de notificação do Azure com F\#

[Os Hubs de Notificação do Azure](/azure/notification-hubs/) são infraestruturas de push multiplataforma e expansíveis que permitem que você envie notificações por push de qualquer back-end (na nuvem ou local) para qualquer plataforma móvel.

Os Hubs de Notificação do Azure podem ser usados com F# de duas maneiras:

1. Durante a criação de Azure Functions em F# que enviam resultados para um hub de notificação. Consulte [Gatilhos de saída do Azure Function para Hubs de Notificação](/azure/azure-functions/functions-bindings-notification-hubs), ou
2. Usando o [SDK do .NET para Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Observe que esses exemplos estão em C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implementação de WebHooks no Azure com F\#

Um [Webhook](https://en.wikipedia.org/wiki/Webhook) é um retorno de chamada disparado por meio de uma solicitação da Web. os Webhooks são usados por sites, como o GitHub, para eventos de sinal. 

Os Webhooks podem ser implementados em F# e hospedados no Azure por meio de um [Azure Function em F# com uma associação de Webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>Como usar Webjobs com F\#

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) são programas que você pode executar em seu aplicativo da Web de Serviço de aplicativo de três maneiras: sob demanda, continuamente ou com agendamento.

[Exemplo do Webjob do F#](https://github.com/jrr/webjob-project-examples)

## <a name="implementing-timers-on-azure-with-f"></a>Implementação de temporizadores no Azure com F\#

O temporizador dispara funções de chamada com base em uma agenda, uma única vez ou de forma recorrente.

Os temporizadores podem ser implementados em F# e hospedados no Azure por meio de um [Azure Function em F# com um gatilho de temporizador](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Implantação e gerenciamento de recursos do Azure com scripts em F#

As VMs do Azure podem ser implantadas e gerenciadas programaticamente a partir de scripts em F# usando as APIs e o Microsoft.Azure.Management. Por exemplo, veja [Introdução às bibliotecas de gerenciamento para .NET](https://msdn.microsoft.com/library/dn722415.aspx) e [Como usar o Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

Da mesma forma, os outros recursos do Azure também podem ser implantados e gerenciados a partir de scripts em F# usando os mesmos componentes. Por exemplo, você pode criar contas de armazenamento, implantar serviços de nuvem do Azure, criar instâncias do Azure Cosmos DB e gerenciar Hubs de notificação do Azure por meio de programação do F# scripts.

O uso de scripts em F# para implantar e gerenciar recursos não é necessário normalmente. Por exemplo, os recursos do Azure também podem ser implantados diretamente de descrições de modelo JSON, que podem ser parametrizadas. Confira [Modelos do Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices) incluindo exemplos como os [Modelos de início rápido do Azure](https://azure.microsoft.com/resources/templates/).

## <a name="other-resources"></a>Outros recursos

* [Documentação completa sobre todos os serviços do Azure](/azure/)
