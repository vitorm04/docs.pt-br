---
title: Grupo de atividade condicionado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7049f0ab787264893f334b8fe6aa0036e240a73f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="conditioned-activity-group"></a>Grupo de atividade condicionado
O exemplo demonstra um aplicativo do registro do traço. <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) tem duas atividades de código a seguir: uma atividade do carro e uma atividade de linha sobrecarga. No construtor de `SimpleCAGWorkflow` , um objeto de ArrayList “travelNeedType” é preenchido com os tipos de registros de traço necessários. Comentando por uma ou ambas as instruções de `travelNeeds.Add` , você altera o comportamento de CAG de acordo. As atividades de carro e linha sobrecarga têm sua condição de <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> preenchida com <xref:System.Workflow.Activities.CodeCondition>. Atividade de carro executa somente se a coleção de `travelNeeds` tem uma entrada de `TravelNeeds.Car` , e a atividade de linha sobrecarga executa somente se a coleção de `travelNeeds` tem uma entrada de `TravelNeeds.Airline` .  
  
 A execução de cada atividade remove a entrada correspondente da coleção. A condição de <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> de opção especifica que o CAG deve sair quando nenhum filho está executando ou está pronto para a execução (com base nas condições de <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> ). Nesse exemplo, isso significa que o CAG sai quando a coleção de `travelNeeds` está vazia.  
  
### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1.  Abra a solução em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Executar a solução sem depuração pressionando CTRL + f5.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
-   Na janela do prompt de comando SDK, execute o arquivo .exe no SimpleCAG \ bin \ debug (ou na pasta \ bin de SimpleCAG para a versão do Visual Basic de exemplo), que está localizado abaixo da pasta principal para o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
