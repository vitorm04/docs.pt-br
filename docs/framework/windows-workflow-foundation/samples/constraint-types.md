---
title: Tipos de restrições
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506606"
---
# <a name="constraint-types"></a><span data-ttu-id="3d407-102">Tipos de restrições</span><span class="sxs-lookup"><span data-stu-id="3d407-102">Constraint Types</span></span>
<span data-ttu-id="3d407-103">Este exemplo mostra duas maneiras diferentes de aplicar restrições em um fluxo de trabalho, um é de dentro da atividade (compilação) e uma estiver fora delas (diretiva).</span><span class="sxs-lookup"><span data-stu-id="3d407-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="3d407-104">Nesse cenário, um autor de atividade (de uma empresa software de 3rth-party) deseja validar a relação entre dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="3d407-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="3d407-105">Nesse caso, o custo devem ser menores do que ou igual ao preço.</span><span class="sxs-lookup"><span data-stu-id="3d407-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="3d407-106">Esta é uma restrição geral de compilação de validação.</span><span class="sxs-lookup"><span data-stu-id="3d407-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="3d407-107">Em um vendedor deseja adicionar alguma validação a esta atividade genérico.</span><span class="sxs-lookup"><span data-stu-id="3d407-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="3d407-108">Nos casos, desejar que a maioria dos produtos para ser $9,99 ou menos.</span><span class="sxs-lookup"><span data-stu-id="3d407-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="3d407-109">Assim, usa uma restrição de política que é sobre a atividade de `CreateProduct` .</span><span class="sxs-lookup"><span data-stu-id="3d407-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="3d407-110">No exemplo:</span><span class="sxs-lookup"><span data-stu-id="3d407-110">In the sample:</span></span>  
  
 <span data-ttu-id="3d407-111">O autor de atividade (compilação) deve:</span><span class="sxs-lookup"><span data-stu-id="3d407-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="3d407-112">Criar uma restrição (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="3d407-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="3d407-113">Isso é onde qualquer lógica de validação reside.</span><span class="sxs-lookup"><span data-stu-id="3d407-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="3d407-114">Substitua o `System.Activities.CodeActivity.OnGetConstraints()` e adicione a restrição (`PriceGreaterThanCost`) às restrições <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="3d407-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="3d407-115">O autor de fluxo de trabalho (diretiva) deve:</span><span class="sxs-lookup"><span data-stu-id="3d407-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="3d407-116">Crie um fluxo de trabalho com uma instância de atividade para validar (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="3d407-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="3d407-117">Criar uma restrição (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="3d407-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="3d407-118">Crie uma instância de <xref:System.Activities.Validation.ValidationSettings> (`validationSettings`) e adicione a restrição (`MaxPrice`) à coleção `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="3d407-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="3d407-119">Aqui o autor de fluxo de trabalho pode adicionar restrições de política a quaisquer atividades, como uma sequência ou uma paralela.</span><span class="sxs-lookup"><span data-stu-id="3d407-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="3d407-120">Chame o <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, que retorna uma coleção de <xref:System.Activities.Validation.ValidationResults> de objetos <xref:System.Activities.Validation.ValidationError> .</span><span class="sxs-lookup"><span data-stu-id="3d407-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="3d407-121">(Opcional) imprima os objetos de <xref:System.Activities.Validation.ValidationError> .</span><span class="sxs-lookup"><span data-stu-id="3d407-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d407-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3d407-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3d407-123">Abra a solução de exemplo de ConstraintTypes.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d407-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d407-124">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="3d407-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d407-125">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3d407-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3d407-126">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3d407-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d407-127">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3d407-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d407-128">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3d407-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`