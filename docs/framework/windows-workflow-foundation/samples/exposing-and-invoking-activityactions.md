---
title: Expõe e chamar ActivityActions
ms.date: 03/30/2017
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
ms.openlocfilehash: 99207c33d82ec9028da2355cc792c366dc5e0cc6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176393"
---
# <a name="exposing-and-invoking-activityactions"></a>Expõe e chamar ActivityActions
Este exemplo demonstra como desenvolver uma atividade personalizado que tem <xref:System.Activities.ActivityAction>. Também demonstra como usar esta atividade fornecendo uma implementação de <xref:System.Activities.ActivityAction>.  
  
 Um <xref:System.Activities.ActivityAction> permite que um autor de atividade expõe "furos" com assinaturas específicas em que o usuário da atividade pode conectar um comportamento personalizado. Por exemplo, a atividade de <xref:System.Activities.Statements.ForEach%601> , (que opera em uma coleção de itens), tem <xref:System.Activities.ActivityAction> que permite que o usuário de atividade obstrua no comportamento que opera no item de iteração atual.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **ActivityAction** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`