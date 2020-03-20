---
title: Internos do host de serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: b95a59b0e1715b3cc18ccfea44d6c4ccd04ca5ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184169"
---
# <a name="workflow-service-host-internals"></a>Internos do host de serviço de fluxo de trabalho
<xref:System.ServiceModel.WorkflowServiceHost>fornece um host para serviços de fluxo de trabalho. Ele é responsável por ouvir as mensagens recebidas e encaminhá-las para a instância de serviço de fluxo de trabalho apropriada, controla o descarregamento e a persistência de fluxos de trabalho ociosos e muito mais. Este tópico descreve como o WorkflowServiceHost processa mensagens recebidas.  
  
## <a name="workflowservicehost-overview"></a>Visão geral de WorkflowServiceHost  

A <xref:System.ServiceModel.WorkflowServiceHost> classe é usada para hospedar serviços de fluxo de trabalho. Ele ouve mensagens recebidas e as encaminha para a instância de serviço apropriada, criando novas instâncias ou carregando instâncias existentes de armazenamento durável conforme necessário. O diagrama a seguir ilustra <xref:System.ServiceModel.WorkflowServiceHost> em um alto nível como funciona:
  
 ![Diagrama que mostra uma visão geral do host de serviço de fluxo de trabalho.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Este diagrama <xref:System.ServiceModel.WorkflowServiceHost> mostra que carrega definições de serviço de fluxo de trabalho a partir de arquivos .xamlx e carrega informações de configuração de um arquivo de configuração. Ele também carrega a configuração de rastreamento a partir do perfil de rastreamento. <xref:System.ServiceModel.WorkflowServiceHost>expõe um ponto final de controle de fluxo de trabalho que permite enviar operações de controle para instâncias de fluxo de trabalho.  Para obter mais informações, consulte [a amostra ponto final do controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost>também expõe pontos finais de aplicativos que ouvem mensagens de aplicativos recebidas. Quando uma mensagem recebida chega, ela é enviada para a instância de serviço de fluxo de trabalho apropriada (se ela estiver atualmente carregada). Se necessário, uma nova instância de fluxo de trabalho é criada. Ou se uma instância existente tiver sido persistida, ela será carregada a partir do armazenamento de persistência.  
  
## <a name="workflowservicehost-details"></a>Detalhes do WorkflowServiceHost  
 O diagrama <xref:System.ServiceModel.WorkflowServiceHost> a seguir mostra como lida com as mensagens com um pouco mais de detalhes:  
  
 ![Diagrama que mostra o fluxo de mensagem host do serviço de fluxo de trabalho.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Este diagrama mostra três pontos finais diferentes, um ponto final do aplicativo, um ponto final de controle de fluxo de trabalho e um ponto final de hospedagem de fluxo de trabalho. O ponto final do aplicativo recebe mensagens vinculadas a uma instância específica do fluxo de trabalho. O ponto final do controle do fluxo de trabalho ouve as operações de controle. O ponto final de hospedagem do <xref:System.ServiceModel.WorkflowServiceHost> fluxo de trabalho ouve mensagens que causam carregar e executar fluxos de trabalho não-serviço. Como mostrado no diagrama, todas as mensagens são processadas através do tempo de execução do WCF.  O estrangulamento da instância de instância <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> do fluxo de trabalho é obtido usando a propriedade. Essa propriedade limitará o número de instâncias simultâneas de serviço de fluxo de trabalho. Quando este acelerador for excedido, quaisquer solicitações adicionais de novas instâncias de serviço de fluxo de trabalho ou solicitações para ativar instâncias de fluxo de trabalho persistidas serão enfileiradas. As solicitações enfileiradas são processadas na ordem FIFO, independentemente de serem solicitações de uma nova instância ou de uma instância em execução. As informações da diretiva de host são carregadas que determina como exceções não tratadas são tratadas e como os serviços de fluxo de trabalho ociosos são descarregados e persistidos. Para obter mais informações sobre esses [tópicos, consulte Como: Configurar o comportamento de exceção não manipulado do fluxo de trabalho com o WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) e [como: Configurar comportamento ocioso com workflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). As instâncias de fluxo de trabalho são persistidas de acordo com as políticas de host e são recarregadas quando necessário. Para obter mais informações sobre a persistência do fluxo de trabalho, [consulte: Como configurar a persistência com workflowServiceHost,](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md) [criando um serviço de fluxo de trabalho de longa duração](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)e persistência do fluxo de [trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 A ilustração a seguir mostra o fluxo quando workflowServiceHost.Open é chamado:  
  
 ![Diagrama que mostra o fluxo quando WorkflowServiceHost.Open é chamado.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 O fluxo de trabalho é carregado a partir de XAML e a árvore de atividade é criada. <xref:System.ServiceModel.WorkflowServiceHost>caminha pela árvore de atividades e cria a descrição do serviço. A configuração é aplicada ao host. Finalmente, o anfitrião começa a ouvir as mensagens recebidas.  
  
 A ilustração a <xref:System.ServiceModel.WorkflowServiceHost> seguir mostra o que faz quando recebe uma mensagem vinculada a uma atividade Receber que tenha CanCreateInstance definido como `true`:  
  
 ![A árvore de decisão usada pelo Host WFS quando recebe uma mensagem e o CanCreateInstance é verdadeiro.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 A mensagem chega e é processada pela pilha de canais WCF. Os aceleradores são verificados e as consultas de correlação são executadas. Se a mensagem estiver vinculada a uma instância existente, a mensagem será entregue. Se uma nova instância precisar ser criada, a propriedade CanCreateInstance da atividade receberá a verificação. Se for definido como verdadeiro, uma nova instância será criada e a mensagem será entregue.  
  
 A ilustração a <xref:System.ServiceModel.WorkflowServiceHost> seguir mostra o que faz quando recebe uma mensagem vinculada a uma atividade Receber que tem CanCreateInstance definido como falso.  
  
 ![A árvore de decisão usada pelo Host WFS quando recebe uma mensagem e o CanCreateInstance é falsa.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 A mensagem chega e é processada pela pilha de canais WCF. Os aceleradores são verificados e as consultas de correlação são executadas. A mensagem é vinculada a uma instância existente (porque canCreateInstance é falsa) para que a instância seja carregada do armazenamento de persistência, o marcador seja retomado e o fluxo de trabalho seja executado.  
  
> [!WARNING]
> O Workflow Service Host falhará se o SQL Server estiver configurado para ouvir apenas no protocolo NamedPipe.  
  
## <a name="see-also"></a>Confira também

- [Serviços de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Serviços de fluxo de trabalho de hospedagem](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [Ponto de extremidade de controle de fluxo de trabalho](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Como configurar um comportamento de exceção não tratado de fluxo de trabalho com o WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Criando um serviço de fluxo de trabalho de execução longa](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Persistência de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
