---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="f1cd6-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1cd6-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="f1cd6-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro do assembly que contém sua declaração.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1cd6-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1cd6-104">Remarks</span></span>  
 <span data-ttu-id="f1cd6-105">Em muitos casos, você deseja a programação de elementos, como classes e estruturas para ser usado pelo conjunto inteiro, não apenas pelo componente que declara.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="f1cd6-106">No entanto, talvez não seja a ser acessado pelo código fora do assembly (por exemplo, se o aplicativo é proprietário).</span><span class="sxs-lookup"><span data-stu-id="f1cd6-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="f1cd6-107">Se você quiser limitar o acesso a um elemento dessa maneira, você pode declará-lo usando o `Friend` modificador.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="f1cd6-108">Código de outras classes, estruturas e módulos que são compilados para o mesmo assembly pode acessar todos os `Friend` elementos nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="f1cd6-109">`Friend`acesso geralmente é o nível preferido para elementos de programação do aplicativo, e `Friend` é o acesso padrão em nível de uma interface, um módulo, uma classe ou uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="f1cd6-110">Você pode usar `Friend` somente no nível de namespace ou módulo.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="f1cd6-111">Portanto, o contexto da declaração para um `Friend` elemento deve ser um arquivo de origem, um namespace, uma interface, um módulo, uma classe ou uma estrutura; ele não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="f1cd6-112">Você pode usar o `Friend` modificador em conjunto com o [protegidos](../../../visual-basic/language-reference/modifiers/protected.md) modificador na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="f1cd6-113">Essa combinação confere ambos `Friend` acesso e protegidos nos elementos declarados, para que eles são acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="f1cd6-114">Você pode especificar `Protected Friend` somente em membros de classes.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="f1cd6-115">Para obter uma comparação de `Friend` e outros modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f1cd6-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1cd6-116">Você pode especificar outro assembly é um assembly friend, que permite acessar todos os tipos e membros que são marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="f1cd6-117">Para obter mais informações, consulte [Assemblies amigáveis](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f1cd6-117">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1cd6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1cd6-118">Example</span></span>  
 <span data-ttu-id="f1cd6-119">A seguinte classe usa a `Friend` modificador para permitir que outros elementos de programação dentro do mesmo assembly para acessar determinados membros.</span><span class="sxs-lookup"><span data-stu-id="f1cd6-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="f1cd6-120">Uso</span><span class="sxs-lookup"><span data-stu-id="f1cd6-120">Usage</span></span>  
 <span data-ttu-id="f1cd6-121">Você pode usar o `Friend` modificador nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="f1cd6-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="f1cd6-122">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="f1cd6-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="f1cd6-123">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="f1cd6-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="f1cd6-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="f1cd6-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="f1cd6-125">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="f1cd6-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="f1cd6-126">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="f1cd6-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f1cd6-127">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="f1cd6-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="f1cd6-128">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="f1cd6-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="f1cd6-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="f1cd6-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f1cd6-130">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="f1cd6-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="f1cd6-131">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="f1cd6-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="f1cd6-132">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="f1cd6-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f1cd6-133">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="f1cd6-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="f1cd6-134">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="f1cd6-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1cd6-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1cd6-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="f1cd6-136">Público</span><span class="sxs-lookup"><span data-stu-id="f1cd6-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="f1cd6-137">Protegido</span><span class="sxs-lookup"><span data-stu-id="f1cd6-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="f1cd6-138">Privado</span><span class="sxs-lookup"><span data-stu-id="f1cd6-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="f1cd6-139">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1cd6-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="f1cd6-140">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f1cd6-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="f1cd6-141">Estruturas</span><span class="sxs-lookup"><span data-stu-id="f1cd6-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="f1cd6-142">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="f1cd6-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
