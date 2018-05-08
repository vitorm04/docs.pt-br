---
title: Composição básica de atividades
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: 67cdad30c60ebbeaf546d7086c6e895fa49a51c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="basic-activity-composition"></a>Composição básica de atividades
Este exemplo demonstra como composto atividades personalizados e sistema forneceu atividades para criar uma atividades mais personalizados.  
  
 O fluxo de trabalho usando as agendas de atividade de pesquisa a pesquisa com uma lista de perguntas e em seguida, de saída que as respostas recebiam.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Este exemplo usa três atividades personalizados. `ReadLine` é um simples <xref:System.Activities.NativeActivity> \<cadeia de caracteres > que cria um <xref:System.Activities.Bookmark> quando agendado e, em seguida, define o `Return` <xref:System.Activities.OutArgument%601> para o valor com o qual o <xref:System.Activities.Bookmark> é retomado. `Prompt` é um <xref:System.Activities.Activity%601> \<cadeia de caracteres > que leva um <xref:System.Activities.InArgument%601>< cadeia de caracteres\> chamado `Text` e retorna os usuários a resposta no `Result` <xref:System.Activities.OutArgument%601> \<cadeia de caracteres >. A atividade de `Prompt` usa as atividades de <xref:System.Activities.Statements.Sequence> e de <xref:System.Activities.Statements.WriteLine> fornecidos como parte do .NET Framework, e também inserir a atividade personalizado de `ReadLine` para obter a entrada do usuário. A atividade personalizado a última da atividade é `Survey` . É um <xref:System.Activities.Activity>< ICollection\<cadeia de caracteres >>.  Essa atividade tem um <xref:System.Activities.InArgument%601>< IEnumerable < cadeia de caracteres\>> denominado `Questions` e preenche o `Result` out argumento com as respostas. A atividade de `Survey` usa <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> e <xref:System.Activities.Statements.AddToCollection%601> do .NET Framework e emprega a atividade de `Prompt` para fazer as perguntas de pesquisa e obter respostas.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **BasicActivityComposition.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`