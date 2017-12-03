---
title: "Expõe e chamar ActivityActions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 27b5ea6c4a4afea1bc3cb9f5a79d22850d2a4143
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="exposing-and-invoking-activityactions"></a>Expõe e chamar ActivityActions
Este exemplo demonstra como desenvolver uma atividade personalizado que tem <xref:System.Activities.ActivityAction>. Também demonstra como usar esta atividade fornecendo uma implementação de <xref:System.Activities.ActivityAction>.  
  
 Um <xref:System.Activities.ActivityAction> permite que um autor de atividade expõem "intervalos" com assinaturas específicas em que o usuário de atividade pode conectar um comportamento personalizado. Por exemplo, o <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` atividade, (que opera em uma coleção de itens), tem um <xref:System.Activities.ActivityAction> que permite que o usuário de atividade de comportamento que opera no item de iteração atual.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **ActivityAction.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`