---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36807ce154ab70e54d211405e0cea5ead56e9b88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="overloadgroups"></a>OverloadGroups
Esse exemplo consiste em uma atividade (`CreateLocation`), que tem duas características interessantes:  
  
1.  Tem alguns argumentos necessários e opcionais alguns.  
  
2.  Permite que o usuário escolha para fornecer um dos dois diferentes conjuntos de argumentos.  
  
 Esses comportamentos é realizada usando esses dois recursos:  
  
-   `[isRequired]` valida que uma propriedade específica de uma atividade é atribui, e se não, ele gerencie uma exceção.  
  
-   `[OverloadGroup]` une um conjunto de argumentos, para que o usuário de atividade pode escolher entre o uso de um conjunto ou outro. O usuário não pode usar argumentos de grupos diferentes de sobrecarga na mesma instância.  
  
 Após configurar fluxos de trabalho diferentes, chamada <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> que retorna uma coleção de <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.Constraint>. Imprima os objetos de <xref:System.Activities.Validation.Constraint> no console.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **OverloadGroups.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
