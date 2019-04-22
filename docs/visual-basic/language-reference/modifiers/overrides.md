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
ms.openlocfilehash: 9eb19bf5e89b12a32cae28b2c087570acc10f3ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826581"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="bb2a8-102">Substituições (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb2a8-102">Overrides (Visual Basic)</span></span>
<span data-ttu-id="bb2a8-103">Especifica que uma propriedade ou procedimento substitui uma propriedade nomeada de forma idêntica ou procedimento herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb2a8-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb2a8-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bb2a8-105">Regras</span><span class="sxs-lookup"><span data-stu-id="bb2a8-105">Rules</span></span>  
  
-   <span data-ttu-id="bb2a8-106">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="bb2a8-106">**Declaration Context.**</span></span> <span data-ttu-id="bb2a8-107">Você pode usar `Overrides` somente em uma instrução de declaração de propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-107">You can use `Overrides` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="bb2a8-108">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="bb2a8-108">**Combined Modifiers.**</span></span> <span data-ttu-id="bb2a8-109">Não é possível especificar `Overrides` junto com `Shadows` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-109">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="bb2a8-110">Como um elemento de substituição é implicitamente substituível, não é possível combinar `Overridable` com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-110">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
-   <span data-ttu-id="bb2a8-111">**Correspondência de assinaturas.**</span><span class="sxs-lookup"><span data-stu-id="bb2a8-111">**Matching Signatures.**</span></span> <span data-ttu-id="bb2a8-112">A assinatura dessa declaração deve corresponder exatamente a *assinatura* da propriedade ou procedimento que ela substitui.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-112">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="bb2a8-113">Isso significa que as listas de parâmetros devem ter o mesmo número de parâmetros, na mesma ordem, com os mesmos tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-113">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>  
  
     <span data-ttu-id="bb2a8-114">Além de assinatura, a declaração de substituição deve corresponder exatamente também o seguinte:</span><span class="sxs-lookup"><span data-stu-id="bb2a8-114">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>  
  
    -   <span data-ttu-id="bb2a8-115">O nível de acesso</span><span class="sxs-lookup"><span data-stu-id="bb2a8-115">The access level</span></span>  
  
    -   <span data-ttu-id="bb2a8-116">O tipo de retorno, se houver</span><span class="sxs-lookup"><span data-stu-id="bb2a8-116">The return type, if any</span></span>  
  
-   <span data-ttu-id="bb2a8-117">**Assinaturas genéricas.**</span><span class="sxs-lookup"><span data-stu-id="bb2a8-117">**Generic Signatures.**</span></span> <span data-ttu-id="bb2a8-118">Para um procedimento genérico, a assinatura inclui o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-118">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="bb2a8-119">Portanto, a declaração de substituição deve corresponder à versão de classe base em também.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-119">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>  
  
-   <span data-ttu-id="bb2a8-120">**Correspondência adicionais.**</span><span class="sxs-lookup"><span data-stu-id="bb2a8-120">**Additional Matching.**</span></span> <span data-ttu-id="bb2a8-121">Além de correspondência a assinatura da versão da classe base, essa declaração também deve corresponder ao-lo nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="bb2a8-121">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>  
  
    -   <span data-ttu-id="bb2a8-122">Modificador de nível de acesso (como [pública](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="bb2a8-122">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>  
  
    -   <span data-ttu-id="bb2a8-123">Mecanismo de passagem de cada parâmetro ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="bb2a8-123">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>  
  
    -   <span data-ttu-id="bb2a8-124">Listas de restrições em cada parâmetro de tipo de um procedimento genérico</span><span class="sxs-lookup"><span data-stu-id="bb2a8-124">Constraint lists on each type parameter of a generic procedure</span></span>  
  
-   <span data-ttu-id="bb2a8-125">**Sombreamento e sobreposição.**</span><span class="sxs-lookup"><span data-stu-id="bb2a8-125">**Shadowing and Overriding.**</span></span> <span data-ttu-id="bb2a8-126">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-126">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="bb2a8-127">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="bb2a8-127">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="bb2a8-128">Se você usar `Overrides`, o compilador adicionará implicitamente `Overloads` para que sua biblioteca de APIs de trabalhar com C# com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="bb2a8-128">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="bb2a8-129">O `Overrides` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="bb2a8-129">The `Overrides` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bb2a8-130">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="bb2a8-130">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bb2a8-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="bb2a8-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bb2a8-132">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="bb2a8-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb2a8-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb2a8-133">See also</span></span>

- [<span data-ttu-id="bb2a8-134">MustOverride</span><span class="sxs-lookup"><span data-stu-id="bb2a8-134">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="bb2a8-135">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="bb2a8-135">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="bb2a8-136">Substituível</span><span class="sxs-lookup"><span data-stu-id="bb2a8-136">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="bb2a8-137">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="bb2a8-137">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="bb2a8-138">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb2a8-138">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="bb2a8-139">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb2a8-139">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="bb2a8-140">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="bb2a8-140">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
