---
title: Confirmação
ms.date: 03/30/2017
ms.assetid: 8637aeaf-ac9e-49b8-93f4-da15dee45277
ms.openlocfilehash: 334ac362333565626dd2bb8dcaede27fbab16f33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="confirmation"></a>Confirmação
Este exemplo mostra quatro cenários comuns envolvendo o uso de <xref:System.Activities.Statements.CompensableActivity> e de confirmação. O exemplo é executado quatro fluxos de trabalho para mostrar a confirmação. Este exemplo está disponível em versões declarativas e imperativas.  
  
## <a name="confirm-a-compensable-activity"></a>Confirme uma atividade compensável  
 O primeiro fluxo de trabalho demonstra como confirmar uma atividade compensável e consiste em uma sequência de duas instâncias de <xref:System.Activities.Statements.CompensableActivity> . Após a conclusão do segundo <xref:System.Activities.Statements.CompensableActivity> uma atividade de confirmação confirmar a primeira atividade. Quando o fluxo de trabalho concluída com sucesso, todas as instâncias de <xref:System.Activities.Statements.CompensableActivity> que não foram confirmadas ou não foram compensadas são confirmadas automaticamente usando a ordem padrão. Sem confirmação, conforme <xref:System.Activities.Statements.CompensableActivity> seria confirmado primeiro.  
  
## <a name="explicit-compensation"></a>Compensação explícita  
 O segundo cenário mostra o efeito de confirmação padrão quando <xref:System.Activities.Statements.CompensableActivity> é compensado explicitamente. O fluxo de trabalho consiste em uma sequência de duas atividades de <xref:System.Activities.Statements.CompensableActivity> , depois que o segundo concluir o primeiro é compensado explicitamente. Como resultado quando o fluxo de trabalho, conclui-se somente como <xref:System.Activities.Statements.CompensableActivity> é confirmado.  
  
## <a name="controlling-the-order-of-confirmation-for-nested-compensableactivity-activities"></a>Controlando a ordem de confirmação para atividades aninhados de CompensableActivity  
 O terceiro cenário mostra como controlar a ordem de confirmação para <xref:System.Activities.Statements.CompensableActivity>aninhado. O cenário consiste em <xref:System.Activities.Statements.CompensableActivity> como a raiz de fluxo de trabalho. O corpo da raiz <xref:System.Activities.Statements.CompensableActivity> é uma sequência de três <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> para a raiz <xref:System.Activities.Statements.CompensableActivity> é uma sequência que especifica para confirmar o primeiro em segundo <xref:System.Activities.Statements.CompensableActivity>aninhado. Quando o fluxo de trabalho concluir confirmar a raiz <xref:System.Activities.Statements.CompensableActivity>, que confirma em seguida, primeiro segundo e terceiro <xref:System.Activities.Statements.CompensableActivity>aninhado, nessa ordem. Como resultado, a ordem padrão de confirmação é invertido essencialmente. Como a terceira <xref:System.Activities.Statements.CompensableActivity> não foi confirmado explicitamente como parte da raiz <xref:System.Activities.Statements.CompensableActivity> por <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>, confirma-se de acordo com a ordem padrão. No entanto, como é único <xref:System.Activities.Statements.CompensableActivity> não-confirmado isso significa apertado confirma-se.  
  
## <a name="scoping-of-variables"></a>Escopo de variáveis  
 O quarto cenário mostra como o tempo de vida de variáveis definidas para <xref:System.Activities.Statements.CompensableActivity> ou um de seus pais ainda estão no escopo quando <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> ou manipuladores de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> são executados mesmo se a atividade concluiu ou o fluxo de trabalho concluído. O fluxo de trabalho consiste em uma sequência de dois <xref:System.Activities.Statements.CompensableActivity>. O corpo do primeiro, `mySum` variável é definido a soma de 5 e 10 e o resultado impresso. No corpo da segunda <xref:System.Activities.Statements.CompensableActivity>, o resultado é definida como a soma de soma e os 7 existentes e o resultado impresso. Um manipulador personalizado de confirmação é definido para o primeiro <xref:System.Activities.Statements.CompensableActivity>, que imprimir a soma, subtraia 7 e imprimir a soma novamente. É claro inspecionando as somas impressas que a variável está no escopo não apenas para os corpos de ambos <xref:System.Activities.Statements.CompensableActivity> de <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> mas também.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Carregar a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Execute o aplicativo de ConfirmationSample.exe.  
  
3.  Observe a saída a seguir:  
  
 **Confirmação: início explícita de workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: HandlerEnd de confirmação de workflowCompensableActivity2: confirmação HandlerExplicit compensação: início do workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity1: HandlerEnd de compensação de workflowCompensableActivity2: confirmação HandlerCustom confirmação: início do manipulador de workflowCompensableActivity1: BodyCompensableActivity2: BodyCompensableActivity3: BodyEnd de workflowCompensableActivity1: HandlerCompensableActivity2 de confirmação: HandlerCompensableActivity3 de confirmação: acesso HandlerVariable de confirmação em um manipulador de confirmação: Início de workflowCompensableActivity1: BodyCompensableActivity1: A soma é: 15CompensableActivity2: BodyCompensableActivity2: adicionando 7 para o sumCompensableActivity2: A soma é agora: 22End de workflowCompensableActivity2: confirmação HandlerCompensableActivity1: Confirmação HandlerCompensableActivity2: A soma é: 22CompensableActivity2: depois da subtração de 12 a soma é agora: 10Press ENTER para sair.**  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\Confirmation`