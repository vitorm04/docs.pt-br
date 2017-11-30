---
title: Particular (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="8503d-102">Particular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8503d-102">Private (Visual Basic)</span></span>
<span data-ttu-id="8503d-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, inclusive em todos os tipos contidos.</span><span class="sxs-lookup"><span data-stu-id="8503d-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8503d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="8503d-104">Remarks</span></span>  
 <span data-ttu-id="8503d-105">Se um elemento de programação representa funcionalidade proprietária, ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele estritamente possível.</span><span class="sxs-lookup"><span data-stu-id="8503d-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="8503d-106">Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que o define para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="8503d-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="8503d-107">Para limitar o acesso a um elemento dessa maneira, você pode declará-la com `Private`.</span><span class="sxs-lookup"><span data-stu-id="8503d-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8503d-108">Regras</span><span class="sxs-lookup"><span data-stu-id="8503d-108">Rules</span></span>  
  
-   <span data-ttu-id="8503d-109">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="8503d-109">**Declaration Context.**</span></span> <span data-ttu-id="8503d-110">Você pode usar `Private` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="8503d-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="8503d-111">Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="8503d-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8503d-112">Comportamento</span><span class="sxs-lookup"><span data-stu-id="8503d-112">Behavior</span></span>  
  
-   <span data-ttu-id="8503d-113">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="8503d-113">**Access Level.**</span></span> <span data-ttu-id="8503d-114">Todo código em um contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="8503d-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="8503d-115">Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="8503d-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="8503d-116">Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="8503d-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="8503d-117">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="8503d-117">**Access Modifiers.**</span></span> <span data-ttu-id="8503d-118">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="8503d-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="8503d-119">Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8503d-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="8503d-120">O `Private` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="8503d-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8503d-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="8503d-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="8503d-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="8503d-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="8503d-123">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="8503d-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="8503d-124">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="8503d-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="8503d-125">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="8503d-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="8503d-126">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="8503d-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="8503d-127">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="8503d-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="8503d-128">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="8503d-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8503d-129">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="8503d-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="8503d-130">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="8503d-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8503d-131">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="8503d-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="8503d-132">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="8503d-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8503d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8503d-133">See Also</span></span>  
 [<span data-ttu-id="8503d-134">Público</span><span class="sxs-lookup"><span data-stu-id="8503d-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="8503d-135">Protegido</span><span class="sxs-lookup"><span data-stu-id="8503d-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="8503d-136">Friend</span><span class="sxs-lookup"><span data-stu-id="8503d-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="8503d-137">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8503d-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="8503d-138">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="8503d-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="8503d-139">Estruturas</span><span class="sxs-lookup"><span data-stu-id="8503d-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="8503d-140">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="8503d-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
