---
title: Escolher atividade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: edc9e285faab064b8552263bd48e6d2ad43d5ec2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="pick-activity"></a>Escolher atividade
A atividade de <xref:System.Activities.Statements.Pick> simplifica a modelagem de um conjunto de disparadores de evento seguidos por seus manipuladores correspondentes.  Uma atividade de <xref:System.Activities.Statements.Pick> contém uma coleção de atividades de <xref:System.Activities.Statements.PickBranch> , onde cada <xref:System.Activities.Statements.PickBranch> é um emparelhamento entre uma atividade de <xref:System.Activities.Statements.PickBranch.Trigger%2A> e uma atividade de <xref:System.Activities.Statements.PickBranch.Action%2A> .  Em tempo de execução, disparadores para todos as ramificações são executados paralelamente.  Quando um disparador for concluída, então a ação correspondente é executada, e todos outros disparadores são canceladas.  O comportamento do [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> atividade é semelhante do [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> atividade.  
  
 Captura de tela a seguir do [usando a atividade escolher](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) amostra do SDK mostra uma atividade de separar com duas ramificações.  Uma ramificação tem um gatilho chamado **entrada leitura**, uma atividade personalizada que lê a entrada da linha de comando. O segundo ramificação tem um disparador de atividade de <xref:System.Activities.Statements.Delay> . Se o **entrada leitura** atividade recebe os dados antes do <xref:System.Activities.Statements.Delay> concluir a atividade, <xref:System.Activities.Statements.Delay> atraso será cancelado e uma mensagem será gravada no console.  Caso contrário, se o **entrada leitura** atividade não recebe dados no tempo alocado, em seguida, ela será cancelada e uma mensagem de tempo limite será gravada no console.  Este é um padrão comum usado para adicionar um tempo limite a qualquer ação.  
  
 ![Escolher atividade](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Ao usar a picareta, a ramificação que executa é a ramificação cujo disparador for concluído primeiro.  Conceitualmente, todos os disparadores executam paralelamente, e um disparador pode ter executado a maioria de sua lógica antes de ser cancelado pela conclusão de um outro disparador.  Com isso em mente, uma orientação então quando usar a atividade de picareta é manipular o disparador como representação de um único evento, e a colocar como pouca lógica como possível nele.  Idealmente, o disparador deve conter apenas lógica suficiente para receber um evento, e qualquer processamento do evento deve entrar em ação de ramificação.  Este método minimiza a quantidade de sobreposição entre a execução de disparadores.  Por exemplo, considere <xref:System.Activities.Statements.Pick> com dois disparadores, onde cada disparador contém uma atividade de <xref:System.ServiceModel.Activities.Receive> seguido pela lógica adicional.  Se a lógica adicional apresenta um ponto ocioso, então existem a possibilidade de ambas as atividades de <xref:System.ServiceModel.Activities.Receive> que concluírem com êxito.  Um disparador concluirá totalmente, quando outro concluirá parcialmente.  Em alguns cenários, aceitar uma mensagem, e então concluir parcialmente o processamento delas são inaceitáveis.  Portanto, ao usar atividades internos de mensagem de WF como <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>, quando <xref:System.ServiceModel.Activities.Receive> são comumente usadas no disparador, <xref:System.ServiceModel.Activities.SendReply> e a outra lógica deve ser colocado em ação sempre que possível.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Usando a atividade de picareta no designer  
 Para usar Pick no designer, localize **escolher** e **PickBranch** na caixa de ferramentas.  Arrastar e soltar **escolher** para a tela.  Por padrão, um novo **escolher** atividade no designer conterá duas ramificações.  Para adicionar mais ramificações, arraste o **PickBranch** atividade e solte-o ao lado de ramificações existentes. Atividades podem ser descartadas até o **escolher** atividade em um a **gatilho** área ou **ação** área de qualquer **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Usando a atividade de picareta no código  
 A atividade de <xref:System.Activities.Statements.Pick> é usada preenchendo sua coleção de <xref:System.Activities.Statements.Pick.Branches%2A> com atividades de <xref:System.Activities.Statements.PickBranch> . As atividades cada um de <xref:System.Activities.Statements.PickBranch> possuem uma propriedade de <xref:System.Activities.Statements.PickBranch.Trigger%2A> de tipo <xref:System.Activities.Activity>. Quando a atividade especificada concluir a execução, <xref:System.Activities.Statements.PickBranch.Action%2A> executa.  
  
 O exemplo de código demonstra como usar uma atividade de <xref:System.Activities.Statements.Pick> para implementar um tempo limite para uma atividade que lê uma linha de console.  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
