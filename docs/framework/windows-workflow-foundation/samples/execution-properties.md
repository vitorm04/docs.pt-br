---
title: "Propriedades de execução"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a394ff136464dd2e69f8c38f07b1b2542bf4a87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`  
  
## <a name="see-also"></a>Consulte também
