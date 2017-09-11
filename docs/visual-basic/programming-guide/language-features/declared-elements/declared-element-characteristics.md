---
title: "Declarado características do elemento (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, lifetime
- access levels, declared elements
- declared elements, scope
- visibility, declared elements
- elements, programming
- scope, declared elements
- lifetime, declared elements
- declared elements, access level
- data types [Visual Basic], declared elements
- declared elements, visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 23f8b3f19c55773b67678afa0c1b8dcf73cb272f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="declared-element-characteristics-visual-basic"></a><span data-ttu-id="e443c-102">Características do elemento declarado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e443c-102">Declared Element Characteristics (Visual Basic)</span></span>
<span data-ttu-id="e443c-103">A *característica* de um elemento declarado é um aspecto do elemento que afeta como o código pode interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="e443c-103">A *characteristic* of a declared element is an aspect of that element that affects how code can interact with it.</span></span> <span data-ttu-id="e443c-104">Cada elemento declarado tem um ou mais das seguintes características associadas a ele:</span><span class="sxs-lookup"><span data-stu-id="e443c-104">Every declared element has one or more of the following characteristics associated with it:</span></span>  
  
-   <span data-ttu-id="e443c-105">*Tipo de dados* — os valores de elemento pode conter, e como ela armazena esses valores.</span><span class="sxs-lookup"><span data-stu-id="e443c-105">*Data type* — the values the element can hold, and how it stores those values.</span></span> <span data-ttu-id="e443c-106">Para obter mais informações, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="e443c-106">For more information, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
-   <span data-ttu-id="e443c-107">*Tempo de vida* — o período de tempo de execução durante o qual o elemento está disponível para uso.</span><span class="sxs-lookup"><span data-stu-id="e443c-107">*Lifetime* — the period of execution time during which the element is available for use.</span></span> <span data-ttu-id="e443c-108">Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="e443c-108">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
-   <span data-ttu-id="e443c-109">*Escopo* — o conjunto de todos os códigos que podem se referir ao elemento sem qualificar seu nome.</span><span class="sxs-lookup"><span data-stu-id="e443c-109">*Scope* — the set of all code that can refer to the element without qualifying its name.</span></span> <span data-ttu-id="e443c-110">Para obter mais informações, consulte [como: controlar o escopo de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="e443c-110">For more information, see [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md).</span></span>  
  
-   <span data-ttu-id="e443c-111">*Nível de acesso* — a permissão para o código fazer uso do elemento.</span><span class="sxs-lookup"><span data-stu-id="e443c-111">*Access level* — the permission for code to make use of the element.</span></span> <span data-ttu-id="e443c-112">Para obter mais informações, consulte [como: controlar a disponibilidade de uma variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="e443c-112">For more information, see [How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md).</span></span>  
  
## <a name="characteristics-of-the-elements"></a><span data-ttu-id="e443c-113">Características dos elementos</span><span class="sxs-lookup"><span data-stu-id="e443c-113">Characteristics of the Elements</span></span>  
 <span data-ttu-id="e443c-114">A tabela a seguir mostra os elementos declarados e as características que se aplicam a cada um deles.</span><span class="sxs-lookup"><span data-stu-id="e443c-114">The following table shows the declared elements and the characteristics that apply to each one.</span></span>  
  
|<span data-ttu-id="e443c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e443c-115">Element</span></span>|<span data-ttu-id="e443c-116">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e443c-116">Data Type</span></span>|<span data-ttu-id="e443c-117">Tempo de vida</span><span class="sxs-lookup"><span data-stu-id="e443c-117">Lifetime</span></span>|<span data-ttu-id="e443c-118">Escopo <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e443c-118">Scope <sup>1</sup></span></span>|<span data-ttu-id="e443c-119">Nível de acesso</span><span class="sxs-lookup"><span data-stu-id="e443c-119">Access Level</span></span>|  
|-------------|---------------|--------------|------------------------|------------------|  
|<span data-ttu-id="e443c-120">Variável</span><span class="sxs-lookup"><span data-stu-id="e443c-120">Variable</span></span>|<span data-ttu-id="e443c-121">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-121">Yes</span></span>|<span data-ttu-id="e443c-122">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-122">Yes</span></span>|<span data-ttu-id="e443c-123">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-123">Yes</span></span>|<span data-ttu-id="e443c-124">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-124">Yes</span></span>|  
|<span data-ttu-id="e443c-125">Constante</span><span class="sxs-lookup"><span data-stu-id="e443c-125">Constant</span></span>|<span data-ttu-id="e443c-126">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-126">Yes</span></span>|<span data-ttu-id="e443c-127">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-127">No</span></span>|<span data-ttu-id="e443c-128">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-128">Yes</span></span>|<span data-ttu-id="e443c-129">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-129">Yes</span></span>|  
|<span data-ttu-id="e443c-130">Enumeração</span><span class="sxs-lookup"><span data-stu-id="e443c-130">Enumeration</span></span>|<span data-ttu-id="e443c-131">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-131">Yes</span></span>|<span data-ttu-id="e443c-132">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-132">No</span></span>|<span data-ttu-id="e443c-133">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-133">Yes</span></span>|<span data-ttu-id="e443c-134">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-134">Yes</span></span>|  
|<span data-ttu-id="e443c-135">Estrutura</span><span class="sxs-lookup"><span data-stu-id="e443c-135">Structure</span></span>|<span data-ttu-id="e443c-136">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-136">No</span></span>|<span data-ttu-id="e443c-137">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-137">No</span></span>|<span data-ttu-id="e443c-138">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-138">Yes</span></span>|<span data-ttu-id="e443c-139">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-139">Yes</span></span>|  
|<span data-ttu-id="e443c-140">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e443c-140">Property</span></span>|<span data-ttu-id="e443c-141">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-141">Yes</span></span>|<span data-ttu-id="e443c-142">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-142">Yes</span></span>|<span data-ttu-id="e443c-143">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-143">Yes</span></span>|<span data-ttu-id="e443c-144">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-144">Yes</span></span>|  
|<span data-ttu-id="e443c-145">Método</span><span class="sxs-lookup"><span data-stu-id="e443c-145">Method</span></span>|<span data-ttu-id="e443c-146">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-146">No</span></span>|<span data-ttu-id="e443c-147">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-147">Yes</span></span>|<span data-ttu-id="e443c-148">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-148">Yes</span></span>|<span data-ttu-id="e443c-149">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-149">Yes</span></span>|  
|<span data-ttu-id="e443c-150">Procedimento (`Sub` ou `Function`)</span><span class="sxs-lookup"><span data-stu-id="e443c-150">Procedure (`Sub` or `Function`)</span></span>|<span data-ttu-id="e443c-151">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-151">No</span></span>|<span data-ttu-id="e443c-152">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-152">Yes</span></span>|<span data-ttu-id="e443c-153">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-153">Yes</span></span>|<span data-ttu-id="e443c-154">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-154">Yes</span></span>|  
|<span data-ttu-id="e443c-155">Parâmetro de procedimento</span><span class="sxs-lookup"><span data-stu-id="e443c-155">Procedure parameter</span></span>|<span data-ttu-id="e443c-156">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-156">Yes</span></span>|<span data-ttu-id="e443c-157">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-157">Yes</span></span>|<span data-ttu-id="e443c-158">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-158">Yes</span></span>|<span data-ttu-id="e443c-159">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-159">No</span></span>|  
|<span data-ttu-id="e443c-160">Retorno de função</span><span class="sxs-lookup"><span data-stu-id="e443c-160">Function return</span></span>|<span data-ttu-id="e443c-161">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-161">Yes</span></span>|<span data-ttu-id="e443c-162">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-162">Yes</span></span>|<span data-ttu-id="e443c-163">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-163">Yes</span></span>|<span data-ttu-id="e443c-164">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-164">No</span></span>|  
|<span data-ttu-id="e443c-165">Operador</span><span class="sxs-lookup"><span data-stu-id="e443c-165">Operator</span></span>|<span data-ttu-id="e443c-166">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-166">Yes</span></span>|<span data-ttu-id="e443c-167">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-167">No</span></span>|<span data-ttu-id="e443c-168">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-168">Yes</span></span>|<span data-ttu-id="e443c-169">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-169">Yes</span></span>|  
|<span data-ttu-id="e443c-170">Interface</span><span class="sxs-lookup"><span data-stu-id="e443c-170">Interface</span></span>|<span data-ttu-id="e443c-171">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-171">No</span></span>|<span data-ttu-id="e443c-172">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-172">No</span></span>|<span data-ttu-id="e443c-173">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-173">Yes</span></span>|<span data-ttu-id="e443c-174">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-174">Yes</span></span>|  
|<span data-ttu-id="e443c-175">Classe</span><span class="sxs-lookup"><span data-stu-id="e443c-175">Class</span></span>|<span data-ttu-id="e443c-176">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-176">No</span></span>|<span data-ttu-id="e443c-177">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-177">No</span></span>|<span data-ttu-id="e443c-178">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-178">Yes</span></span>|<span data-ttu-id="e443c-179">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-179">Yes</span></span>|  
|<span data-ttu-id="e443c-180">Evento</span><span class="sxs-lookup"><span data-stu-id="e443c-180">Event</span></span>|<span data-ttu-id="e443c-181">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-181">No</span></span>|<span data-ttu-id="e443c-182">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-182">No</span></span>|<span data-ttu-id="e443c-183">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-183">Yes</span></span>|<span data-ttu-id="e443c-184">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-184">Yes</span></span>|  
|<span data-ttu-id="e443c-185">Representante</span><span class="sxs-lookup"><span data-stu-id="e443c-185">Delegate</span></span>|<span data-ttu-id="e443c-186">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-186">No</span></span>|<span data-ttu-id="e443c-187">Não</span><span class="sxs-lookup"><span data-stu-id="e443c-187">No</span></span>|<span data-ttu-id="e443c-188">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-188">Yes</span></span>|<span data-ttu-id="e443c-189">Sim</span><span class="sxs-lookup"><span data-stu-id="e443c-189">Yes</span></span>|  
  
 <span data-ttu-id="e443c-190"><sup>1</sup> escopo é às vezes referido como *visibilidade*.</span><span class="sxs-lookup"><span data-stu-id="e443c-190"><sup>1</sup> Scope is sometimes referred to as *visibility*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e443c-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e443c-191">See Also</span></span>  
 <span data-ttu-id="e443c-192">[Elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-192">[Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md) </span></span>  
<span data-ttu-id="e443c-193"> [Nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-193"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="e443c-194"> [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-194"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="e443c-195"> [Tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-195"> [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span></span>  
<span data-ttu-id="e443c-196"> [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-196"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="e443c-197"> [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-197"> [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span></span>  
<span data-ttu-id="e443c-198"> [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="e443c-198"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="e443c-199"> [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)</span><span class="sxs-lookup"><span data-stu-id="e443c-199"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)</span></span>
