---
title: Validação das relações de atividades
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: 50f08118fb5ad4d9b8fe809e7ab3cc5d57f28149
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784804"
---
# <a name="activity-relationships-validation"></a>Validação das relações de atividades
Esse exemplo consiste em três atividades, `CreateCity`, `CreateState`, e `CreateCountry`. `CreateCity` deve ser dentro de uma atividade de `CreateState` , e `CreateState` deve ser dentro de uma atividade de `CreateCountry` . Com o propósito deste exemplo, a lógica de validação está no código para atividades de `CreateState` , e XAML para atividades de `CreateCity` . Ambos tem o mesmo comportamento.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fornece as três seguintes atividades auxiliar que permitem que o desenvolvedor valida relações entre atividades:  
  
 <xref:System.Activities.Validation.GetParentChain>  
 Fornece a coleção de todas as atividades que pertencem ao pai do nó atual  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 Fornece a coleção de todas as atividades que pertencem a subárvore do nó atual, excluindo o nó atual  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 Fornece a coleção de todas as atividades na mesma árvore que o nó atual  
  
 No exemplo, uma atividade de <xref:System.Activities.Statements.ForEach%601> é usada para andar através da coleção retornada por <xref:System.Activities.Validation.GetParentChain>. Para cada elemento na coleção, o tipo é comparado a `CreateCountry` (ou a `CreateState` se `CreateCity` está sendo validada), e quando uma correspondência for encontrada o sinalizador do resultado é definido como `true`. Finalmente, <xref:System.Activities.Validation.AssertValidation> é usado para gerar um erro de validação se o sinalizador do resultado é definido como `false`.  
  
### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução de exemplo de ContainmentValidation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile a solução.  
  
3.  O pressionar o CTRL + F5 para iniciar o programa.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
