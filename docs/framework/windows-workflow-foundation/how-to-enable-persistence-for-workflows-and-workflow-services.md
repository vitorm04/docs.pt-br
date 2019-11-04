---
title: 'Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460885"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Como: Ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho

Este tópico descreve como ativar persistência para fluxos de trabalho e serviços de fluxo de trabalho.

## <a name="enable-persistence-for-workflows"></a>Ativar persistência para fluxos de trabalho

Você pode associar um repositório de instância com um **WorkflowApplication** usando a propriedade <xref:System.Activities.WorkflowApplication.InstanceStore%2A> da classe <xref:System.Activities.WorkflowApplication>. O método de <xref:System.Activities.WorkflowApplication.Persist%2A> salva ou persiste um fluxo de trabalho no armazenamento de instância associada ao aplicativo. O método de <xref:System.Activities.WorkflowApplication.Unload%2A> persiste um fluxo de trabalho no armazenamento de instância e então descarrega a instância de memória. O método **Load** carrega um fluxo de trabalho na memória usando os dados de fluxo de trabalho armazenados no repositório de persistência da instância.

O método **Persist** executa as seguintes etapas:

1. Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.

2. Persiste ou salva o fluxo de trabalho no armazenamento de persistência.

3. Continua o agendador de fluxo de trabalho.

 O método **Unload** executa as seguintes etapas:

1. Pausa o agendador de fluxo de trabalho e aguarda até que o fluxo de trabalho entre o estado ocioso.

2. Persiste ou salva o fluxo de trabalho no armazenamento de persistência.

3. Descarte a instância de fluxo de trabalho na memória.

Os métodos **Persist** e **Unload** serão bloqueados enquanto um fluxo de trabalho estiver em uma zona de não persistência até que o fluxo de trabalho saia da zona sem persistência. O método continua com persistir ou descarrega a operação após a zona sem persistir completa. Se a zona sem persistir não concluir passa antes do tempo limite, ou se o processo de persistência leva muito longas, um TimeoutException será lançada.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Ativar persistência para serviços de fluxo de trabalho no código

O membro **DurableInstancingOptions** da classe <xref:System.ServiceModel.WorkflowServiceHost> tem uma propriedade chamada **InstanceStore** que você pode usar para associar um repositório de instância ao **WorkflowServiceHost**.

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

Quando o **WorkflowServiceHost** for aberto, a persistência será habilitada automaticamente se o **DurableInstancingOptions. InstanceStore** não for nulo.

Normalmente, um comportamento de serviço fornece o armazenamento de instância concreto a ser usado com um host de serviço de fluxo de trabalho usando a propriedade **InstanceStore** . Por exemplo, o SqlWorkflowInstanceStoreBehavior cria uma instância do **SqlWorkflowInstanceStore**, configura-a e a atribui ao **DurableInstancingOptions. InstanceStore**.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Ativar persistência para serviços de fluxo de trabalho usando um arquivo de configuração do aplicativo

Persistência pode ser ativada usando um arquivo de configuração do aplicativo adicionando o seguinte código ao seu arquivo app.config ou web.config:

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
