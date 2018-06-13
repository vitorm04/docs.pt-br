---
title: 'Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 35158c45217e764bc2e27dac26f8d680e5897fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514412"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho
Este tópico descreve como ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho.  
  
## <a name="enable-persistence-for-workflows"></a>Ativar persistência para fluxos de trabalho  
 Você pode associar um armazenamento de instância com um **WorkflowApplication** usando o <xref:System.Activities.WorkflowApplication.InstanceStore%2A> propriedade o <xref:System.Activities.WorkflowApplication> classe. O método de <xref:System.Activities.WorkflowApplication.Persist%2A> salva ou persiste um fluxo de trabalho no armazenamento de instância associada ao aplicativo. O método de <xref:System.Activities.WorkflowApplication.Unload%2A> persiste um fluxo de trabalho no armazenamento de instância e então descarrega a instância de memória. O **carga** método carrega um fluxo de trabalho na memória usando os dados de fluxo de trabalho armazenados no repositório de persistência de instância.  
  
 O **Persist** método executa as seguintes etapas:  
  
1.  Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.  
  
2.  Persiste ou salva o fluxo de trabalho no armazenamento de persistência.  
  
3.  Continua o agendador de fluxo de trabalho.  
  
 O **Unload** método executa as seguintes etapas:  
  
1.  Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.  
  
2.  Persiste ou salva o fluxo de trabalho no armazenamento de persistência.  
  
3.  Descarte a instância de fluxo de trabalho na memória.  
  
 Ambos o **Persist** e **Unload** métodos bloqueará enquanto um fluxo de trabalho está em uma zona no-persist até que o fluxo de trabalho será encerrado a zona no-persist. O método continua com persistir ou descarrega a operação após a zona sem persistir completa. Se a zona sem persistir não concluir passa antes do tempo limite, ou se o processo de persistência leva muito longas, um TimeoutException será lançada.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>Ativar persistência para serviços de fluxo de trabalho no código  
 O **DurableInstancingOptions** membro o <xref:System.ServiceModel.WorkflowServiceHost> classe tem uma propriedade denominada **InstanceStore** que você pode usar para associar um armazenamento de instância com o **WorkflowServiceHost** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Quando o **WorkflowServiceHost** é aberto, persistência é habilitada automaticamente se o **DurableInstancingOptions.InstanceStore** não é nulo.  
  
 Normalmente, um comportamento de serviço fornece o armazenamento de instância concreta para ser usado com um host de serviço de fluxo de trabalho usando o **InstanceStore** propriedade. Por exemplo, o SqlWorkflowInstanceStoreBehavior cria uma instância do **SqlWorkflowInstanceStore**, configura e atribui-lo para o **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Ativar persistência para serviços de fluxo de trabalho usando um arquivo de configuração do aplicativo  
 Persistência pode ser ativada usando um arquivo de configuração do aplicativo adicionando o seguinte código ao seu arquivo app.config ou web.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
