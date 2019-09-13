---
title: Protegido (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929464"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="ed420-102">Protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed420-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="ed420-103">Um modificador de acesso de membro que especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de sua própria classe ou de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="ed420-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed420-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed420-104">Remarks</span></span>  
 <span data-ttu-id="ed420-105">Às vezes, um elemento de programação declarado em uma classe contém dados confidenciais ou código restrito e você deseja limitar o acesso ao elemento.</span><span class="sxs-lookup"><span data-stu-id="ed420-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="ed420-106">No entanto, se a classe for herdável e você esperar uma hierarquia de classes derivadas, talvez seja necessário que essas classes derivadas acessem os dados ou o código.</span><span class="sxs-lookup"><span data-stu-id="ed420-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="ed420-107">Nesse caso, você deseja que o elemento seja acessível tanto da classe base quanto de todas as classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="ed420-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="ed420-108">Para limitar o acesso a um elemento dessa maneira, você pode declará-lo `Protected`com.</span><span class="sxs-lookup"><span data-stu-id="ed420-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="ed420-109">O `Protected` modificador de acesso pode ser combinado com dois outros modificadores:</span><span class="sxs-lookup"><span data-stu-id="ed420-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="ed420-110">O modificador [Friend protegido](protected-friend.md) torna um membro de classe acessível de dentro dessa classe, de classes derivadas e do mesmo assembly no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="ed420-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="ed420-111">O modificador [particular protegido](private-protected.md) torna um membro de classe acessível por tipos derivados, mas somente dentro de seu assembly de contenção.</span><span class="sxs-lookup"><span data-stu-id="ed420-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="ed420-112">Regras</span><span class="sxs-lookup"><span data-stu-id="ed420-112">Rules</span></span>  
  
- <span data-ttu-id="ed420-113">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="ed420-113">**Declaration Context.**</span></span> <span data-ttu-id="ed420-114">Você pode usar `Protected` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="ed420-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="ed420-115">Isso significa que o contexto de Declaração `Protected` para um elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="ed420-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="ed420-116">Comportamento</span><span class="sxs-lookup"><span data-stu-id="ed420-116">Behavior</span></span>  
  
- <span data-ttu-id="ed420-117">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="ed420-117">**Access Level.**</span></span> <span data-ttu-id="ed420-118">Todo o código em uma classe pode acessar seus elementos.</span><span class="sxs-lookup"><span data-stu-id="ed420-118">All code in a class can access its elements.</span></span> <span data-ttu-id="ed420-119">O código em qualquer classe derivada de uma classe base pode acessar todos os `Protected` elementos da classe base.</span><span class="sxs-lookup"><span data-stu-id="ed420-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="ed420-120">Isso é verdadeiro para todas as gerações de derivação.</span><span class="sxs-lookup"><span data-stu-id="ed420-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="ed420-121">Isso significa que uma classe pode acessar `Protected` elementos da classe base da classe base e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ed420-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="ed420-122">O acesso protegido não é um superconjunto ou subconjunto de acesso Friend.</span><span class="sxs-lookup"><span data-stu-id="ed420-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="ed420-123">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="ed420-123">**Access Modifiers.**</span></span> <span data-ttu-id="ed420-124">As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="ed420-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="ed420-125">Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ed420-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="ed420-126">O `Protected` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="ed420-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ed420-127">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="ed420-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ed420-128">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="ed420-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="ed420-129">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="ed420-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ed420-130">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="ed420-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="ed420-131">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="ed420-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="ed420-132">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="ed420-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="ed420-133">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="ed420-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="ed420-134">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="ed420-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ed420-135">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="ed420-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="ed420-136">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="ed420-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ed420-137">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="ed420-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="ed420-138">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="ed420-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed420-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed420-139">See also</span></span>

- [<span data-ttu-id="ed420-140">Público</span><span class="sxs-lookup"><span data-stu-id="ed420-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="ed420-141">Friend</span><span class="sxs-lookup"><span data-stu-id="ed420-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="ed420-142">Privado</span><span class="sxs-lookup"><span data-stu-id="ed420-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="ed420-143">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="ed420-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="ed420-144">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="ed420-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="ed420-145">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed420-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ed420-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ed420-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ed420-147">Estruturas</span><span class="sxs-lookup"><span data-stu-id="ed420-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ed420-148">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="ed420-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
