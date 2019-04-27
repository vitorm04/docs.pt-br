---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 18681935d0380f9be3970fdb5d17ffb089152f59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802535"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="77e32-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77e32-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="77e32-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro do assembly que contém sua declaração.</span><span class="sxs-lookup"><span data-stu-id="77e32-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77e32-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="77e32-104">Remarks</span></span>  
 <span data-ttu-id="77e32-105">Em muitos casos, convém elementos de programação como classes e estruturas para ser usado por todo o assembly, não apenas pelo componente que declara-los.</span><span class="sxs-lookup"><span data-stu-id="77e32-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="77e32-106">No entanto, você talvez não queira eles sejam acessíveis pelo código fora do assembly (por exemplo, se o aplicativo é proprietário).</span><span class="sxs-lookup"><span data-stu-id="77e32-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="77e32-107">Se você quiser limitar o acesso a um elemento dessa forma, você pode declará-lo usando o `Friend` modificador.</span><span class="sxs-lookup"><span data-stu-id="77e32-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="77e32-108">Código em outras classes, estruturas e módulos que são compilados no mesmo assembly pode acessar todos os `Friend` elementos nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="77e32-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="77e32-109">`Friend` acesso geralmente é o nível de preferência para elementos de programação do aplicativo, e `Friend` é o acesso padrão em nível de uma interface, um módulo, uma classe ou uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="77e32-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="77e32-110">Você pode usar `Friend` somente no nível de namespace ou módulo.</span><span class="sxs-lookup"><span data-stu-id="77e32-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="77e32-111">Portanto, o contexto da declaração para um `Friend` elemento deve ser um arquivo de origem, um namespace, uma interface, um módulo, uma classe ou uma estrutura; ele não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="77e32-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="77e32-112">Você também pode usar o [Protected Friend](protected-friend.md) modificador de acesso, o que torna um membro da classe acessível de dentro dessa classe, de classes derivadas e do mesmo assembly em que a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="77e32-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="77e32-113">Para restringir o acesso a um membro dentro de sua classe e de classes derivadas no mesmo assembly, você deve usar o [Private Protected](private-protected.md) modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="77e32-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="77e32-114">Para obter uma comparação `Friend` e outros modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="77e32-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77e32-115">Você pode especificar que o outro assembly é um assembly amigável, que permite acessar todos os tipos e membros que são marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="77e32-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="77e32-116">Para obter mais informações, consulte [Assemblies amigáveis](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="77e32-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77e32-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77e32-117">Example</span></span>  
 <span data-ttu-id="77e32-118">A classe a seguir usa o `Friend` modificador para permitir que outros elementos de programação dentro do mesmo assembly para acessar determinados membros.</span><span class="sxs-lookup"><span data-stu-id="77e32-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="77e32-119">Uso</span><span class="sxs-lookup"><span data-stu-id="77e32-119">Usage</span></span>  
 <span data-ttu-id="77e32-120">Você pode usar o `Friend` modificador nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="77e32-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="77e32-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="77e32-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="77e32-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="77e32-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="77e32-123">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="77e32-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="77e32-124">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="77e32-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="77e32-125">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="77e32-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="77e32-126">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="77e32-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="77e32-127">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="77e32-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="77e32-128">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="77e32-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="77e32-129">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="77e32-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="77e32-130">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="77e32-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="77e32-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="77e32-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="77e32-132">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="77e32-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="77e32-133">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="77e32-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="77e32-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77e32-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="77e32-135">Público</span><span class="sxs-lookup"><span data-stu-id="77e32-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="77e32-136">Protegido</span><span class="sxs-lookup"><span data-stu-id="77e32-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="77e32-137">Privado</span><span class="sxs-lookup"><span data-stu-id="77e32-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="77e32-138">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="77e32-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="77e32-139">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="77e32-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="77e32-140">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77e32-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="77e32-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="77e32-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="77e32-142">Estruturas</span><span class="sxs-lookup"><span data-stu-id="77e32-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="77e32-143">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="77e32-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
