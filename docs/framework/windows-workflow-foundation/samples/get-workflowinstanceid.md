---
title: Obter WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142726"
---
# <a name="get-workflowinstanceid"></a>Obter WorkflowInstanceId
Este exemplo demonstra como usar a atividade personalizado, `GetWorkflowInstanceId` para retornar a identificação de instância de fluxo de trabalho  
  
## <a name="demonstrates"></a>Demonstra  
 Desenvolvimento personalizado de atividade, como acessar a instância de fluxo de trabalho.  
  
## <a name="discussion"></a>Discussão  
 Obter o ID de instância de um fluxo de trabalho em execução exige a escrever código. Se você deseja gravar um fluxo de trabalho totalmente declarativo, você precisa de uma atividade que pode retornar a ID da instância de fluxo de trabalho de forma que a atividade pode ser referenciada no fluxo de trabalho para fornecer uma experiência totalmente declarativa de criação de fluxo de trabalho. Muitos cenários requerem acesso a identificação da instância: alguns exemplos são de log ou auditando fins ou fazendo correlação de nível fornecendo o ID de instância de volta para um cliente para a associação futura (por exemplo, usando esta atividade dentro de uma atividade de SendReply).  
  
 `GetWorkflowInstanceId` é implementado como <xref:System.Activities.CodeActivity%601> porque ele deve retornar um valor do tipo <xref:System.Guid>, e deve ter acesso a <xref:System.Activities.CodeActivityContext> para obter a identificação de instância de fluxo de trabalho A implementação é bastante básica.  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
