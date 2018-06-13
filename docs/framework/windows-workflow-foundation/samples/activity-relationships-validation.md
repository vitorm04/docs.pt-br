---
title: Validação das relações de atividades
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: e6dd0e6a7b48444073ebae378e21c1b45977a1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515102"
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="64c3c-102">Validação das relações de atividades</span><span class="sxs-lookup"><span data-stu-id="64c3c-102">Activity Relationships Validation</span></span>
<span data-ttu-id="64c3c-103">Esse exemplo consiste em três atividades, `CreateCity`, `CreateState`, e `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="64c3c-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="64c3c-104">`CreateCity` deve ser dentro de uma atividade de `CreateState` , e `CreateState` deve ser dentro de uma atividade de `CreateCountry` .</span><span class="sxs-lookup"><span data-stu-id="64c3c-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="64c3c-105">Com o propósito deste exemplo, a lógica de validação está no código para atividades de `CreateState` , e XAML para atividades de `CreateCity` .</span><span class="sxs-lookup"><span data-stu-id="64c3c-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="64c3c-106">Ambos tem o mesmo comportamento.</span><span class="sxs-lookup"><span data-stu-id="64c3c-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="64c3c-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fornece as três seguintes atividades auxiliar que permitem que o desenvolvedor valida relações entre atividades:</span><span class="sxs-lookup"><span data-stu-id="64c3c-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="64c3c-108">Fornece a coleção de todas as atividades que pertencem ao pai do nó atual</span><span class="sxs-lookup"><span data-stu-id="64c3c-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="64c3c-109">Fornece a coleção de todas as atividades que pertencem a subárvore do nó atual, excluindo o nó atual</span><span class="sxs-lookup"><span data-stu-id="64c3c-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="64c3c-110">Fornece a coleção de todas as atividades na mesma árvore que o nó atual</span><span class="sxs-lookup"><span data-stu-id="64c3c-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="64c3c-111">No exemplo, uma atividade de <xref:System.Activities.Statements.ForEach%601> é usada para andar através da coleção retornada por <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="64c3c-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="64c3c-112">Para cada elemento na coleção, o tipo é comparado a `CreateCountry` (ou a `CreateState` se `CreateCity` está sendo validada), e quando uma correspondência for encontrada o sinalizador do resultado é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="64c3c-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="64c3c-113">Finalmente, <xref:System.Activities.Validation.AssertValidation> é usado para gerar um erro de validação se o sinalizador do resultado é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="64c3c-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="64c3c-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="64c3c-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="64c3c-115">Abra a solução de exemplo de ContainmentValidation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64c3c-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="64c3c-116">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="64c3c-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="64c3c-117">O pressionar o CTRL + F5 para iniciar o programa.</span><span class="sxs-lookup"><span data-stu-id="64c3c-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64c3c-118">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="64c3c-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="64c3c-119">Verificar o seguinte diretório (padrão) antes de continuar:</span><span class="sxs-lookup"><span data-stu-id="64c3c-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="64c3c-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="64c3c-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="64c3c-121">Este exemplo está no seguinte diretório:</span><span class="sxs-lookup"><span data-stu-id="64c3c-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
