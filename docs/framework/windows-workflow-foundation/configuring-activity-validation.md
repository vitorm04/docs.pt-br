---
title: Configurando a validação de atividades
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 65928de1dc8b8d9914648463a136790c7978f53c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774134"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="ebd02-102">Configurando a validação de atividades</span><span class="sxs-lookup"><span data-stu-id="ebd02-102">Configuring Activity Validation</span></span>
<span data-ttu-id="ebd02-103">Validação de atividade autores e permite que usuários da atividade para identificar e relatar erros na configuração de uma atividade antes da execução.</span><span class="sxs-lookup"><span data-stu-id="ebd02-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="ebd02-104">Windows Workflow Foundation (WF) fornece os seguintes três tipos de validação de atividade:</span><span class="sxs-lookup"><span data-stu-id="ebd02-104">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="ebd02-105">`RequiredArgument` e atributos de `OverloadGroup` .</span><span class="sxs-lookup"><span data-stu-id="ebd02-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="ebd02-106">Validação classe base imperativa.</span><span class="sxs-lookup"><span data-stu-id="ebd02-106">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="ebd02-107">Restrições declarativas.</span><span class="sxs-lookup"><span data-stu-id="ebd02-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="ebd02-108">`RequiredArgument` e atributos de `OverloadGroup` indicam que determinados argumentos em uma atividade são necessários.</span><span class="sxs-lookup"><span data-stu-id="ebd02-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="ebd02-109">A validação classe base imperativa fornece uma maneira simples para uma atividade fornece validação sobre se, e restrições declarativas permitem a validação sobre a atividade e sua relação com o fluxo de trabalho contém.</span><span class="sxs-lookup"><span data-stu-id="ebd02-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="ebd02-110">Se uma atividade não é configurado corretamente de acordo com os requisitos de validação, erros e avisos de validação são retornados.</span><span class="sxs-lookup"><span data-stu-id="ebd02-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="ebd02-111">Se um trabalho de que são criados usando o designer de trabalho, todos os erros e avisos de validação são exibidos no designer.</span><span class="sxs-lookup"><span data-stu-id="ebd02-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="ebd02-112">Se o trabalho são criados fora do designer de trabalho todos os erros de validação são retornados quando o fluxo de trabalho é chamado.</span><span class="sxs-lookup"><span data-stu-id="ebd02-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="ebd02-113">Independentemente de como funciona foram criados, um trabalho com erros de validação são permitidos nunca executar.</span><span class="sxs-lookup"><span data-stu-id="ebd02-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="ebd02-114">Esta seção fornece uma visão geral desses tipos de validação de atividade e como validação de atividade é chamada.</span><span class="sxs-lookup"><span data-stu-id="ebd02-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebd02-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ebd02-115">In This Section</span></span>  
 [<span data-ttu-id="ebd02-116">Argumentos necessários e grupos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="ebd02-116">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="ebd02-117">Descreve como usar atributos de `RequiredArgument` e de `OverloadGroup` para fornecer validação.</span><span class="sxs-lookup"><span data-stu-id="ebd02-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="ebd02-118">Validação baseada em código obrigatório</span><span class="sxs-lookup"><span data-stu-id="ebd02-118">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="ebd02-119">Descreve como usar a validação classe base para <xref:System.Activities.CodeActivity> e atividades com base <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="ebd02-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="ebd02-120">Restrições declarativas</span><span class="sxs-lookup"><span data-stu-id="ebd02-120">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="ebd02-121">Descreve como usar restrições declarativas para fornecer validação complexa de atividade.</span><span class="sxs-lookup"><span data-stu-id="ebd02-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="ebd02-122">Invocando a validação de atividades</span><span class="sxs-lookup"><span data-stu-id="ebd02-122">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="ebd02-123">Discute quando a validação de atividade é chamado automaticamente e como chamar explicitamente validação.</span><span class="sxs-lookup"><span data-stu-id="ebd02-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ebd02-124">Referência</span><span class="sxs-lookup"><span data-stu-id="ebd02-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ebd02-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ebd02-125">Related Sections</span></span>
