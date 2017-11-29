---
title: "Validação das relações de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03ac8e41f8126c6b05eac82d143291a0de491969
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="6ec6d-102">Validação das relações de atividades</span><span class="sxs-lookup"><span data-stu-id="6ec6d-102">Activity Relationships Validation</span></span>
<span data-ttu-id="6ec6d-103">Esse exemplo consiste em três atividades, `CreateCity`, `CreateState`, e `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="6ec6d-104">`CreateCity` deve ser dentro de uma atividade de `CreateState` , e `CreateState` deve ser dentro de uma atividade de `CreateCountry` .</span><span class="sxs-lookup"><span data-stu-id="6ec6d-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="6ec6d-105">Com o propósito deste exemplo, a lógica de validação está no código para atividades de `CreateState` , e XAML para atividades de `CreateCity` .</span><span class="sxs-lookup"><span data-stu-id="6ec6d-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="6ec6d-106">Ambos tem o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="6ec6d-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fornece as três seguintes atividades auxiliar que permitem que o desenvolvedor valida relações entre atividades:</span><span class="sxs-lookup"><span data-stu-id="6ec6d-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="6ec6d-108">Fornece a coleção de todas as atividades que pertencem ao pai do nó atual</span><span class="sxs-lookup"><span data-stu-id="6ec6d-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="6ec6d-109">Fornece a coleção de todas as atividades que pertencem a subárvore do nó atual, excluindo o nó atual</span><span class="sxs-lookup"><span data-stu-id="6ec6d-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="6ec6d-110">Fornece a coleção de todas as atividades na mesma árvore que o nó atual</span><span class="sxs-lookup"><span data-stu-id="6ec6d-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="6ec6d-111">No exemplo, uma atividade de <xref:System.Activities.Statements.ForEach%601> é usada para andar através da coleção retornada por <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="6ec6d-112">Para cada elemento na coleção, o tipo é comparado a `CreateCountry` (ou a `CreateState` se `CreateCity` está sendo validada), e quando uma correspondência for encontrada o sinalizador do resultado é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="6ec6d-113">Finalmente, <xref:System.Activities.Validation.AssertValidation> é usado para gerar um erro de validação se o sinalizador do resultado é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="6ec6d-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="6ec6d-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="6ec6d-115">Abra a solução de exemplo de ContainmentValidation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ec6d-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6ec6d-116">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="6ec6d-117">O pressionar o CTRL + F5 para iniciar o programa.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ec6d-118">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6ec6d-119">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="6ec6d-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6ec6d-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="6ec6d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ec6d-121">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="6ec6d-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`  
  
## <a name="see-also"></a><span data-ttu-id="6ec6d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ec6d-122">See Also</span></span>
