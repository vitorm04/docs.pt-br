---
title: Particular (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d7935cf691d961591ff5e3d2a290afb88de9165a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="private-visual-basic"></a><span data-ttu-id="5da87-102">Particular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5da87-102">Private (Visual Basic)</span></span>
<span data-ttu-id="5da87-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, inclusive em todos os tipos contidos.</span><span class="sxs-lookup"><span data-stu-id="5da87-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5da87-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5da87-104">Remarks</span></span>  
 <span data-ttu-id="5da87-105">Se um elemento de programação representa funcionalidade proprietária, ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele estritamente possível.</span><span class="sxs-lookup"><span data-stu-id="5da87-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="5da87-106">Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que o define para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="5da87-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="5da87-107">Para limitar o acesso a um elemento dessa maneira, você pode declará-la com `Private`.</span><span class="sxs-lookup"><span data-stu-id="5da87-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5da87-108">Regras</span><span class="sxs-lookup"><span data-stu-id="5da87-108">Rules</span></span>  
  
-   <span data-ttu-id="5da87-109">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="5da87-109">**Declaration Context.**</span></span> <span data-ttu-id="5da87-110">Você pode usar `Private` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="5da87-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="5da87-111">Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="5da87-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5da87-112">Comportamento</span><span class="sxs-lookup"><span data-stu-id="5da87-112">Behavior</span></span>  
  
-   <span data-ttu-id="5da87-113">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="5da87-113">**Access Level.**</span></span> <span data-ttu-id="5da87-114">Todo código em um contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="5da87-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="5da87-115">Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="5da87-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="5da87-116">Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="5da87-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="5da87-117">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="5da87-117">**Access Modifiers.**</span></span> <span data-ttu-id="5da87-118">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="5da87-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="5da87-119">Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5da87-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="5da87-120">O `Private` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="5da87-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5da87-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="5da87-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="5da87-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="5da87-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="5da87-123">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="5da87-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="5da87-124">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="5da87-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="5da87-125">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="5da87-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="5da87-126">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="5da87-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="5da87-127">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="5da87-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="5da87-128">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="5da87-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5da87-129">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="5da87-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="5da87-130">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="5da87-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5da87-131">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="5da87-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="5da87-132">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="5da87-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5da87-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5da87-133">See Also</span></span>  
 [<span data-ttu-id="5da87-134">Público</span><span class="sxs-lookup"><span data-stu-id="5da87-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="5da87-135">Protegido</span><span class="sxs-lookup"><span data-stu-id="5da87-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="5da87-136">Friend</span><span class="sxs-lookup"><span data-stu-id="5da87-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="5da87-137">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5da87-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="5da87-138">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="5da87-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="5da87-139">Estruturas</span><span class="sxs-lookup"><span data-stu-id="5da87-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5da87-140">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="5da87-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
