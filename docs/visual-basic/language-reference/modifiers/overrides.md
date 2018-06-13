---
title: Substituições (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 81118b9e97f320bffdbb58e5e1a2859052c4cee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602511"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="61678-102">Substituições (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61678-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="61678-103">Especifica que uma propriedade ou procedimento substitui uma propriedade nomeada de forma idêntica ou procedimento herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="61678-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61678-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="61678-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="61678-105">Regras</span><span class="sxs-lookup"><span data-stu-id="61678-105">Rules</span></span>  
  
-   <span data-ttu-id="61678-106">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="61678-106">**Declaration Context.**</span></span> <span data-ttu-id="61678-107">Você pode usar `Overrides` somente na declaração de uma propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="61678-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="61678-108">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="61678-108">**Combined Modifiers.**</span></span> <span data-ttu-id="61678-109">Não é possível especificar `Overrides` junto com `Shadows` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="61678-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="61678-110">Como um elemento de substituição é implicitamente substituível, você não pode combinar `Overridable` com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="61678-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="61678-111">**Correspondência de assinaturas.**</span><span class="sxs-lookup"><span data-stu-id="61678-111">**Matching Signatures.**</span></span> <span data-ttu-id="61678-112">A assinatura dessa declaração deve corresponder exatamente a *assinatura* da propriedade ou procedimento que ela substitui.</span><span class="sxs-lookup"><span data-stu-id="61678-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="61678-113">Isso significa que as listas de parâmetros devem ter o mesmo número de parâmetros, na mesma ordem, com os mesmos tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="61678-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="61678-114">Além da assinatura, a declaração de substituição deve corresponder exatamente também o seguinte:</span><span class="sxs-lookup"><span data-stu-id="61678-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="61678-115">O nível de acesso</span><span class="sxs-lookup"><span data-stu-id="61678-115">The access level</span></span>  
  
    -   <span data-ttu-id="61678-116">O tipo de retorno, se houver</span><span class="sxs-lookup"><span data-stu-id="61678-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="61678-117">**Assinaturas genéricas.**</span><span class="sxs-lookup"><span data-stu-id="61678-117">**Generic Signatures.**</span></span> <span data-ttu-id="61678-118">Para um procedimento genérico, a assinatura inclui o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="61678-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="61678-119">Portanto, a declaração de substituição deve corresponder à versão de classe base em também.</span><span class="sxs-lookup"><span data-stu-id="61678-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="61678-120">**Correspondência adicionais.**</span><span class="sxs-lookup"><span data-stu-id="61678-120">**Additional Matching.**</span></span> <span data-ttu-id="61678-121">Além de correspondência a assinatura da versão da classe base, essa declaração deve também coincidir nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="61678-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="61678-122">Modificador de nível de acesso (como [pública](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="61678-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="61678-123">Mecanismo de passagem de cada parâmetro ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="61678-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="61678-124">Listas de restrições em cada parâmetro de tipo de um procedimento genérico</span><span class="sxs-lookup"><span data-stu-id="61678-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="61678-125">**Sombreamento e sobreposição.**</span><span class="sxs-lookup"><span data-stu-id="61678-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="61678-126">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="61678-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="61678-127">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="61678-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="61678-128">Se você usar `Overrides`, o compilador adiciona implicitamente `Overloads` para que sua biblioteca de APIs trabalhar mais facilmente com c#.</span><span class="sxs-lookup"><span data-stu-id="61678-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="61678-129">O `Overrides` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="61678-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="61678-130">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="61678-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="61678-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="61678-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="61678-132">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="61678-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="61678-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61678-133">See Also</span></span>  
 [<span data-ttu-id="61678-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="61678-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="61678-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="61678-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="61678-136">Substituível</span><span class="sxs-lookup"><span data-stu-id="61678-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="61678-137">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="61678-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="61678-138">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61678-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="61678-139">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61678-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="61678-140">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="61678-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
