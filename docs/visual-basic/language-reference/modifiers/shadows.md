---
title: Sombras (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb767c372cc05d61d569227af8eef0dc3c67489b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="e27a8-102">Sombras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e27a8-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="e27a8-103">Especifica que um elemento de programação declarado redeclara e oculta um elemento de nome idêntico, ou conjunto de elementos sobrecarregados, em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="e27a8-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e27a8-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e27a8-104">Remarks</span></span>  
 <span data-ttu-id="e27a8-105">O objetivo principal do sombreamento (também conhecido como *ocultar pelo nome*) é preservar a definição de seus membros de classe.</span><span class="sxs-lookup"><span data-stu-id="e27a8-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="e27a8-106">A classe base pode passar por uma mudança que cria um elemento com o mesmo nome que uma que já definido.</span><span class="sxs-lookup"><span data-stu-id="e27a8-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="e27a8-107">Se isso acontecer, o `Shadows` modificador obriga referências através da sua classe a ser resolvido para o membro que você definiu, em vez de para o novo elemento de classe base.</span><span class="sxs-lookup"><span data-stu-id="e27a8-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="e27a8-108">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="e27a8-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e27a8-109">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="e27a8-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e27a8-110">Regras</span><span class="sxs-lookup"><span data-stu-id="e27a8-110">Rules</span></span>  
  
-   <span data-ttu-id="e27a8-111">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="e27a8-111">**Declaration Context.**</span></span> <span data-ttu-id="e27a8-112">Você pode usar `Shadows` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="e27a8-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="e27a8-113">Isso significa que o contexto da declaração para um `Shadows` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="e27a8-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="e27a8-114">Você pode declarar apenas um elemento de sombreamento em uma única declaração.</span><span class="sxs-lookup"><span data-stu-id="e27a8-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="e27a8-115">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="e27a8-115">**Combined Modifiers.**</span></span> <span data-ttu-id="e27a8-116">Não é possível especificar `Shadows` junto com `Overloads`, `Overrides`, ou `Static` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="e27a8-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="e27a8-117">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="e27a8-117">**Element Types.**</span></span> <span data-ttu-id="e27a8-118">Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="e27a8-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="e27a8-119">Se você sombrear uma propriedade ou procedimento com outra propriedade ou procedimento, os parâmetros e o tipo de retorno não precisam coincide com a propriedade de classe base ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="e27a8-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="e27a8-120">**Acessando.**</span><span class="sxs-lookup"><span data-stu-id="e27a8-120">**Accessing.**</span></span> <span data-ttu-id="e27a8-121">O elemento sombreado na classe base normalmente está indisponível de dentro da classe derivada que o sombreia.</span><span class="sxs-lookup"><span data-stu-id="e27a8-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="e27a8-122">No entanto, as seguintes considerações se aplicam.</span><span class="sxs-lookup"><span data-stu-id="e27a8-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="e27a8-123">Se o elemento sombreador não está acessível do código que faz referência a ele, a referência será resolvida para o elemento sombreado.</span><span class="sxs-lookup"><span data-stu-id="e27a8-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="e27a8-124">Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento de classe base em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e27a8-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="e27a8-125">Se você sombrear um elemento, você ainda pode acessar o elemento sombreado por meio de um objeto declarado com o tipo da classe base.</span><span class="sxs-lookup"><span data-stu-id="e27a8-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="e27a8-126">Você também pode acessá-lo por meio de `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="e27a8-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="e27a8-127">O `Shadows` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="e27a8-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e27a8-128">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="e27a8-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="e27a8-129">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="e27a8-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="e27a8-130">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="e27a8-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="e27a8-131">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="e27a8-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="e27a8-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="e27a8-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="e27a8-133">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="e27a8-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="e27a8-134">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="e27a8-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="e27a8-135">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="e27a8-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e27a8-136">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="e27a8-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="e27a8-137">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="e27a8-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e27a8-138">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="e27a8-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="e27a8-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="e27a8-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e27a8-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e27a8-140">See Also</span></span>  
 [<span data-ttu-id="e27a8-141">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="e27a8-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="e27a8-142">Estático</span><span class="sxs-lookup"><span data-stu-id="e27a8-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="e27a8-143">Privado</span><span class="sxs-lookup"><span data-stu-id="e27a8-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="e27a8-144">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="e27a8-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="e27a8-145">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="e27a8-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="e27a8-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="e27a8-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="e27a8-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e27a8-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="e27a8-148">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="e27a8-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="e27a8-149">Substituível</span><span class="sxs-lookup"><span data-stu-id="e27a8-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="e27a8-150">Substituições</span><span class="sxs-lookup"><span data-stu-id="e27a8-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="e27a8-151">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e27a8-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
