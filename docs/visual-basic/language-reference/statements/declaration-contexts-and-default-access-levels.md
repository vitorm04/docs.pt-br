---
title: "Contextos de declaração e padrão de acesso a níveis (Visual Basic) | Documentos do Microsoft"
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
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: 8
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
ms.openlocfilehash: a8f571ab0370a20a28028363533e1da56dffbaa6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a><span data-ttu-id="69568-102">Contextos de declaração e níveis de acesso padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69568-102">Declaration Contexts and Default Access Levels (Visual Basic)</span></span>
<span data-ttu-id="69568-103">Este tópico descreve quais tipos de Visual Basic podem ser declarados no quais outros tipos, e o que os níveis de acesso padrão se não especificado.</span><span class="sxs-lookup"><span data-stu-id="69568-103">This topic describes which Visual Basic types can be declared within which other types, and what their access levels default to if not specified.</span></span>  
  
## <a name="declaration-context-levels"></a><span data-ttu-id="69568-104">Níveis de contexto de declaração</span><span class="sxs-lookup"><span data-stu-id="69568-104">Declaration Context Levels</span></span>  
 <span data-ttu-id="69568-105">O *contexto declaração* de um elemento de programação é a região de código no qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="69568-105">The *declaration context* of a programming element is the region of code in which it is declared.</span></span> <span data-ttu-id="69568-106">Isso geralmente é outro elemento de programação, que é chamado de *que contém o elemento*.</span><span class="sxs-lookup"><span data-stu-id="69568-106">This is often another programming element, which is then called the *containing element*.</span></span>  
  
 <span data-ttu-id="69568-107">Os níveis de contextos de declaração são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="69568-107">The levels for declaration contexts are the following:</span></span>  
  
-   <span data-ttu-id="69568-108">*Nível de Namespace* — dentro de um namespace ou arquivo de origem, mas não dentro de uma classe, estrutura, módulo ou interface</span><span class="sxs-lookup"><span data-stu-id="69568-108">*Namespace level* — within a source file or namespace but not within a class, structure, module, or interface</span></span>  
  
-   <span data-ttu-id="69568-109">*Nível de módulo* — dentro de uma classe, estrutura, módulo ou interface, mas não dentro de um procedimento ou bloco</span><span class="sxs-lookup"><span data-stu-id="69568-109">*Module level* — within a class, structure, module, or interface but not within a procedure or block</span></span>  
  
-   <span data-ttu-id="69568-110">*Nível de procedimento* — dentro de um procedimento ou bloco (como `If` ou `For`)</span><span class="sxs-lookup"><span data-stu-id="69568-110">*Procedure level* — within a procedure or block (such as `If` or `For`)</span></span>  
  
 <span data-ttu-id="69568-111">A tabela a seguir mostra os níveis de acesso padrão para vários elementos de programação declarados, dependendo de seus contextos de declaração.</span><span class="sxs-lookup"><span data-stu-id="69568-111">The following table shows the default access levels for various declared programming elements, depending on their declaration contexts.</span></span>  
  
|<span data-ttu-id="69568-112">Elementos declarados</span><span class="sxs-lookup"><span data-stu-id="69568-112">Declared element</span></span>|<span data-ttu-id="69568-113">Nível de Namespace</span><span class="sxs-lookup"><span data-stu-id="69568-113">Namespace level</span></span>|<span data-ttu-id="69568-114">Nível de módulo</span><span class="sxs-lookup"><span data-stu-id="69568-114">Module level</span></span>|<span data-ttu-id="69568-115">Nível de procedimento</span><span class="sxs-lookup"><span data-stu-id="69568-115">Procedure level</span></span>|  
|----------------------|---------------------|------------------|---------------------|  
|<span data-ttu-id="69568-116">Variável ([instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-116">Variable ([Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md))</span></span>|<span data-ttu-id="69568-117">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-117">Not allowed</span></span>|<span data-ttu-id="69568-118">`Private`(`Public` na `Structure`, não é permitido em `Interface`)</span><span class="sxs-lookup"><span data-stu-id="69568-118">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="69568-119">Constante ([instrução Const](../../../visual-basic/language-reference/statements/const-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-119">Constant ([Const Statement](../../../visual-basic/language-reference/statements/const-statement.md))</span></span>|<span data-ttu-id="69568-120">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-120">Not allowed</span></span>|<span data-ttu-id="69568-121">`Private`(`Public` na `Structure`, não é permitido em `Interface`)</span><span class="sxs-lookup"><span data-stu-id="69568-121">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="69568-122">Enumeração ([instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-122">Enumeration ([Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="69568-123">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-123">Not allowed</span></span>|  
|<span data-ttu-id="69568-124">Classe ([instrução Class](../../../visual-basic/language-reference/statements/class-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-124">Class ([Class Statement](../../../visual-basic/language-reference/statements/class-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="69568-125">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-125">Not allowed</span></span>|  
|<span data-ttu-id="69568-126">Estrutura ([estrutura instrução](../../../visual-basic/language-reference/statements/structure-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-126">Structure ([Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="69568-127">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-127">Not allowed</span></span>|  
|<span data-ttu-id="69568-128">Módulo ([instrução módulo](../../../visual-basic/language-reference/statements/module-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-128">Module ([Module Statement](../../../visual-basic/language-reference/statements/module-statement.md))</span></span>|`Friend`|<span data-ttu-id="69568-129">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-129">Not allowed</span></span>|<span data-ttu-id="69568-130">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-130">Not allowed</span></span>|  
|<span data-ttu-id="69568-131">Interface ([instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-131">Interface ([Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="69568-132">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-132">Not allowed</span></span>|  
|<span data-ttu-id="69568-133">Procedimento ([declaração de função](../../../visual-basic/language-reference/statements/function-statement.md), [Sub instrução](../../../visual-basic/language-reference/statements/sub-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-133">Procedure ([Function Statement](../../../visual-basic/language-reference/statements/function-statement.md), [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md))</span></span>|<span data-ttu-id="69568-134">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-134">Not allowed</span></span>|`Public`|<span data-ttu-id="69568-135">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-135">Not allowed</span></span>|  
|<span data-ttu-id="69568-136">Referência externa ([instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-136">External reference ([Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md))</span></span>|<span data-ttu-id="69568-137">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-137">Not allowed</span></span>|<span data-ttu-id="69568-138">`Public`(não permitido em `Interface`)</span><span class="sxs-lookup"><span data-stu-id="69568-138">`Public` (not allowed in `Interface`)</span></span>|<span data-ttu-id="69568-139">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-139">Not allowed</span></span>|  
|<span data-ttu-id="69568-140">Operador ([instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-140">Operator ([Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md))</span></span>|<span data-ttu-id="69568-141">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-141">Not allowed</span></span>|<span data-ttu-id="69568-142">`Public`(não permitido em `Interface` ou `Module`)</span><span class="sxs-lookup"><span data-stu-id="69568-142">`Public` (not allowed in `Interface` or `Module`)</span></span>|<span data-ttu-id="69568-143">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-143">Not allowed</span></span>|  
|<span data-ttu-id="69568-144">Propriedade ([declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-144">Property ([Property Statement](../../../visual-basic/language-reference/statements/property-statement.md))</span></span>|<span data-ttu-id="69568-145">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-145">Not allowed</span></span>|`Public`|<span data-ttu-id="69568-146">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-146">Not allowed</span></span>|  
|<span data-ttu-id="69568-147">Propriedade padrão ([padrão](../../../visual-basic/language-reference/modifiers/default.md))</span><span class="sxs-lookup"><span data-stu-id="69568-147">Default property ([Default](../../../visual-basic/language-reference/modifiers/default.md))</span></span>|<span data-ttu-id="69568-148">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-148">Not allowed</span></span>|<span data-ttu-id="69568-149">`Public`(não permitido em `Module`)</span><span class="sxs-lookup"><span data-stu-id="69568-149">`Public` (not allowed in `Module`)</span></span>|<span data-ttu-id="69568-150">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-150">Not allowed</span></span>|  
|<span data-ttu-id="69568-151">Evento ([instrução Event](../../../visual-basic/language-reference/statements/event-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-151">Event ([Event Statement](../../../visual-basic/language-reference/statements/event-statement.md))</span></span>|<span data-ttu-id="69568-152">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-152">Not allowed</span></span>|`Public`|<span data-ttu-id="69568-153">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-153">Not allowed</span></span>|  
|<span data-ttu-id="69568-154">Delegado ([instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md))</span><span class="sxs-lookup"><span data-stu-id="69568-154">Delegate ([Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="69568-155">Não permitido</span><span class="sxs-lookup"><span data-stu-id="69568-155">Not allowed</span></span>|  
  
 <span data-ttu-id="69568-156">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="69568-156">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69568-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69568-157">See Also</span></span>  
 <span data-ttu-id="69568-158">[Friend](../../../visual-basic/language-reference/modifiers/friend.md) </span><span class="sxs-lookup"><span data-stu-id="69568-158">[Friend](../../../visual-basic/language-reference/modifiers/friend.md) </span></span>  
<span data-ttu-id="69568-159"> [Privado](../../../visual-basic/language-reference/modifiers/private.md) </span><span class="sxs-lookup"><span data-stu-id="69568-159"> [Private](../../../visual-basic/language-reference/modifiers/private.md) </span></span>  
<span data-ttu-id="69568-160"> [Público](../../../visual-basic/language-reference/modifiers/public.md)</span><span class="sxs-lookup"><span data-stu-id="69568-160"> [Public](../../../visual-basic/language-reference/modifiers/public.md)</span></span>
