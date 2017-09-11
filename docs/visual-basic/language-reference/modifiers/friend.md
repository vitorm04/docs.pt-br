---
title: Friend (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Friend
dev_langs:
- VB
helpviewer_keywords:
- Friend keyword
- Friend access modifier
- Friend keyword, syntax
- Protected Friend keyword combination
- Friend keyword, and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 078601228cf7d2477f0d19d224ea5b9fe4258b02
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="friend-visual-basic"></a><span data-ttu-id="45989-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45989-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="45989-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente a partir de dentro do assembly que contém sua declaração.</span><span class="sxs-lookup"><span data-stu-id="45989-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45989-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="45989-104">Remarks</span></span>  
 <span data-ttu-id="45989-105">Em muitos casos, você deseja programar elementos como classes e estruturas para ser usado pelo assembly inteiro, não apenas pelo componente que declara-los.</span><span class="sxs-lookup"><span data-stu-id="45989-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="45989-106">No entanto, você talvez não queira estejam acessíveis pelo código fora do assembly (por exemplo, se o aplicativo é proprietário).</span><span class="sxs-lookup"><span data-stu-id="45989-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="45989-107">Se você quiser limitar o acesso a um elemento dessa maneira, você pode declará-lo usando o `Friend` modificador.</span><span class="sxs-lookup"><span data-stu-id="45989-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="45989-108">Código em outras classes, estruturas e módulos são compilados no mesmo assembly pode acessar todos os `Friend` elementos nesse assembly.</span><span class="sxs-lookup"><span data-stu-id="45989-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="45989-109">`Friend`acesso geralmente é o nível de preferência para elementos de programação do aplicativo, e `Friend` é o acesso padrão em nível de uma interface, um módulo, uma classe ou uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="45989-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="45989-110">Você pode usar `Friend` somente no nível de namespace ou módulo.</span><span class="sxs-lookup"><span data-stu-id="45989-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="45989-111">Portanto, o contexto da declaração para um `Friend` elemento deve ser um arquivo de origem, um namespace, uma interface, um módulo, uma classe ou uma estrutura; não pode ser um procedimento.</span><span class="sxs-lookup"><span data-stu-id="45989-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="45989-112">Você pode usar o `Friend` modificador em conjunto com o [protegido](../../../visual-basic/language-reference/modifiers/protected.md) modificador na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="45989-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="45989-113">Essa combinação confere ambos `Friend` acesso e protegidos nos elementos declarados, para que sejam acessíveis a partir de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="45989-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="45989-114">Você pode especificar `Protected Friend` somente em membros de classes.</span><span class="sxs-lookup"><span data-stu-id="45989-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="45989-115">Para obter uma comparação de `Friend` e outros modificadores de acesso, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="45989-115">For a comparison of `Friend` and the other access modifiers, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45989-116">Você pode especificar outro assembly é um assembly de amigo, que permite acessar todos os tipos e membros que são marcados como `Friend`.</span><span class="sxs-lookup"><span data-stu-id="45989-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="45989-117">Para obter mais informações, consulte [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="45989-117">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45989-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45989-118">Example</span></span>  
 <span data-ttu-id="45989-119">A classe a seguir usa o `Friend` modificador para permitir que outros elementos de programação dentro do mesmo assembly para acessar determinados membros.</span><span class="sxs-lookup"><span data-stu-id="45989-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 <span data-ttu-id="45989-120">[!code-vb[VbVbalrAccessModifiers n º&1;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="45989-120">[!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]</span></span>  
  
## <a name="usage"></a><span data-ttu-id="45989-121">Uso</span><span class="sxs-lookup"><span data-stu-id="45989-121">Usage</span></span>  
 <span data-ttu-id="45989-122">Você pode usar o `Friend` modificador nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="45989-122">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="45989-123">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="45989-123">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="45989-124">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="45989-124">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="45989-125">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="45989-125">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="45989-126">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="45989-126">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="45989-127">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="45989-127">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="45989-128">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="45989-128">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="45989-129">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="45989-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="45989-130">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="45989-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="45989-131">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="45989-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="45989-132">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="45989-132">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="45989-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="45989-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="45989-134">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="45989-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="45989-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="45989-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="45989-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45989-136">See Also</span></span>  
 <span data-ttu-id="45989-137"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="45989-137"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
<span data-ttu-id="45989-138"> [Público](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="45989-138"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="45989-139"> [Protegido](../../../visual-basic/language-reference/modifiers/protected.md) </span><span class="sxs-lookup"><span data-stu-id="45989-139"> [Protected](../../../visual-basic/language-reference/modifiers/protected.md) </span></span>  
<span data-ttu-id="45989-140"> [Privado](../../../visual-basic/language-reference/modifiers/private.md) </span><span class="sxs-lookup"><span data-stu-id="45989-140"> [Private](../../../visual-basic/language-reference/modifiers/private.md) </span></span>  
<span data-ttu-id="45989-141"> [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="45989-141"> [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span></span>  
<span data-ttu-id="45989-142"> [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="45989-142"> [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="45989-143"> [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="45989-143"> [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="45989-144"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="45989-144"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
