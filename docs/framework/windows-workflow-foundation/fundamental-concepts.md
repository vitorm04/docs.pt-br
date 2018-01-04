---
title: Conceitos fundamentais de fluxo de trabalho do Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca570f661b1867737cc3af295aff5fd8d4cd5ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="fundamental-windows-workflow-concepts"></a>Conceitos fundamentais de fluxo de trabalho do Windows
Desenvolvimento de fluxo de trabalho nos conceitos dos usos de [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] que podem ser novos a alguns desenvolvedores. Este tópico descreve alguns dos conceitos e como eles são implementados.  
  
## <a name="workflows-and-activities"></a>Fluxos de trabalho e atividades  
 Um fluxo de trabalho é uma coleção estruturada de ações que modela um processo. Cada ação no fluxo de trabalho é modelada como uma atividade. Um host interage com um fluxo de trabalho usando <xref:System.Activities.WorkflowInvoker> para chamar um fluxo de trabalho como se fosse um método, <xref:System.Activities.WorkflowApplication> para o controle explícito sobre a execução de uma única instância de fluxo de trabalho, e <xref:System.ServiceModel.WorkflowServiceHost> para interações mensagem- com base em cenários de várias instâncias. Porque as etapas de fluxo de trabalho são definidas como uma hierarquia de atividades, a atividade o nível mais alto na hierarquia pode ser determina definir o fluxo de trabalho propriamente dito. Esse modelo de hierarquia toma o lugar de `SequentialWorkflow` e classes explícitos de `StateMachineWorkflow` versões anteriores. As atividades elas mesmas são desenvolvidas como coleções de outras atividades (usando a classe de <xref:System.Activities.Activity> como uma base, geralmente definidas usando XAML) ou são normalmente criado usando a classe de <xref:System.Activities.CodeActivity> , que pode usar o tempo de execução para acesso a dados, ou usando a classe de <xref:System.Activities.NativeActivity> , que expõe a largura de fluxo de trabalho para o autor de atividade. As atividades desenvolvidas utilizando <xref:System.Activities.CodeActivity> e <xref:System.Activities.NativeActivity> são criados usando linguagens compatíveis CLR- como C#.  
  
## <a name="activity-data-model"></a>Modelo de dados de atividades  
 As atividades armazenam e compartilham dados usando os tipos mostrados na tabela a seguir.  
  
|||  
|-|-|  
|Variável|Armazena dados em uma atividade.|  
|Argumento|Dados de move e fora de uma atividade.|  
|Expressão|Uma atividade com um valor de retorno alto usado em associações do argumento.|  
  
## <a name="workflow-runtime"></a>Tempo de Execução do Fluxo de Trabalho  
 O tempo de execução de fluxo de trabalho é o ambiente no qual os fluxos de trabalho são executadas. <xref:System.Activities.WorkflowInvoker> é a maneira mais simples para executar um fluxo de trabalho. O host usa <xref:System.Activities.WorkflowInvoker> para o seguinte:  
  
-   Para chamar sincronamente um fluxo de trabalho.  
  
-   Para fornecer a entrada, ou recupere saída de um fluxo de trabalho.  
  
-   Para adicionar as extensões a ser usadas por atividades.  
  
 <xref:System.Activities.ActivityInstance> é o proxy thread-safe que hospeda pode usar para interagir com o tempo de execução. O host usa <xref:System.Activities.ActivityInstance> para o seguinte:  
  
-   Para obter uma instância ou criando o carregar o de um armazenamento de instância.  
  
-   Para ser notificado de eventos de ciclo de vida da instância.  
  
-   Para controlar a execução de fluxo de trabalho.  
  
-   Para fornecer a entrada, ou recupere saída de um fluxo de trabalho.  
  
-   Para sinalizar uma continuação de fluxo de trabalho e passar valores no fluxo de trabalho.  
  
-   Para persistir dados de fluxo de trabalho.  
  
-   Para adicionar as extensões a ser usadas por atividades.  
  
 As atividades acedem para o ambiente de tempo de execução de fluxo de trabalho usando a classe derivada apropriada de <xref:System.Activities.ActivityContext> , como <xref:System.Activities.NativeActivityContext> ou <xref:System.Activities.CodeActivityContext>. Usam essa resolvendo argumentos e variáveis, agendando atividades filhos, e muitas outras para fins.  
  
## <a name="services"></a>Serviços  
 Fluxos de trabalho fornecem uma maneira natural de implementar e acessar serviços fracamente acoplados, usando atividades de mensagem. As atividades de mensagem são compiladas em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e são o mecanismo principal usado para obter e retirar dados de um fluxo de trabalho. Você pode composto atividades de mensagem juntos para modelar qualquer tipo de padrão de troca de mensagem você deseja. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]consulte [atividades de mensagens](../../../docs/framework/wcf/feature-details/messaging-activities.md). Os serviços de fluxo de trabalho são hospedados usando a classe de <xref:System.ServiceModel.Activities.WorkflowServiceHost> . [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Visão geral dos serviços de hospedagem de fluxo de trabalho](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Serviços de fluxo de trabalho consulte [serviços de fluxo de trabalho](../../../docs/framework/wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Persistência, descarga, e fluxos de trabalho longos  
 O fluxo de trabalho do Windows simplifica a criação de programas reativos longos fornecendo:  
  
-   Atividades que acessam a entrada externo.  
  
-   A capacidade de criar os objetos de <xref:System.Activities.Bookmark> que podem ser continuados por um ouvinte host.  
  
-   A capacidade de persistir os dados de um fluxo de trabalho e de descarregar o fluxo de trabalho, e recarregar e reativar no fluxo de trabalho em resposta a ressunção de objetos <xref:System.Activities.Bookmark> em um fluxo de trabalho específico.  
  
 Um fluxo de trabalho executar continuamente atividades até que não haja mais atividade a executar ou até que todas as atividades atualmente em execução esperem entrada. Nesse último estado, o fluxo de trabalho estiver ocioso. É comum para um host descarregar fluxos de trabalho que tenham a ociosa ida e para os recarregar para continuar a execução quando uma mensagem chega. <xref:System.ServiceModel.Activities.WorkflowServiceHost> fornece a funcionalidade para este recurso e fornece um extensível descarrega a política. Para os blocos de execução que usam os dados voláteis de estado ou outros dados que não podem ser mantidos, uma atividade pode indicar a um host que não deve ser mantidas usando <xref:System.Activities.NoPersistHandle>. Um fluxo de trabalho também pode explicitamente persistir os dados a um meio de armazenamento durável usando a atividade de <xref:System.Activities.Statements.Persist> .
