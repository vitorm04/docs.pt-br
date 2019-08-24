---
title: Criando e executando uma instância de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016042"
---
# <a name="creating-and-running-a-workflow-instance"></a>Criando e executando uma instância de fluxo de trabalho

Este exemplo mostra como executar uma instância de fluxo de trabalho. Mostra como executar forma síncrona e de forma assíncrona.

## <a name="demonstrates"></a>Demonstra

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Discussão

A primeira parte do exemplo usa <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Esta é a maneira mais básica de executar um fluxo de trabalho. Fluxos de trabalho executados com <xref:System.Activities.WorkflowInvoker.Invoke%2A> são executados synchronously.

A segunda parte do exemplo usa a classe de <xref:System.Activities.WorkflowApplication> . <xref:System.Activities.WorkflowApplication> permite que você ter mais controle sobre cada instância, incluindo a capacidade de interagir com o fluxo de trabalho em execução e executar de forma assíncrona o fluxo de trabalho.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Consulte também

- [Usando WorkflowInvoker e WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
