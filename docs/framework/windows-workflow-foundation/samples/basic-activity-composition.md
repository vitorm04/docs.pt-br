---
title: Composição básica de atividades
ms.date: 03/30/2017
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
ms.openlocfilehash: ade8187ca44a8182b55cf0f01e5bfe5a9a747255
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518370"
---
# <a name="basic-activity-composition"></a>Composição básica de atividades
Este exemplo demonstra como composto atividades personalizados e sistema forneceu atividades para criar uma atividades mais personalizados.  
  
 O fluxo de trabalho usando as agendas de atividade de pesquisa a pesquisa com uma lista de perguntas e em seguida, de saída que as respostas recebiam.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Este exemplo usa três atividades personalizados. `ReadLine` é uma simples <xref:System.Activities.NativeActivity> \<cadeia de caracteres > que cria um <xref:System.Activities.Bookmark> quando agendada e, em seguida, define o `Return` <xref:System.Activities.OutArgument%601> para o valor com o qual o <xref:System.Activities.Bookmark> é retomado. `Prompt` é um <xref:System.Activities.Activity%601> \<cadeia de caracteres > que usa um <xref:System.Activities.InArgument%601>< cadeia de caracteres\> denominada `Text` e retorna os usuários a resposta no `Result` <xref:System.Activities.OutArgument%601> \<cadeia de caracteres >. A atividade de `Prompt` usa as atividades de <xref:System.Activities.Statements.Sequence> e de <xref:System.Activities.Statements.WriteLine> fornecidos como parte do .NET Framework, e também inserir a atividade personalizado de `ReadLine` para obter a entrada do usuário. A atividade personalizado a última da atividade é `Survey` . É um <xref:System.Activities.Activity>< ICollection\<cadeia de caracteres >>.  Esta atividade leva um <xref:System.Activities.InArgument%601>< IEnumerable < cadeia de caracteres\>> denominado `Questions` e preenche o `Result` argumento com as respostas de saída. A atividade de `Survey` usa <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> e <xref:System.Activities.Statements.AddToCollection%601> do .NET Framework e emprega a atividade de `Prompt` para fazer as perguntas de pesquisa e obter respostas.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra o **Basicactivitycomposition** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Criar e executar a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`