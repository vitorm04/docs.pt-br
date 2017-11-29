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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a5ab416dc484dddc0b6aa0ec25757921815c723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="overloadgroups"></a>OverloadGroups
Esse exemplo consiste em uma atividade (`CreateLocation`), que tem duas características interessantes:  
  
1.  Tem alguns argumentos necessários e opcionais alguns.  
  
2.  Permite que o usuário escolha para fornecer um dos dois diferentes conjuntos de argumentos.  
  
 Esses comportamentos é realizada usando esses dois recursos:  
  
-   `[isRequired]` valida que uma propriedade específica de uma atividade é atribui, e se não, ele gerencie uma exceção.  
  
-   `[OverloadGroup]` une um conjunto de argumentos, para que o usuário de atividade pode escolher entre o uso de um conjunto ou outro. O usuário não pode usar argumentos de grupos diferentes de sobrecarga na mesma instância.  
  
 Depois de configurar diferentes fluxos de trabalho, chame <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> que retorna um <xref:System.Activities.Validation.ValidationResults> coleção de <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation`. Imprimir o <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation` objetos no console.  
  
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
  
## <a name="see-also"></a>Consulte também
