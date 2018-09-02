---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469863"
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
  
1.  Abra o **Overloadgroups** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
