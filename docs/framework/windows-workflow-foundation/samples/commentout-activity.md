---
title: Atividade de CommentOut
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 900f6647eadb04a783fe0a3a143a71d9c766a48c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="commentout-activity"></a><span data-ttu-id="14fb3-102">Atividade de CommentOut</span><span class="sxs-lookup"><span data-stu-id="14fb3-102">CommentOut Activity</span></span>
<span data-ttu-id="14fb3-103">Este exemplo demonstra como escrever uma atividade personalizado que remove outras atividades do caminho de execução, comentando efetivamente eles para fora.</span><span class="sxs-lookup"><span data-stu-id="14fb3-103">This sample demonstrates how to write a custom activity that removes other activities from the path of execution, effectively commenting them out.</span></span>  
  
## <a name="the-commentout-activity"></a><span data-ttu-id="14fb3-104">A atividade de CommentOut</span><span class="sxs-lookup"><span data-stu-id="14fb3-104">The CommentOut Activity</span></span>  
 <span data-ttu-id="14fb3-105">Para obter o objetivo, a atividade de CommentOut deriva de classe base de <xref:System.Activities.CodeActivity> e implementa-se um método vazia de <xref:System.Activities.CodeActivity.Execute%2A> .</span><span class="sxs-lookup"><span data-stu-id="14fb3-105">To achieve its goal, the CommentOut activity derives from the <xref:System.Activities.CodeActivity> base class and implements an empty <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 <span data-ttu-id="14fb3-106">A classe é declarada como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="14fb3-106">The class is declared as shown in the following example.</span></span>  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 <span data-ttu-id="14fb3-107">O atributo de `Designer` especifica a classe que implementa a interface visual de atividade em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="14fb3-107">The `Designer` attribute specifies the class that implements the visual interface of the activity at design time.</span></span> <span data-ttu-id="14fb3-108">O `ContentProperty` atributo declara que o `"Body"` propriedade pode ser ignorada na representação XAML de uma instância dessa atividade.</span><span class="sxs-lookup"><span data-stu-id="14fb3-108">The `ContentProperty` attribute declares that the `"Body"` property can be skipped in the XAML representation of an instance of this activity.</span></span>  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 <span data-ttu-id="14fb3-109">Na classe de designer, XAML é usado para criar uma representação visual personalizado de atividade.</span><span class="sxs-lookup"><span data-stu-id="14fb3-109">In the designer class, XAML is used to create a custom visual representation of the activity.</span></span> <span data-ttu-id="14fb3-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> é uma classe que fornece o editor visual.</span><span class="sxs-lookup"><span data-stu-id="14fb3-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> is a class that provides the visual editor.</span></span>  
  
 <span data-ttu-id="14fb3-111">Uma única atividade pode ser levada na superfície de atividade de `CommentOut` .</span><span class="sxs-lookup"><span data-stu-id="14fb3-111">A single activity can be dropped onto the `CommentOut` activity surface.</span></span> <span data-ttu-id="14fb3-112">Se você deseja adicionar vários atividades à superfície, arraste uma atividade da sequência aqui primeiro.</span><span class="sxs-lookup"><span data-stu-id="14fb3-112">If you want to add multiple activities to this surface, drag a sequence activity here first.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="14fb3-113">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="14fb3-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="14fb3-114">Abra CommentOut.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14fb3-114">Open CommentOut.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="14fb3-115">Crie a solução. CTRL+SHIFT+B pressionando.</span><span class="sxs-lookup"><span data-stu-id="14fb3-115">Compile the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="14fb3-116">Inicie o exemplo sem depuração pressionando CTRL + f5.</span><span class="sxs-lookup"><span data-stu-id="14fb3-116">Start the sample without debugging by pressing CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14fb3-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="14fb3-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14fb3-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="14fb3-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14fb3-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="14fb3-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14fb3-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="14fb3-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
