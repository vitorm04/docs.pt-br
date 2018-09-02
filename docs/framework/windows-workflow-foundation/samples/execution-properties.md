---
title: Propriedades de execução
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409083"
---
# <a name="execution-properties"></a>Propriedades de execução
Este exemplo mostra como definir e usar uma propriedade de execução em uma atividade personalizado. Nesse exemplo, a propriedade de execução determina a cor do console de primeiro plano. Um fluxo de trabalho do exemplo mostra como caminhos lógicos diferentes de execução (ramificações de uma atividade de <xref:System.Activities.Statements.Parallel> ) podem manter diferentes cores de console independentemente de execução intercalada de atividades (através das ramificações de atividade de <xref:System.Activities.Statements.Parallel> ).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução de exemplo de ExecutionProperties.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Exibir ThreeColors.xaml antes de criar a solução exibe um erro, porque as atividades personalizados usadas devem ser compiladas ao mesmo tempo que a solução.  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`