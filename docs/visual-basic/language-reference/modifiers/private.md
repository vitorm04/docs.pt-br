---
title: Particular (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234549"
---
# <a name="private-visual-basic"></a><span data-ttu-id="33eb3-102">Particular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33eb3-102">Private (Visual Basic)</span></span>
<span data-ttu-id="33eb3-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, inclusive em todos os tipos contidos.</span><span class="sxs-lookup"><span data-stu-id="33eb3-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33eb3-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="33eb3-104">Remarks</span></span>  
 <span data-ttu-id="33eb3-105">Se um elemento de programação representa funcionalidade proprietária, ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele estritamente possível.</span><span class="sxs-lookup"><span data-stu-id="33eb3-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="33eb3-106">Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que o define para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="33eb3-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="33eb3-107">Para limitar o acesso a um elemento dessa maneira, você pode declará-la com `Private`.</span><span class="sxs-lookup"><span data-stu-id="33eb3-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="33eb3-108">Você também pode usar o [privada protegida](private-protected.md) modificador de acesso, o que torna a acessíveis a partir dentro dessa classe e de classes derivadas localizadas em seu assembly que contém um membro.</span><span class="sxs-lookup"><span data-stu-id="33eb3-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="33eb3-109">Regras</span><span class="sxs-lookup"><span data-stu-id="33eb3-109">Rules</span></span>  

-   <span data-ttu-id="33eb3-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="33eb3-110">**Declaration Context.**</span></span> <span data-ttu-id="33eb3-111">Você pode usar `Private` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="33eb3-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="33eb3-112">Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="33eb3-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="33eb3-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="33eb3-113">Behavior</span></span>  
  
-   <span data-ttu-id="33eb3-114">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="33eb3-114">**Access Level.**</span></span> <span data-ttu-id="33eb3-115">Todo código em um contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="33eb3-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="33eb3-116">Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="33eb3-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="33eb3-117">Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="33eb3-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="33eb3-118">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="33eb3-118">**Access Modifiers.**</span></span> <span data-ttu-id="33eb3-119">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="33eb3-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="33eb3-120">Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="33eb3-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="33eb3-121">O `Private` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="33eb3-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="33eb3-122">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="33eb3-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="33eb3-123">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="33eb3-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="33eb3-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="33eb3-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="33eb3-125">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="33eb3-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="33eb3-126">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="33eb3-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="33eb3-127">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="33eb3-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="33eb3-128">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="33eb3-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="33eb3-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="33eb3-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="33eb3-130">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="33eb3-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="33eb3-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="33eb3-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="33eb3-132">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="33eb3-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="33eb3-133">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="33eb3-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="33eb3-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33eb3-134">See Also</span></span>  
 [<span data-ttu-id="33eb3-135">Público</span><span class="sxs-lookup"><span data-stu-id="33eb3-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="33eb3-136">Protegido</span><span class="sxs-lookup"><span data-stu-id="33eb3-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="33eb3-137">Friend</span><span class="sxs-lookup"><span data-stu-id="33eb3-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 <span data-ttu-id="33eb3-138">[Privado protegido](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="33eb3-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="33eb3-139">[Protected Friend](./protected-friend.md)[acessar níveis no Visual Basic    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="33eb3-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>  
 [<span data-ttu-id="33eb3-140">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="33eb3-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="33eb3-141">Estruturas</span><span class="sxs-lookup"><span data-stu-id="33eb3-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="33eb3-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="33eb3-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
