---
title: Tipos de restrições
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 53e5975017c3a27ede8ad07cd93f78f71df2d3e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="constraint-types"></a>Tipos de restrições
Este exemplo mostra duas maneiras diferentes de aplicar restrições em um fluxo de trabalho, um é de dentro da atividade (compilação) e uma estiver fora delas (diretiva). Nesse cenário, um autor de atividade (de uma empresa software de 3rth-party) deseja validar a relação entre dois argumentos. Nesse caso, o custo devem ser menores do que ou igual ao preço. Esta é uma restrição geral de compilação de validação.  
  
 Em um vendedor deseja adicionar alguma validação a esta atividade genérico. Nos casos, desejar que a maioria dos produtos para ser $9,99 ou menos. Assim, usa uma restrição de política que é sobre a atividade de `CreateProduct` .  
  
 No exemplo:  
  
 O autor de atividade (compilação) deve:  
  
-   Criar uma restrição (`PriceGreaterThanCost`). Isso é onde qualquer lógica de validação reside.  
  
-   Substitua o `System.Activities.CodeActivity.OnGetConstraints()` e adicione a restrição (`PriceGreaterThanCost`) às restrições <xref:System.Collections.IList>.  
  
 O autor de fluxo de trabalho (diretiva) deve:  
  
-   Crie um fluxo de trabalho com uma instância de atividade para validar (`CreateProduct`).  
  
-   Criar uma restrição (`MaxPrice`).  
  
-   Crie uma instância de <xref:System.Activities.Validation.ValidationSettings> (`validationSettings`) e adicione a restrição (`MaxPrice`) à coleção `AdditionalConstraints`. Aqui o autor de fluxo de trabalho pode adicionar restrições de política a quaisquer atividades, como uma sequência ou uma paralela.  
  
-   Chame o <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, que retorna uma coleção de <xref:System.Activities.Validation.ValidationResults> de objetos <xref:System.Activities.Validation.ValidationError> .  
  
-   (Opcional) imprima os objetos de <xref:System.Activities.Validation.ValidationError> .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução de exemplo de ConstraintTypes.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`