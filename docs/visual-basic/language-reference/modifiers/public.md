---
title: Público (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0b8c31facc3605ff5a77aecf7b11456b33fbab72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647741"
---
# <a name="public-visual-basic"></a><span data-ttu-id="0786f-102">Público (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0786f-102">Public (Visual Basic)</span></span>
<span data-ttu-id="0786f-103">Especifica que um ou mais elementos de programação declarados não têm nenhuma restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="0786f-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0786f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="0786f-104">Remarks</span></span>  
 <span data-ttu-id="0786f-105">Se você estiver publicando um componente ou um conjunto de componentes, como uma biblioteca de classes, geralmente você deseja que os elementos de programação para ser acessado por qualquer código que interopera com o assembly.</span><span class="sxs-lookup"><span data-stu-id="0786f-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="0786f-106">Para concede tal acesso ilimitado em um elemento, você pode declará-la com `Public`.</span><span class="sxs-lookup"><span data-stu-id="0786f-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="0786f-107">Acesso público é o nível normal para um elemento de programação quando você não precisa limitar o acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="0786f-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="0786f-108">Observe que o nível de acesso de um elemento declarado dentro de uma interface, módulo, classe ou estrutura padrão é `Public` se você não declarar o contrário.</span><span class="sxs-lookup"><span data-stu-id="0786f-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0786f-109">Regras</span><span class="sxs-lookup"><span data-stu-id="0786f-109">Rules</span></span>  
  
- <span data-ttu-id="0786f-110">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="0786f-110">**Declaration Context.**</span></span> <span data-ttu-id="0786f-111">Você pode usar `Public` apenas no nível de namespace ou módulo.</span><span class="sxs-lookup"><span data-stu-id="0786f-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="0786f-112">Isso significa que o contexto da declaração para um `Public` elemento deve ser um arquivo de origem, namespace, interface, módulo, classe ou estrutura e não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="0786f-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="0786f-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="0786f-113">Behavior</span></span>  
  
- <span data-ttu-id="0786f-114">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="0786f-114">**Access Level.**</span></span> <span data-ttu-id="0786f-115">Todo o código que pode acessar um módulo, classe ou estrutura pode acessar seu `Public` elementos.</span><span class="sxs-lookup"><span data-stu-id="0786f-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="0786f-116">**Acesso padrão.**</span><span class="sxs-lookup"><span data-stu-id="0786f-116">**Default Access.**</span></span> <span data-ttu-id="0786f-117">Variáveis locais dentro de um procedimento usam como padrão acesso público e você não podem usar qualquer modificador de acesso sobre eles.</span><span class="sxs-lookup"><span data-stu-id="0786f-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="0786f-118">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="0786f-118">**Access Modifiers.**</span></span> <span data-ttu-id="0786f-119">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="0786f-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="0786f-120">Para obter uma comparação os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0786f-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="0786f-121">O `Public` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="0786f-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0786f-122">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="0786f-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="0786f-123">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="0786f-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="0786f-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="0786f-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="0786f-125">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="0786f-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="0786f-126">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="0786f-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="0786f-127">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="0786f-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="0786f-128">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="0786f-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="0786f-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="0786f-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="0786f-130">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="0786f-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="0786f-131">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="0786f-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="0786f-132">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="0786f-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="0786f-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="0786f-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="0786f-134">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="0786f-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="0786f-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="0786f-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0786f-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0786f-136">See also</span></span>

- [<span data-ttu-id="0786f-137">Protegido</span><span class="sxs-lookup"><span data-stu-id="0786f-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="0786f-138">Friend</span><span class="sxs-lookup"><span data-stu-id="0786f-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="0786f-139">Privado</span><span class="sxs-lookup"><span data-stu-id="0786f-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="0786f-140">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="0786f-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="0786f-141">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="0786f-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="0786f-142">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0786f-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0786f-143">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="0786f-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0786f-144">Estruturas</span><span class="sxs-lookup"><span data-stu-id="0786f-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0786f-145">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="0786f-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
