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
ms.openlocfilehash: 3e30267c8aa11ce97b3b3064ff0954378dab57af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959808"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="a2d2f-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2d2f-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="a2d2f-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro do assembly que contém sua declaração.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d2f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2d2f-104">Remarks</span></span>  
 <span data-ttu-id="a2d2f-105">Em muitos casos, você deseja que elementos de programação, como classes e estruturas, sejam usados pelo assembly inteiro, não apenas pelo componente que os declara.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="a2d2f-106">No entanto, talvez você não queira que eles fiquem acessíveis pelo código fora do assembly (por exemplo, se o aplicativo for proprietário).</span><span class="sxs-lookup"><span data-stu-id="a2d2f-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="a2d2f-107">Se você quiser limitar o acesso a um elemento dessa forma, você pode declará-lo usando o `Friend` modificador.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="a2d2f-108">O código em outras classes, estruturas e módulos que são compilados para o mesmo assembly pode acessar todos `Friend` os elementos nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="a2d2f-109">`Friend`o acesso é geralmente o nível preferencial para os elementos de programação de um `Friend` aplicativo e é o nível de acesso padrão de uma interface, um módulo, uma classe ou uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="a2d2f-110">Você pode usar `Friend` somente no nível do módulo, da interface ou do namespace.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="a2d2f-111">Portanto, o contexto de declaração de `Friend` um elemento deve ser um arquivo de origem, um namespace, uma interface, um módulo, uma classe ou uma estrutura; ele não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="a2d2f-112">Você também pode usar o modificador de acesso [Friend protegido](protected-friend.md) , que torna um membro de classe acessível de dentro dessa classe, de classes derivadas e do mesmo assembly no qual a classe é definida.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="a2d2f-113">Para restringir o acesso a um membro de dentro de sua classe e de classes derivadas no mesmo assembly, use o modificador de acesso [protegido privado](private-protected.md) .</span><span class="sxs-lookup"><span data-stu-id="a2d2f-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="a2d2f-114">Para obter uma comparação `Friend` entre o e os outros modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a2d2f-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2d2f-115">Você pode especificar que outro assembly é um assembly Friend, que permite que ele acesse todos os tipos e membros marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="a2d2f-116">Para obter mais informações, consulte [Assemblies amigáveis](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a2d2f-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2d2f-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2d2f-117">Example</span></span>  
 <span data-ttu-id="a2d2f-118">A classe a seguir usa `Friend` o modificador para permitir que outros elementos de programação dentro do mesmo assembly acessem determinados membros.</span><span class="sxs-lookup"><span data-stu-id="a2d2f-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="a2d2f-119">Uso</span><span class="sxs-lookup"><span data-stu-id="a2d2f-119">Usage</span></span>  
 <span data-ttu-id="a2d2f-120">Você pode usar o `Friend` modificador nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="a2d2f-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="a2d2f-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="a2d2f-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="a2d2f-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="a2d2f-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="a2d2f-123">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="a2d2f-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="a2d2f-124">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="a2d2f-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="a2d2f-125">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="a2d2f-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="a2d2f-126">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="a2d2f-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="a2d2f-127">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="a2d2f-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="a2d2f-128">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="a2d2f-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="a2d2f-129">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="a2d2f-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="a2d2f-130">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="a2d2f-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="a2d2f-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="a2d2f-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="a2d2f-132">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="a2d2f-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="a2d2f-133">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="a2d2f-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a2d2f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2d2f-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="a2d2f-135">Público</span><span class="sxs-lookup"><span data-stu-id="a2d2f-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="a2d2f-136">Protegido</span><span class="sxs-lookup"><span data-stu-id="a2d2f-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="a2d2f-137">Privado</span><span class="sxs-lookup"><span data-stu-id="a2d2f-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="a2d2f-138">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="a2d2f-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="a2d2f-139">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="a2d2f-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="a2d2f-140">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2d2f-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a2d2f-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="a2d2f-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="a2d2f-142">Estruturas</span><span class="sxs-lookup"><span data-stu-id="a2d2f-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a2d2f-143">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="a2d2f-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
