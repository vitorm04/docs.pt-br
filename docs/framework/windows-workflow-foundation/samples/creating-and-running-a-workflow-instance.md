---
title: Criando e executando uma instância de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 571d41194ebc98be81646fb5bfdab060225015ca
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516575"
---
# <a name="creating-and-running-a-workflow-instance"></a>Criando e executando uma instância de fluxo de trabalho
Este exemplo mostra como executar uma instância de fluxo de trabalho. Mostra como executar forma síncrona e de forma assíncrona.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>Discussão  
 A primeira parte do exemplo usa <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Esta é a maneira mais básica de executar um fluxo de trabalho. Fluxos de trabalho executados com <xref:System.Activities.WorkflowInvoker.Invoke%2A> são executados synchronously.  
  
 A segunda parte do exemplo usa a classe de <xref:System.Activities.WorkflowApplication> . <xref:System.Activities.WorkflowApplication> permite que você ter mais controle sobre cada instância, incluindo a capacidade de interagir com o fluxo de trabalho em execução e executar de forma assíncrona o fluxo de trabalho.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>Consulte também  
 [Usando WorkflowInvoker e WorkflowApplication](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
