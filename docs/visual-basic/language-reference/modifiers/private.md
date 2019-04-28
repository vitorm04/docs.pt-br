---
title: Particular (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920439"
---
# <a name="private-visual-basic"></a><span data-ttu-id="22435-102">Particular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22435-102">Private (Visual Basic)</span></span>
<span data-ttu-id="22435-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, inclusive em todos os tipos contidos.</span><span class="sxs-lookup"><span data-stu-id="22435-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22435-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="22435-104">Remarks</span></span>  
 <span data-ttu-id="22435-105">Se um elemento de programação representa a funcionalidade proprietária ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele tão restrito quanto possível.</span><span class="sxs-lookup"><span data-stu-id="22435-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="22435-106">Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que define-o para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="22435-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="22435-107">Para limitar o acesso a um elemento dessa forma, você pode declará-la com `Private`.</span><span class="sxs-lookup"><span data-stu-id="22435-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="22435-108">Você também pode usar o [Private Protected](private-protected.md) modificador de acesso, o que torna um membro acessível de dentro dessa classe e de classes derivadas localizadas no seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="22435-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="22435-109">Regras</span><span class="sxs-lookup"><span data-stu-id="22435-109">Rules</span></span>  

- <span data-ttu-id="22435-110">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="22435-110">**Declaration Context.**</span></span> <span data-ttu-id="22435-111">Você pode usar `Private` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="22435-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="22435-112">Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="22435-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="22435-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="22435-113">Behavior</span></span>  
  
- <span data-ttu-id="22435-114">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="22435-114">**Access Level.**</span></span> <span data-ttu-id="22435-115">Todo o código em um contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="22435-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="22435-116">Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="22435-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="22435-117">Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="22435-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="22435-118">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="22435-118">**Access Modifiers.**</span></span> <span data-ttu-id="22435-119">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="22435-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="22435-120">Para obter uma comparação os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="22435-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="22435-121">O `Private` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="22435-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="22435-122">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="22435-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="22435-123">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="22435-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="22435-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="22435-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="22435-125">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="22435-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="22435-126">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="22435-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="22435-127">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="22435-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="22435-128">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="22435-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="22435-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="22435-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="22435-130">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="22435-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="22435-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="22435-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="22435-132">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="22435-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="22435-133">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="22435-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="22435-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22435-134">See also</span></span>

- [<span data-ttu-id="22435-135">Público</span><span class="sxs-lookup"><span data-stu-id="22435-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="22435-136">Protegido</span><span class="sxs-lookup"><span data-stu-id="22435-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="22435-137">Friend</span><span class="sxs-lookup"><span data-stu-id="22435-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="22435-138">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="22435-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="22435-139">[Protected Friend](./protected-friend.md)[acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="22435-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="22435-140">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="22435-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="22435-141">Estruturas</span><span class="sxs-lookup"><span data-stu-id="22435-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="22435-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="22435-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
