---
title: "Esquema de base de dados de persistência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc758f85b4f8b0bec5c00979f42d3f7b2ea7b182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-database-schema"></a>Esquema de base de dados de persistência
Este tópico descreve as visualizações públicas suportadas por instância Store de fluxo de trabalho SQL.  
  
## <a name="instances-view"></a>O modo de instâncias  
 O **instâncias** exibição contém informações gerais sobre todas as instâncias de fluxo de trabalho no banco de dados.  
  
|Nome da coluna|Tipo de coluna|Descrição|  
|-----------------|-----------------|-----------------|  
|InstanceId|UniqueIdentifier|A identificação de uma instância de fluxo de trabalho.|  
|PendingTimer|DateTime|Indica que o fluxo de trabalho está bloqueado em uma atividade do atraso e continuado será depois que o timer expirar. Esse valor pode ser zero se o fluxo de trabalho não é espera com barreira na um timer expirar.|  
|CreationTime|DateTime|Indica quando o fluxo de trabalho foi criado.|  
|LastUpdatedTime|DateTime|Indica a última vez que o fluxo de trabalho foi persistente a base de dados.|  
|ServiceDeploymentId|BigInt|Atua como uma chave estrangeira para modo de ServiceDeployments []. Se a instância atual de fluxo de trabalho é uma instância de um serviço web hospedado, então essa coluna tem um valor, se não estiver definida PARA ANULAR.|  
|SuspensionExceptionName|Nvarchar(450)|Indica o tipo de exceção (por exemplo, InvalidOperationException) que fez com que o fluxo de trabalho Suspender.|  
|SuspensionReason|Nvarchar (máximo)|Indica como a instância de fluxo de trabalho foi suspendida. Se uma exceção causou a instância suspende, então essa coluna contém a mensagem associada com a exceção.<br /><br /> Se a instância foi suspendida manualmente, então essa coluna contém a razão especificada pelo usuário para suspender a instância.|  
|ActiveBookmarks|Nvarchar (máximo)|Se a instância de fluxo de trabalho estiver ocioso, essa propriedade indica que indicadores a instância é bloqueada sobre. Se a instância não estiver ocioso, então essa coluna é NULA.|  
|CurrentMachine|nvarchar (128)|Indica que o nome do computador atualmente tem a instância de fluxo de trabalho carregado na memória.|  
|LastMachine|Nvarchar(450)|Indica o computador o último que carregou a instância de fluxo de trabalho.|  
|ExecutionStatus|Nvarchar(450)|Indica o estado atual de execução de fluxo de trabalho. Os estados possíveis incluem **executando**, **ocioso**, **fechado**.|  
|IsInitialized|Bit|Indica se a instância de fluxo de trabalho foi inicializada. Uma instância inicializada de fluxo de trabalho é uma instância de fluxo de trabalho que é mantido pelo menos uma vez.|  
|IsSuspended|Bit|Indica se a instância de fluxo de trabalho foi suspendida.|  
|IsCompleted|Bit|Indica se a instância de fluxo de trabalho terminou de executar. **Observação:** Iif o **InstanceCompletionAction** está definida como **DeleteAll**, as instâncias são removidas da exibição após a conclusão.|  
|EncodingOption|TinyInt|Descreve a codificação usada para serializar as propriedades de dados.<br /><br /> -0 – sem codificação<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary (máximo)|Contém serializou as propriedades de dados de instância que serão fornecidos de volta para o tempo de execução de fluxo de trabalho que a instância é carregada.<br /><br /> Cada propriedade primitiva é um tipo nativo de CLR, o que significa que qualquer conjunto especial é necessário para desserializar a operação.|  
|WriteOnlyPrimitiveDataProperties|Varbinary (máximo)|Contém serializou as propriedades de dados de instância que não são fornecidas de volta para o tempo de execução de fluxo de trabalho que a instância é carregada.<br /><br /> Cada propriedade primitiva é um tipo nativo de CLR, o que significa que qualquer conjunto especial é necessário para desserializar a operação.|  
|ReadWriteComplexDataProperties|Varbinary (máximo)|Contém serializou as propriedades de dados de instância que serão fornecidos de volta para o tempo de execução de fluxo de trabalho que a instância é carregada.<br /><br /> Desserialização um exigiria conhecimento de todos os tipos de objeto armazenados nesta operação.|  
|WriteOnlyComplexDataProperties|Varbinary (máximo)|Contém serializou as propriedades de dados de instância que não são fornecidas de volta para o tempo de execução de fluxo de trabalho que a instância é carregada.<br /><br /> Desserialização um exigiria conhecimento de todos os tipos de objeto armazenados nesta operação.|  
|IdentityName|Nvarchar (máximo)|O nome da definição de fluxo de trabalho.|  
|IdentityPackage|Nvarchar (máximo)|Informações de pacote fornecida quando o fluxo de trabalho foi criado (como o nome assembly).|  
|Build|BigInt|O número de compilação de versão de fluxo de trabalho.|  
|Principal|BigInt|O número de versão principal de fluxo de trabalho.|  
|Secundário|BigInt|O menor número de versão de fluxo de trabalho.|  
|Revisão|BigInt|O número de revisão de versão de fluxo de trabalho.|  
  
> [!CAUTION]
>  O **instâncias** exibição também contém um gatilho Delete. Os usuários com as permissões apropriadas podem executar instruções de exclusão nesta exibição que removerá vigorosa as instâncias de fluxo de trabalho de base de dados. Recomendamos excluir diretamente de exibição somente como um recurso o último como excluir uma instância sob o tempo de execução de fluxo de trabalho pode levar a consequências não intencionais. Em vez disso, use o ponto final de gerenciamento de instância de fluxo de trabalho para que o tempo de execução de fluxo de trabalho finalizar a instância. Se você deseja excluir um grande número de instâncias de exibição, certifique-se de que não há nenhum tempo de execução ativa que pode operar nessas instâncias.  
  
## <a name="servicedeployments-view"></a>O modo de ServiceDeployments  
 O **ServiceDeployments** exibição contém informações de implantação para todos os Web (IIS / WAS) serviços de fluxo de trabalho hospedados. Cada instância de fluxo de trabalho que está hospedado na Web irá conter uma **ServiceDeploymentId** que se refere a uma linha nesta exibição.  
  
|Nome da coluna|Tipo de coluna|Descrição|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|A chave primária para esta exibição.|  
|SiteName|Nvarchar (máximo)|Representa o nome do site que contém o serviço de fluxo de trabalho (por exemplo, **Default Web Site**).|  
|RelativeServicePath|Nvarchar (máximo)|Representa o caminho virtual relativo ao site da web que aponta para o serviço de fluxo de trabalho. (por exemplo  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|Nvarchar (máximo)|Representa o caminho virtual relativo ao site da web que aponta para um aplicativo que contém o serviço de fluxo de trabalho. (por exemplo, **/app1**).|  
|ServiceName|Nvarchar (máximo)|Representa o nome do serviço de fluxo de trabalho. (por exemplo, **PurchaseOrderService**).|  
|ServiceNamespace|Nvarchar (máximo)|Representa o namespace do serviço de fluxo de trabalho. (por exemplo, **MyCompany**).|  
  
 O modo de ServiceDeployments também contém um disparador de exclusão. Os usuários com as permissões apropriadas podem executar instruções de exclusão nesta exibição para remover entradas de ServiceDeployment de base de dados. Observe que:  
  
1.  Excluir entradas desta exibição é grande desde que o base de dados inteiro deve ser bloqueado antes de executar esta operação. Isso é necessário para evitar o cenário onde uma instância de fluxo de trabalho pode referir-se a uma entrada inexistente de ServiceDeployment. Excluir desta exibição somente durante o tempo de inatividade/janelas de aplicativos.  
  
2.  Qualquer tentativa de excluir uma linha de ServiceDeployment que faz referência a entradas na **instâncias** exibição resultará em uma não-operacional. Você só pode excluir linhas de ServiceDeployment com referências zero.  
  
## <a name="instancepromotedproperties-view"></a>O modo de InstancePromotedProperties  
 O **InstancePromotedProperties** exibição contém informações para todas as propriedades promovidas que são especificados pelo usuário. Uma propriedade promovida funciona como uma propriedade de primeira classe, que um usuário possa usar em consultas para recuperar instâncias.  Por exemplo, um usuário pode adicionar uma promoção de PurchaseOrder que sempre armazena o custo de um pedido no **Value1** coluna. Isso deve permitir um usuário para consultar todos os pedidos de compra cujos custo exceder qualquer valor.  
  
|Tipo de coluna|Tipo de coluna|Descrição|  
|-|-|-|  
|InstanceId|UniqueIdentifier|A identificação de instância de fluxo de trabalho|  
|EncodingOption|TinyInt|Descreve a codificação usada para serializar as propriedades binários elevadas.<br /><br /> -0 – sem codificação<br />-1 – GZipStream|  
|PromotionName|Nvarchar (400)|O nome da promoção associada com essa instância. O PromotionName é necessário para adicionar contexto para colunas genéricos nesta linha.<br /><br /> Por exemplo, um PromotionName de PurchaseOrder pode indicar que o valor1 contém os custos de ordem, valor2 contém o nome do cliente que fez o pedido, valor 3 contém o endereço de cliente, e assim por diante.|  
|Valor [1-32]|SqlVariant|O valor [] 1-32 contém os valores que podem ser armazenados em uma coluna de SqlVariant. Uma única promoção não pode conter mais de 32 SqlVariants.|  
|Valor [33-64]|Varbinary (máximo)|O valor [] 33-64 contém valores serializados. Por exemplo, Value33 pode conter JPEG de um item que está sendo comprado. Uma única promoção não pode conter mais de 32 propriedades binários|  
  
 O modo de InstancePromotedProperties é limite do esquema, o que significa que os usuários podem adicionar índices em uma ou mais colunas para otimizar consultas nesta exibição.  
  
> [!NOTE]
>  Uma exibição indexada requer mais armazenamento e adicione a sobrecarga adicional de processamento. Consulte [melhorando o desempenho com exibições indexadas do SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=179529) para obter mais informações.
