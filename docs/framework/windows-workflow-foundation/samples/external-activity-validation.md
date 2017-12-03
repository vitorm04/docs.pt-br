---
title: "Validação externo de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ebc79fa582a32ccc252e6c22b9b223870da7e44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="external-activity-validation"></a>Validação externo de atividades
Este exemplo mostra como adicionar lógica de validação para uma atividade interno que não é do autor. A lógica de validação consiste garantir que todas as atividades de <xref:System.Activities.Statements.If> atual no fluxo de trabalho têm sua propriedade hierarchical update definida <xref:System.Activities.Statements.If.Then%2A> ou seu conjunto de propriedades de <xref:System.Activities.Statements.If.Else%2A> . Além disso, a lógica de validação inclui verifique se todas as atividades de <xref:System.Activities.Statements.Pick> atual no fluxo de trabalho têm mais de uma ramificação, e se isso não for o caso, um aviso é gerado.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Este exemplo cria um fluxo de trabalho com uma instância de cada atividade para validar: a atividade de <xref:System.Activities.Statements.If> e a atividade de <xref:System.Activities.Statements.Pick> . <xref:System.Activities.Validation.Constraint> é criado para cada comportamento de validação. As restrições criadas nesse exemplo são `ConstraintError_IfShouldHaveThenOrElse` e `ConstraintWarning_PickHasOneBranch`. Em seguida, essas restrições é adicionado à coleção de `AdditionalConstraints` de uma instância de <xref:System.Activities.Validation.ValidationSettings> . Finalmente, o método de `static` de <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> de <xref:System.Activities.Validation.ActivityValidationServices> é chamado para validar as atividades no fluxo de trabalho e os resultados de validação são impresso - ao console.  
  
> [!NOTE]
>  Você pode adicionar restrições de política a quaisquer atividades. Por exemplo, você pode adicionar uma restrição de política a uma atividade de <xref:System.Activities.Statements.Sequence> ou de <xref:System.Activities.Statements.Parallel> .  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de ExternalActivityValidation.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione Ctrl+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`