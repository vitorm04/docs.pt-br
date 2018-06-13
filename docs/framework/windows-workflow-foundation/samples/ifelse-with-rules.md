---
title: IfElse com regras
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 179ec29f957894433fb527a14048460f5ff6ee5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515115"
---
# <a name="ifelse-with-rules"></a>IfElse com regras
Este exemplo mostra o uso de uma condição de regra com uma atividade de <xref:System.Workflow.Activities.IfElseActivity> .  
  
 O exemplo passa em um parâmetro de `OrderValue` host. O valor do parâmetro é usado em uma condição de regra no primeiro ramificação de atividade de <xref:System.Workflow.Activities.IfElseActivity> . Se o valor for menor que 10.000, o primeiro branch que é executado e o <xref:System.Workflow.Activities.CodeActivity> atividade na ramificação primeiro imprime **obter aprovação do Gerenciador de** para o console. Se o valor for maior que 10.000, o <xref:System.Workflow.Activities.CodeActivity> atividade na segunda ramificação executa e imprime **Obtenha vice-Presidente aprovação**.  
  
### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1.  Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Executar a solução sem depuração pressionando CTRL + f5.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
-   Na janela do prompt de comando SDK, execute o arquivo .exe no IfElseWithRules \ bin \ debug (ou na pasta \ bin de IfElseWithRules para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
