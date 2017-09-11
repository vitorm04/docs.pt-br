---
title: Sombras (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shadows
- shadows
dev_langs:
- VB
helpviewer_keywords:
- shadowing
- duplicate names
- scope, shadowing
- Shadows keyword
- names, shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 40546c5e427c7b95181d096cf535c1ea934f4394
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="shadows-visual-basic"></a><span data-ttu-id="1254b-102">Sombras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1254b-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="1254b-103">Especifica que um elemento de programação declarado redeclara e oculta um elemento de nome idêntico, ou conjunto de elementos sobrecarregados, na classe base.</span><span class="sxs-lookup"><span data-stu-id="1254b-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1254b-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="1254b-104">Remarks</span></span>  
 <span data-ttu-id="1254b-105">O objetivo principal do sombreamento (também conhecido como *ocultar pelo nome*) é preservar a definição de seus membros de classe.</span><span class="sxs-lookup"><span data-stu-id="1254b-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="1254b-106">A classe base pode passar por uma mudança que cria um elemento com o mesmo nome que um que já definido.</span><span class="sxs-lookup"><span data-stu-id="1254b-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="1254b-107">Se isso acontecer, o `Shadows` modificador obriga referências através da sua classe a serem resolvidas ao membro que você definiu, em vez de para o novo elemento de classe base.</span><span class="sxs-lookup"><span data-stu-id="1254b-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="1254b-108">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="1254b-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="1254b-109">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="1254b-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1254b-110">Regras</span><span class="sxs-lookup"><span data-stu-id="1254b-110">Rules</span></span>  
  
-   <span data-ttu-id="1254b-111">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="1254b-111">**Declaration Context.**</span></span> <span data-ttu-id="1254b-112">Você pode usar `Shadows` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="1254b-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="1254b-113">Isso significa que o contexto da declaração para um `Shadows` elemento deve ser uma classe e não pode ser um arquivo fonte, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="1254b-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="1254b-114">Você pode declarar apenas um elemento de sombreamento em uma única declaração.</span><span class="sxs-lookup"><span data-stu-id="1254b-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="1254b-115">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="1254b-115">**Combined Modifiers.**</span></span> <span data-ttu-id="1254b-116">Não é possível especificar `Shadows` junto com `Overloads`, `Overrides`, ou `Static` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="1254b-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="1254b-117">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="1254b-117">**Element Types.**</span></span> <span data-ttu-id="1254b-118">Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="1254b-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="1254b-119">Se você sombrear uma propriedade ou procedimento com outra propriedade ou procedimento, os parâmetros e o tipo de retorno não precisam corresponder as da propriedade da classe base ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="1254b-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="1254b-120">**Acessando.**</span><span class="sxs-lookup"><span data-stu-id="1254b-120">**Accessing.**</span></span> <span data-ttu-id="1254b-121">O elemento sombreado na classe base normalmente está indisponível de dentro da classe derivada que o sombreia.</span><span class="sxs-lookup"><span data-stu-id="1254b-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="1254b-122">No entanto, as seguintes considerações se aplicam.</span><span class="sxs-lookup"><span data-stu-id="1254b-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="1254b-123">Se o elemento sombreado não está acessível do código referindo-se a ele, a referência é resolvida para o elemento sombreado.</span><span class="sxs-lookup"><span data-stu-id="1254b-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="1254b-124">Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento da classe base em vez disso.</span><span class="sxs-lookup"><span data-stu-id="1254b-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="1254b-125">Se você sombrear um elemento, você ainda pode acessar o elemento sombreado através de um objeto declarado com o tipo da classe base.</span><span class="sxs-lookup"><span data-stu-id="1254b-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="1254b-126">Você também pode acessá-lo por meio de `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="1254b-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="1254b-127">O `Shadows` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="1254b-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1254b-128">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="1254b-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1254b-129">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="1254b-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="1254b-130">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="1254b-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1254b-131">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="1254b-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="1254b-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="1254b-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1254b-133">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="1254b-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="1254b-134">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="1254b-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="1254b-135">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="1254b-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1254b-136">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="1254b-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="1254b-137">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="1254b-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1254b-138">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="1254b-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="1254b-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="1254b-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1254b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1254b-140">See Also</span></span>  
 <span data-ttu-id="1254b-141">[Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-141">[Shared](../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="1254b-142"> [Estático](../../../visual-basic/language-reference/modifiers/static.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-142"> [Static](../../../visual-basic/language-reference/modifiers/static.md) </span></span>  
<span data-ttu-id="1254b-143"> [Privado](../../../visual-basic/language-reference/modifiers/private.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-143"> [Private](../../../visual-basic/language-reference/modifiers/private.md) </span></span>  
<span data-ttu-id="1254b-144"> [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-144"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span></span>  
<span data-ttu-id="1254b-145"> [Noções básicas sobre herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-145"> [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md) </span></span>  
<span data-ttu-id="1254b-146"> [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-146"> [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) </span></span>  
<span data-ttu-id="1254b-147"> [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-147"> [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) </span></span>  
<span data-ttu-id="1254b-148"> [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-148"> [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="1254b-149"> [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-149"> [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) </span></span>  
<span data-ttu-id="1254b-150"> [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md) </span><span class="sxs-lookup"><span data-stu-id="1254b-150"> [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) </span></span>  
<span data-ttu-id="1254b-151"> [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="1254b-151"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
