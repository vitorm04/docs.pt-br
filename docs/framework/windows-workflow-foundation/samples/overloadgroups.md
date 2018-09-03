---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469863"
---
# <a name="overloadgroups"></a><span data-ttu-id="8aae2-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="8aae2-102">OverloadGroups</span></span>
<span data-ttu-id="8aae2-103">Esse exemplo consiste em uma atividade (`CreateLocation`), que tem duas características interessantes:</span><span class="sxs-lookup"><span data-stu-id="8aae2-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="8aae2-104">Tem alguns argumentos necessários e opcionais alguns.</span><span class="sxs-lookup"><span data-stu-id="8aae2-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="8aae2-105">Permite que o usuário escolha para fornecer um dos dois diferentes conjuntos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="8aae2-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="8aae2-106">Esses comportamentos é realizada usando esses dois recursos:</span><span class="sxs-lookup"><span data-stu-id="8aae2-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="8aae2-107">`[isRequired]` valida que uma propriedade específica de uma atividade é atribui, e se não, ele gerencie uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8aae2-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="8aae2-108">`[OverloadGroup]` une um conjunto de argumentos, para que o usuário de atividade pode escolher entre o uso de um conjunto ou outro.</span><span class="sxs-lookup"><span data-stu-id="8aae2-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="8aae2-109">O usuário não pode usar argumentos de grupos diferentes de sobrecarga na mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8aae2-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="8aae2-110">Após configurar fluxos de trabalho diferentes, chamada <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> que retorna uma coleção de <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="8aae2-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="8aae2-111">Imprima os objetos de <xref:System.Activities.Validation.Constraint> no console.</span><span class="sxs-lookup"><span data-stu-id="8aae2-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8aae2-112">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="8aae2-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8aae2-113">Abra o **Overloadgroups** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8aae2-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="8aae2-114">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="8aae2-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8aae2-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8aae2-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8aae2-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8aae2-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8aae2-117">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="8aae2-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8aae2-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8aae2-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
