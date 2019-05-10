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
ms.openlocfilehash: 7fff91d993743574d13030aa3d5cc1e462e76838
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751035"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="a148a-102">Substituições (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a148a-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="a148a-103">Especifica que uma propriedade ou procedimento substitui uma propriedade nomeada de forma idêntica ou procedimento herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="a148a-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="a148a-104">Regras</span><span class="sxs-lookup"><span data-stu-id="a148a-104">Rules</span></span>

- <span data-ttu-id="a148a-105">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="a148a-105">**Declaration Context.**</span></span> <span data-ttu-id="a148a-106">Você pode usar `Overrides` somente em uma instrução de declaração de propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="a148a-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="a148a-107">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="a148a-107">**Combined Modifiers.**</span></span> <span data-ttu-id="a148a-108">Não é possível especificar `Overrides` junto com `Shadows` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="a148a-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="a148a-109">Como um elemento de substituição é implicitamente substituível, não é possível combinar `Overridable` com `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a148a-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="a148a-110">**Correspondência de assinaturas.**</span><span class="sxs-lookup"><span data-stu-id="a148a-110">**Matching Signatures.**</span></span> <span data-ttu-id="a148a-111">A assinatura dessa declaração deve corresponder exatamente a *assinatura* da propriedade ou procedimento que ela substitui.</span><span class="sxs-lookup"><span data-stu-id="a148a-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="a148a-112">Isso significa que as listas de parâmetros devem ter o mesmo número de parâmetros, na mesma ordem, com os mesmos tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="a148a-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="a148a-113">Além de assinatura, a declaração de substituição deve corresponder exatamente também o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a148a-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="a148a-114">O nível de acesso</span><span class="sxs-lookup"><span data-stu-id="a148a-114">The access level</span></span>

  - <span data-ttu-id="a148a-115">O tipo de retorno, se houver</span><span class="sxs-lookup"><span data-stu-id="a148a-115">The return type, if any</span></span>

- <span data-ttu-id="a148a-116">**Assinaturas genéricas.**</span><span class="sxs-lookup"><span data-stu-id="a148a-116">**Generic Signatures.**</span></span> <span data-ttu-id="a148a-117">Para um procedimento genérico, a assinatura inclui o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="a148a-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="a148a-118">Portanto, a declaração de substituição deve corresponder à versão de classe base em também.</span><span class="sxs-lookup"><span data-stu-id="a148a-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="a148a-119">**Correspondência adicionais.**</span><span class="sxs-lookup"><span data-stu-id="a148a-119">**Additional Matching.**</span></span> <span data-ttu-id="a148a-120">Além de correspondência a assinatura da versão da classe base, essa declaração também deve corresponder ao-lo nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="a148a-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="a148a-121">Modificador de nível de acesso (como [pública](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="a148a-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="a148a-122">Mecanismo de passagem de cada parâmetro ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="a148a-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="a148a-123">Listas de restrições em cada parâmetro de tipo de um procedimento genérico</span><span class="sxs-lookup"><span data-stu-id="a148a-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="a148a-124">**Sombreamento e sobreposição.**</span><span class="sxs-lookup"><span data-stu-id="a148a-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="a148a-125">Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="a148a-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="a148a-126">Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="a148a-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="a148a-127">Se você usar `Overrides`, o compilador adicionará implicitamente `Overloads` para que sua biblioteca de APIs de trabalhar com C# com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="a148a-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="a148a-128">O `Overrides` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="a148a-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="a148a-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="a148a-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="a148a-130">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="a148a-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="a148a-131">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="a148a-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="a148a-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a148a-132">See also</span></span>

- [<span data-ttu-id="a148a-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a148a-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="a148a-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a148a-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="a148a-135">Substituível</span><span class="sxs-lookup"><span data-stu-id="a148a-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="a148a-136">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a148a-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="a148a-137">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a148a-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="a148a-138">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a148a-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a148a-139">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="a148a-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
