---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a5ab416dc484dddc0b6aa0ec25757921815c723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="overloadgroups"></a><span data-ttu-id="3abe8-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="3abe8-102">OverloadGroups</span></span>
<span data-ttu-id="3abe8-103">Esse exemplo consiste em uma atividade (`CreateLocation`), que tem duas características interessantes:</span><span class="sxs-lookup"><span data-stu-id="3abe8-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="3abe8-104">Tem alguns argumentos necessários e opcionais alguns.</span><span class="sxs-lookup"><span data-stu-id="3abe8-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="3abe8-105">Permite que o usuário escolha para fornecer um dos dois diferentes conjuntos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="3abe8-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="3abe8-106">Esses comportamentos é realizada usando esses dois recursos:</span><span class="sxs-lookup"><span data-stu-id="3abe8-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="3abe8-107">`[isRequired]` valida que uma propriedade específica de uma atividade é atribui, e se não, ele gerencie uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3abe8-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="3abe8-108">`[OverloadGroup]` une um conjunto de argumentos, para que o usuário de atividade pode escolher entre o uso de um conjunto ou outro.</span><span class="sxs-lookup"><span data-stu-id="3abe8-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="3abe8-109">O usuário não pode usar argumentos de grupos diferentes de sobrecarga na mesma instância.</span><span class="sxs-lookup"><span data-stu-id="3abe8-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="3abe8-110">Depois de configurar diferentes fluxos de trabalho, chame <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> que retorna um <xref:System.Activities.Validation.ValidationResults> coleção de <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation`.</span><span class="sxs-lookup"><span data-stu-id="3abe8-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation`.</span></span> <span data-ttu-id="3abe8-111">Imprimir o <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation` objetos no console.</span><span class="sxs-lookup"><span data-stu-id="3abe8-111">Print the <!--zz <xref:System.Activities.Validation.ConstraintViolation>--> `System.Activities.Validation.ConstraintViolation` objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3abe8-112">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3abe8-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3abe8-113">Abra o **OverloadGroups.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3abe8-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3abe8-114">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="3abe8-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3abe8-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3abe8-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3abe8-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3abe8-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3abe8-117">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3abe8-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3abe8-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3abe8-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`  
  
## <a name="see-also"></a><span data-ttu-id="3abe8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3abe8-119">See Also</span></span>
