---
title: Validação básica
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539467"
---
# <a name="basic-validation"></a><span data-ttu-id="4bb87-102">Validação básica</span><span class="sxs-lookup"><span data-stu-id="4bb87-102">Basic Validation</span></span>
<span data-ttu-id="4bb87-103">Esse exemplo consiste em uma atividade, `CreateProduct`, que valida que o argumento de `Cost` é menor que ou igual ao seu argumento de `Price` .</span><span class="sxs-lookup"><span data-stu-id="4bb87-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="4bb87-104">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="4bb87-104">Sample Details</span></span>  
 <span data-ttu-id="4bb87-105">Há dois autores que usam a validação, o autor de atividade (cria a lógica de validação para atividades) e o autor de fluxo de trabalho que chama serviços de validação em um fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="4bb87-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="4bb87-106">Nesse cenário, o autor de atividade deseja impor que cada instância da atividade deve ter um custo iguais ou menores do que a do preço.</span><span class="sxs-lookup"><span data-stu-id="4bb87-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="4bb87-107">O autor de atividade (dentro da atividade) deve:</span><span class="sxs-lookup"><span data-stu-id="4bb87-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="4bb87-108">Criar uma restrição (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="4bb87-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="4bb87-109">Isso é onde qualquer lógica de validação reside.</span><span class="sxs-lookup"><span data-stu-id="4bb87-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="4bb87-110">Substitua o `System.Activities.CodeActivity.OnGetConstraints()` e adicione a restrição (`PriceGreaterThanCost`) às restrições <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="4bb87-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="4bb87-111">O autor de fluxo de trabalho (programa principal) deve:</span><span class="sxs-lookup"><span data-stu-id="4bb87-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="4bb87-112">Crie um fluxo de trabalho com uma instância de atividade para validar (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="4bb87-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="4bb87-113">Chamar <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, que retorna uma coleção de <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="4bb87-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="4bb87-114">(Opcional) imprima os objetos de <xref:System.Activities.Validation.ValidationError> .</span><span class="sxs-lookup"><span data-stu-id="4bb87-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4bb87-115">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4bb87-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4bb87-116">Abra a solução de exemplo de BasicValidation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bb87-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="4bb87-117">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="4bb87-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4bb87-118">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4bb87-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4bb87-119">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4bb87-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4bb87-120">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4bb87-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4bb87-121">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4bb87-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`