---
title: Público
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351288"
---
# <a name="public-visual-basic"></a><span data-ttu-id="6a3aa-102">Público (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a3aa-102">Public (Visual Basic)</span></span>
<span data-ttu-id="6a3aa-103">Especifica que um ou mais elementos de programação declarados não têm restrições de acesso.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a3aa-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a3aa-104">Remarks</span></span>  
 <span data-ttu-id="6a3aa-105">Se você estiver publicando um componente ou conjunto de componentes, como uma biblioteca de classes, geralmente você desejará que os elementos de programação sejam acessíveis por qualquer código que interopere com seu assembly.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="6a3aa-106">Para confere tal acesso ilimitado em um elemento, você pode declará-lo com `Public`.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="6a3aa-107">Acesso público é o nível normal de um elemento de programação quando você não precisa limitar o acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="6a3aa-108">Observe que o nível de acesso de um elemento declarado em uma interface, módulo, classe ou estrutura usa como padrão a `Public` se você não declará-lo caso contrário.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6a3aa-109">Regras</span><span class="sxs-lookup"><span data-stu-id="6a3aa-109">Rules</span></span>  
  
- <span data-ttu-id="6a3aa-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="6a3aa-110">**Declaration Context.**</span></span> <span data-ttu-id="6a3aa-111">Você pode usar `Public` somente no nível do módulo, da interface ou do namespace.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="6a3aa-112">Isso significa que o contexto de declaração para um elemento de `Public` deve ser um arquivo de origem, namespace, interface, módulo, classe ou estrutura, e não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6a3aa-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6a3aa-113">Behavior</span></span>  
  
- <span data-ttu-id="6a3aa-114">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="6a3aa-114">**Access Level.**</span></span> <span data-ttu-id="6a3aa-115">Todo o código que pode acessar um módulo, uma classe ou uma estrutura pode acessar seus elementos de `Public`.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="6a3aa-116">**Acesso padrão.**</span><span class="sxs-lookup"><span data-stu-id="6a3aa-116">**Default Access.**</span></span> <span data-ttu-id="6a3aa-117">Variáveis locais dentro de um procedimento assumem o acesso público como padrão, e você não pode usar nenhum modificador de acesso neles.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="6a3aa-118">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="6a3aa-118">**Access Modifiers.**</span></span> <span data-ttu-id="6a3aa-119">As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="6a3aa-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="6a3aa-120">Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6a3aa-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="6a3aa-121">O modificador de `Public` pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="6a3aa-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6a3aa-122">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="6a3aa-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6a3aa-123">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="6a3aa-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6a3aa-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="6a3aa-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6a3aa-125">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="6a3aa-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="6a3aa-126">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="6a3aa-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6a3aa-127">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="6a3aa-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="6a3aa-128">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="6a3aa-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6a3aa-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="6a3aa-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6a3aa-130">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="6a3aa-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="6a3aa-131">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="6a3aa-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="6a3aa-132">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="6a3aa-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="6a3aa-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="6a3aa-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6a3aa-134">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="6a3aa-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="6a3aa-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="6a3aa-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6a3aa-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a3aa-136">See also</span></span>

- [<span data-ttu-id="6a3aa-137">Protegido</span><span class="sxs-lookup"><span data-stu-id="6a3aa-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="6a3aa-138">Friend</span><span class="sxs-lookup"><span data-stu-id="6a3aa-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="6a3aa-139">Privado</span><span class="sxs-lookup"><span data-stu-id="6a3aa-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="6a3aa-140">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="6a3aa-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="6a3aa-141">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="6a3aa-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="6a3aa-142">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a3aa-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="6a3aa-143">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6a3aa-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6a3aa-144">Estruturas</span><span class="sxs-lookup"><span data-stu-id="6a3aa-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6a3aa-145">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="6a3aa-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
