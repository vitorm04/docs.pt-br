---
title: "Configurando a validação de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 440f3ee85fe24707c6bb433736bf6104d9e0dfc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="1654d-102">Configurando a validação de atividades</span><span class="sxs-lookup"><span data-stu-id="1654d-102">Configuring Activity Validation</span></span>
<span data-ttu-id="1654d-103">Validação de atividade autores e permite que usuários da atividade para identificar e relatar erros na configuração de uma atividade antes da execução.</span><span class="sxs-lookup"><span data-stu-id="1654d-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="1654d-104"> fornece os seguintes tipos de validação de atividade:</span><span class="sxs-lookup"><span data-stu-id="1654d-104"> provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="1654d-105">`RequiredArgument` e atributos de `OverloadGroup` .</span><span class="sxs-lookup"><span data-stu-id="1654d-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="1654d-106">Validação classe base imperativa.</span><span class="sxs-lookup"><span data-stu-id="1654d-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="1654d-107">Restrições declarativas.</span><span class="sxs-lookup"><span data-stu-id="1654d-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="1654d-108">`RequiredArgument` e atributos de `OverloadGroup` indicam que determinados argumentos em uma atividade são necessários.</span><span class="sxs-lookup"><span data-stu-id="1654d-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="1654d-109">A validação classe base imperativa fornece uma maneira simples para uma atividade fornece validação sobre se, e restrições declarativas permitem a validação sobre a atividade e sua relação com o fluxo de trabalho contém.</span><span class="sxs-lookup"><span data-stu-id="1654d-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="1654d-110">Se uma atividade não é configurado corretamente de acordo com os requisitos de validação, erros e avisos de validação são retornados.</span><span class="sxs-lookup"><span data-stu-id="1654d-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="1654d-111">Se um trabalho de que são criados usando o designer de trabalho, todos os erros e avisos de validação são exibidos no designer.</span><span class="sxs-lookup"><span data-stu-id="1654d-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="1654d-112">Se o trabalho são criados fora do designer de trabalho todos os erros de validação são retornados quando o fluxo de trabalho é chamado.</span><span class="sxs-lookup"><span data-stu-id="1654d-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="1654d-113">Independentemente de como funciona foram criados, um trabalho com erros de validação são permitidos nunca executar.</span><span class="sxs-lookup"><span data-stu-id="1654d-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="1654d-114">Esta seção fornece uma visão geral desses tipos de validação de atividade e como validação de atividade é chamada.</span><span class="sxs-lookup"><span data-stu-id="1654d-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1654d-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1654d-115">In This Section</span></span>  
 [<span data-ttu-id="1654d-116">Argumentos necessários e grupos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="1654d-116">Required Arguments and Overload Groups</span></span>](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 <span data-ttu-id="1654d-117">Descreve como usar atributos de `RequiredArgument` e de `OverloadGroup` para fornecer validação.</span><span class="sxs-lookup"><span data-stu-id="1654d-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="1654d-118">Validação baseada em código obrigatório</span><span class="sxs-lookup"><span data-stu-id="1654d-118">Imperative Code-Based Validation</span></span>](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <span data-ttu-id="1654d-119">Descreve como usar a validação classe base para <xref:System.Activities.CodeActivity> e atividades com base <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="1654d-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="1654d-120">Restrições declarativas</span><span class="sxs-lookup"><span data-stu-id="1654d-120">Declarative Constraints</span></span>](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 <span data-ttu-id="1654d-121">Descreve como usar restrições declarativas para fornecer validação complexa de atividade.</span><span class="sxs-lookup"><span data-stu-id="1654d-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="1654d-122">Invocando a validação de atividades</span><span class="sxs-lookup"><span data-stu-id="1654d-122">Invoking Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 <span data-ttu-id="1654d-123">Discute quando a validação de atividade é chamado automaticamente e como chamar explicitamente validação.</span><span class="sxs-lookup"><span data-stu-id="1654d-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1654d-124">Referência</span><span class="sxs-lookup"><span data-stu-id="1654d-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1654d-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1654d-125">Related Sections</span></span>
