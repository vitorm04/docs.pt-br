---
title: Manipulador cancelar a atividade compensável
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: ce4d67b26a2b4c6a9b507715b48e75e328c5b100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514995"
---
# <a name="cancellation-handler-on-compensable-activity"></a>Manipulador cancelar a atividade compensável
Este exemplo demonstra o uso de um manipulador cancelar em <xref:System.Activities.Statements.CompensableActivity>.  
  
 Este exemplo contém dois cenários que demonstram o uso de cancelamento de <xref:System.Activities.Statements.CompensableActivity> . O primeiro cenário contém uma atividade compensável raiz que contém três atividades compensáveis filhos. Duas atividades filhos completa executar seus corpo da atividade com êxito. Quando o terceiro corpo filho da atividade é executado, ele encontrar uma exceção que é manipulada cancelar o terceiro processamento de atividade, após o qual cancelamento de atividade da raiz é disparado. A lógica na atividade raiz nesse exemplo é compensar duas outras atividades filhos que eles concluíram anteriormente.  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 O segundo cenário demonstra executar <xref:System.Activities.Statements.TryCatch> paralelamente a <xref:System.Activities.Statements.Delay>, que os terminar antes de <xref:System.Activities.Statements.TryCatch> ramificação. A condição de conclusão é definida como `true` uma vez que o primeiro ramificação concluir, causando a outra ramificação a ser cancelado.  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra CompensationCancellation.sln.  
  
2.  Compilar o exemplo pressionando CTRL+SHIFT+B ou selecione a solução compilação” do menu de compilação.  
  
3.  Executar o exemplo pressionando F5 ou selecione “Iniciar a depuração” no menu debug. Como alternativa você pode pressionar Ctrl+F5 ou selecione “Iniciar sem depuração” no menu debug.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`