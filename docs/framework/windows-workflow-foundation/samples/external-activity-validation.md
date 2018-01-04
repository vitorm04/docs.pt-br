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
ms.workload: dotnet
ms.openlocfilehash: da326969e622a51f6a93b9faf5f81da079ea4003
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="f50b2-102">Validação externo de atividades</span><span class="sxs-lookup"><span data-stu-id="f50b2-102">External Activity Validation</span></span>
<span data-ttu-id="f50b2-103">Este exemplo mostra como adicionar lógica de validação para uma atividade interno que não é do autor.</span><span class="sxs-lookup"><span data-stu-id="f50b2-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="f50b2-104">A lógica de validação consiste garantir que todas as atividades de <xref:System.Activities.Statements.If> atual no fluxo de trabalho têm sua propriedade hierarchical update definida <xref:System.Activities.Statements.If.Then%2A> ou seu conjunto de propriedades de <xref:System.Activities.Statements.If.Else%2A> .</span><span class="sxs-lookup"><span data-stu-id="f50b2-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="f50b2-105">Além disso, a lógica de validação inclui verifique se todas as atividades de <xref:System.Activities.Statements.Pick> atual no fluxo de trabalho têm mais de uma ramificação, e se isso não for o caso, um aviso é gerado.</span><span class="sxs-lookup"><span data-stu-id="f50b2-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f50b2-106">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="f50b2-106">Sample details</span></span>  
 <span data-ttu-id="f50b2-107">Este exemplo cria um fluxo de trabalho com uma instância de cada atividade para validar: a atividade de <xref:System.Activities.Statements.If> e a atividade de <xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="f50b2-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="f50b2-108"><xref:System.Activities.Validation.Constraint> é criado para cada comportamento de validação.</span><span class="sxs-lookup"><span data-stu-id="f50b2-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="f50b2-109">As restrições criadas nesse exemplo são `ConstraintError_IfShouldHaveThenOrElse` e `ConstraintWarning_PickHasOneBranch`.</span><span class="sxs-lookup"><span data-stu-id="f50b2-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="f50b2-110">Em seguida, essas restrições é adicionado à coleção de `AdditionalConstraints` de uma instância de <xref:System.Activities.Validation.ValidationSettings> .</span><span class="sxs-lookup"><span data-stu-id="f50b2-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="f50b2-111">Finalmente, o método de `static` de <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> de <xref:System.Activities.Validation.ActivityValidationServices> é chamado para validar as atividades no fluxo de trabalho e os resultados de validação são impresso - ao console.</span><span class="sxs-lookup"><span data-stu-id="f50b2-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f50b2-112">Você pode adicionar restrições de política a quaisquer atividades.</span><span class="sxs-lookup"><span data-stu-id="f50b2-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="f50b2-113">Por exemplo, você pode adicionar uma restrição de política a uma atividade de <xref:System.Activities.Statements.Sequence> ou de <xref:System.Activities.Statements.Parallel> .</span><span class="sxs-lookup"><span data-stu-id="f50b2-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f50b2-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="f50b2-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="f50b2-115">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de ExternalActivityValidation.sln.</span><span class="sxs-lookup"><span data-stu-id="f50b2-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="f50b2-116">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="f50b2-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f50b2-117">Para executar a solução, pressione Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="f50b2-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f50b2-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f50b2-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f50b2-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f50b2-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f50b2-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f50b2-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f50b2-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f50b2-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`