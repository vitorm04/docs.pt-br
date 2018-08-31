---
title: Validação básica
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332727"
---
# <a name="basic-validation"></a>Validação básica
Esse exemplo consiste em uma atividade, `CreateProduct`, que valida que o argumento de `Cost` é menor que ou igual ao seu argumento de `Price` .  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Há dois autores que usam a validação, o autor de atividade (cria a lógica de validação para atividades) e o autor de fluxo de trabalho que chama serviços de validação em um fluxo de trabalho específico. Nesse cenário, o autor de atividade deseja impor que cada instância da atividade deve ter um custo iguais ou menores do que a do preço.  
  
 O autor de atividade (dentro da atividade) deve:  
  
-   Criar uma restrição (`PriceGreaterThanCost`). Isso é onde qualquer lógica de validação reside.  
  
-   Substitua o `System.Activities.CodeActivity.OnGetConstraints()` e adicione a restrição (`PriceGreaterThanCost`) às restrições <xref:System.Collections.IList>.  
  
 O autor de fluxo de trabalho (programa principal) deve:  
  
-   Crie um fluxo de trabalho com uma instância de atividade para validar (`CreateProduct`).  
  
-   Chamar <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, que retorna uma coleção de <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.ValidationError>.  
  
-   (Opcional) imprima os objetos de <xref:System.Activities.Validation.ValidationError> .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução de exemplo de BasicValidation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`