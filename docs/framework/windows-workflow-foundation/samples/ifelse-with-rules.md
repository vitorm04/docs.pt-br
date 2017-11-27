---
title: IfElse com regras
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5cd0859db8071f9af130756fdc9b34726199be9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
