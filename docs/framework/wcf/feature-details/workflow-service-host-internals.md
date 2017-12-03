---
title: "Internos do host de serviço de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf12cac374759c1cb45a7086ac771a982758e78f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-service-host-internals"></a>Internos do host de serviço de fluxo de trabalho
<xref:System.ServiceModel.WorkflowServiceHost>Fornece um host para os serviços de fluxo de trabalho. Ele é responsável por escutar mensagens de entrada e roteá-los para a instância do serviço de fluxo de trabalho apropriado, ele controla descarregar e persistentes de fluxos de trabalho ociosos e muito mais. Este tópico descreve como WorkflowServiceHost processa mensagens de entrada.  
  
## <a name="workflowservicehost-overview"></a>Visão geral de WorkflowServiceHost  
 O <xref:System.ServiceModel.WorkflowServiceHost> classe é usada para hospedar serviços de fluxo de trabalho. Ele escuta mensagens de entrada e os direciona para a instância de serviço apropriado, criando novas instâncias ou carregar instâncias existentes de armazenamento durável, conforme necessário.  O diagrama a seguir ilustra em um alto nível como <xref:System.ServiceModel.WorkflowServiceHost> funciona.  
  
 ![Visão geral de WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 Este diagrama mostra que <xref:System.ServiceModel.WorkflowServiceHost> carrega as definições de serviço de fluxo de trabalho de arquivos .xamlx e carrega as informações de configuração de um arquivo de configuração. Ele também carrega controle de configuração do perfil de rastreamento. <xref:System.ServiceModel.WorkflowServiceHost>expõe um ponto de extremidade de controle de fluxo de trabalho que permite que você envie as operações de controle para instâncias de fluxo de trabalho.  Para obter mais informações, consulte [ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) e [exemplo de ponto de extremidade de gerenciamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>também expõe pontos de extremidade do aplicativo escutam mensagens de aplicativo de entrada. Quando chega uma mensagem de entrada, ela é enviada para a instância do serviço de fluxo de trabalho apropriado (se ele é carregado no momento). Se for necessário uma nova instância de fluxo de trabalho é criado. Ou, se uma instância existente é persistente é carregado do armazenamento de persistência.  
  
## <a name="workflowservicehost-details"></a>Detalhes do WorkflowServiceHost  
 O diagrama a seguir mostra como <xref:System.ServiceModel.WorkflowServiceHost> manipula mensagens em mais detalhes.  
  
 ![Fluxo de mensagens do Host de serviço de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 Este diagrama mostra três pontos de extremidade diferentes, um ponto de extremidade do aplicativo, um ponto de extremidade de controle de fluxo de trabalho e um ponto de extremidade de hospedagem de fluxo de trabalho. O ponto de extremidade do aplicativo recebe mensagens que são vinculadas para uma instância de fluxo de trabalho específico. Verifica se o ponto de extremidade de controle de fluxo de trabalho para operações de controle. O fluxo de trabalho que hospeda o ponto de extremidade de escuta para mensagens que causam <xref:System.ServiceModel.WorkflowServiceHost> para carregar e executar fluxos de trabalho sem serviço. Conforme mostrado no diagrama de todas as mensagens são processadas pelo tempo de execução do WCF.  Limitação de instância do serviço de fluxo de trabalho é obtida usando o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> propriedade. Essa propriedade limita o número de instâncias de serviço de fluxo de trabalho simultâneas. Quando essa limitação é excedida adicional serão enfileiradas solicitações para novas instâncias de serviço de fluxo de trabalho ou solicitações para ativar instâncias de fluxo de trabalho persistentes. As solicitações em fila são processadas em ordem de FIFO independentemente de estarem solicitações para uma nova instância ou uma instância em execução e persistente. Informações de política de host são carregadas que determina como exceções sem tratamento são tratadas e serviços de fluxo de trabalho ocioso são descarregados e persistente. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]consulte estes tópicos [como: configurar o fluxo de trabalho sem tratamento comportamento de exceção com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) e [como: configurar comportamento ocioso com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Instâncias de fluxo de trabalho são mantidas de acordo com as políticas de host e são recarregadas quando necessário. Para obter mais informações sobre a persistência de fluxo de trabalho, consulte: [como: configurar persistência com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), e [persistência de fluxo de trabalho ](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 A ilustração a seguir mostra o que é chamado de WorkflowServiceHost. Open.  
  
 ![Quando o WorkflowServiceHost. Open é chamado](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 O fluxo de trabalho XAML é carregado e a árvore de atividade é criada. <xref:System.ServiceModel.WorkflowServiceHost>conduzirá a árvore de atividade e cria a descrição do serviço. Configuração é aplicada ao host. Finalmente, o host começa a escutar mensagens de entrada.  
  
 A ilustração a seguir mostra o que o <xref:System.ServiceModel.WorkflowServiceHost> quando ele recebe uma mensagem associada para uma atividade de recebimento com o CanCreateInstance definida como `true`.  
  
 ![Host de serviço de fluxo de trabalho recebe uma mensagem](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 A mensagem chega e é processada pela pilha de canal WCF. Limitações são verificadas e consultas de correlação são executadas. Se a mensagem é vinculada a uma instância existente a mensagem será entregue. Se uma nova instância deve ser criada, a propriedade CanCreateInstance de recepção da atividade é verificada. Se for definido como true, uma nova instância é criada e a mensagem será entregue.  
  
 A ilustração a seguir mostra o que o <xref:System.ServiceModel.WorkflowServiceHost> quando ele recebe uma mensagem associada para uma atividade de recebimento com o CanCreateInstance definida como false.  
  
 ![WorkflowServiceHost recebe uma mensagem](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 A mensagem chega e é processada pela pilha de canal WCF. Limitações são verificadas e consultas de correlação são executadas. A mensagem é vinculada a uma instância existente (porque CanCreateInstance é falso) para a instância é carregada do repositório de persistência, o indicador é retomado e executa o fluxo de trabalho.  
  
> [!WARNING]
>  Host de serviço de fluxo de trabalho não abrir se o SQL Server está configurado para escutar no protocolo de pipe nomeado apenas.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Serviços de hospedagem de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 [Ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 [Exemplo de ponto de extremidade de gerenciamento de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)  
 [Como: configurar o fluxo de trabalho sem tratamento do comportamento de exceção com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
 [Criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
