---
title: Internos do host de serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: dd03508397b77f4446a5b708c69333336d97193c
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036033"
---
# <a name="workflow-service-host-internals"></a>Internos do host de serviço de fluxo de trabalho
<xref:System.ServiceModel.WorkflowServiceHost> Fornece um host para serviços de fluxo de trabalho. Ele é responsável por escutar mensagens de entrada e roteá-lo à instância do serviço de fluxo de trabalho apropriado, controla descarregando e persistência de fluxos de trabalho ociosos e muito mais. Este tópico descreve como o WorkflowServiceHost processa as mensagens de entrada.  
  
## <a name="workflowservicehost-overview"></a>Visão geral de WorkflowServiceHost  
 O <xref:System.ServiceModel.WorkflowServiceHost> classe é usada para hospedar serviços de fluxo de trabalho. Ele escuta mensagens de entrada e encaminha-as para a instância de serviço apropriado, criar novas instâncias ou carregar instâncias existentes do armazenamento durável, conforme necessário.  O diagrama a seguir ilustra em um alto nível como <xref:System.ServiceModel.WorkflowServiceHost> funciona.  
  
 ![Visão geral de WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 Este diagrama mostra que <xref:System.ServiceModel.WorkflowServiceHost> carrega as definições de serviço de fluxo de trabalho de arquivos. xamlx e carrega informações de configuração de um arquivo de configuração. Ele também carrega a configuração de rastreamento do perfil de rastreamento. <xref:System.ServiceModel.WorkflowServiceHost> expõe um ponto de extremidade de controle de fluxo de trabalho que permite que você envie operações de controle para instâncias de fluxo de trabalho.  Para obter mais informações, consulte [exemplo de ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost> também expõe pontos de extremidade do aplicativo que escutam mensagens recebidas do aplicativo. Quando chega uma mensagem de entrada, ele é enviado para a instância do serviço de fluxo de trabalho apropriado (se ele é carregado no momento). Se for necessário uma nova instância de fluxo de trabalho é criado. Ou, se uma instância existente tiver sido persistida é carregado do armazenamento de persistência.  
  
## <a name="workflowservicehost-details"></a>Detalhes de WorkflowServiceHost  
 O diagrama a seguir mostra como <xref:System.ServiceModel.WorkflowServiceHost> manipula mensagens de um pouco mais detalhadamente.  
  
 ![Host de serviço de fluxo de trabalho de fluxo de mensagens](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 Este diagrama mostra três pontos de extremidade diferentes, um ponto de extremidade do aplicativo, um ponto de extremidade de controle de fluxo de trabalho e um ponto de extremidade de hospedagem de fluxo de trabalho. O ponto de extremidade do aplicativo recebe mensagens que são associadas para uma instância de fluxo de trabalho específico. O ponto de extremidade de controle de fluxo de trabalho escuta para operações de controle. O fluxo de trabalho que hospeda o ponto de extremidade de escuta para mensagens que causam <xref:System.ServiceModel.WorkflowServiceHost> para carregar e executar fluxos de trabalho sem serviço. Conforme mostrado no diagrama de todas as mensagens são processadas por meio de runtime do WCF.  Limitação da instância de serviço de fluxo de trabalho é obtida usando o <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> propriedade. Essa propriedade limita o número de instâncias de serviço de fluxo de trabalho simultâneas. Quando essa limitação for excedida outras solicitações para novas instâncias de serviço de fluxo de trabalho ou solicitações para ativar instâncias de fluxo de trabalho persistidas serão enfileiradas. As solicitações enfileiradas são processadas na ordem FIFO independentemente de estarem solicitações para uma nova instância ou uma instância em execução e persistida. Informações de política de host são carregadas que determina como são tratadas as exceções sem tratamento e como os serviços de fluxo de trabalho ocioso são descarregados e persistidos. Para obter mais informações sobre esses tópicos, consulte [como: configurar o fluxo de trabalho sem tratamento comportamento de exceção com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) e [como: configurar comportamento ocioso com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). As instâncias de fluxo de trabalho são mantidas de acordo com as políticas de host e são recarregadas quando necessário. Para obter mais informações sobre a persistência do fluxo de trabalho, consulte: [como: configurar a persistência com WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), e [persistência de fluxo de trabalho ](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 A ilustração a seguir mostra o que o WorkflowServiceHost. Open é chamado.  
  
 ![Quando o WorkflowServiceHost. Open é chamado](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 O fluxo de trabalho é carregado do XAML e a árvore de atividade é criada. <xref:System.ServiceModel.WorkflowServiceHost> percorre a árvore de atividade e cria a descrição do serviço. Configuração é aplicada ao host. Finalmente, o host começa a escutar mensagens de entrada.  
  
 A ilustração a seguir mostra o que o <xref:System.ServiceModel.WorkflowServiceHost> faz quando ele recebe uma mensagem associada de uma atividade de recebimento que tem CanCreateInstance definida como `true`.  
  
 ![Host de serviço de fluxo de trabalho recebe uma mensagem](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 A mensagem chega e é processada pela pilha de canais do WCF. As restrições são verificadas e consultas de correlação são executadas. Se a mensagem é vinculada a uma instância existente, a mensagem é entregue. Se precisar de uma nova instância a ser criado, a propriedade CanCreateInstance de recepção da atividade é verificada. Se ele for definido como true, uma nova instância é criada e a mensagem é entregue.  
  
 A ilustração a seguir mostra o que o <xref:System.ServiceModel.WorkflowServiceHost> faz quando ele recebe uma mensagem associada de uma atividade de recebimento que possua CanCreateInstance definida como false.  
  
 ![WorkflowServiceHost recebe uma mensagem](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 A mensagem chega e é processada pela pilha de canais do WCF. As restrições são verificadas e consultas de correlação são executadas. A mensagem está associada para uma instância existente (porque CanCreateInstance é false) para a instância é carregada do repositório de persistência, o indicador é continuado e executa o fluxo de trabalho.  
  
> [!WARNING]
> Host de serviço de fluxo de trabalho não abrir se o SQL Server está configurado para escutar no protocolo de pipe nomeado apenas.  
  
## <a name="see-also"></a>Consulte também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
- [Serviços de fluxo de trabalho de hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
- [Ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
- [Como configurar um comportamento de exceção sem tratamento de fluxo de trabalho com o WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
- [Criando um serviço de fluxo de trabalho de longa execução](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
- [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)