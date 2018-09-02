---
title: Grupo de atividade condicionado
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 144a6c76ea6314c553e201fe4e2364890d869f34
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418163"
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
