---
title: Substituições
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
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351380"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="a7242-102">Substituições (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7242-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="a7242-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span><span class="sxs-lookup"><span data-stu-id="a7242-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="a7242-104">Regras</span><span class="sxs-lookup"><span data-stu-id="a7242-104">Rules</span></span>

- <span data-ttu-id="a7242-105">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="a7242-105">**Declaration Context.**</span></span> <span data-ttu-id="a7242-106">You can use `Overrides` only in a property or procedure declaration statement.</span><span class="sxs-lookup"><span data-stu-id="a7242-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="a7242-107">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="a7242-107">**Combined Modifiers.**</span></span> <span data-ttu-id="a7242-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="a7242-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="a7242-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a7242-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="a7242-110">**Matching Signatures.**</span><span class="sxs-lookup"><span data-stu-id="a7242-110">**Matching Signatures.**</span></span> <span data-ttu-id="a7242-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span><span class="sxs-lookup"><span data-stu-id="a7242-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="a7242-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span><span class="sxs-lookup"><span data-stu-id="a7242-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="a7242-113">In addition to the signature, the overriding declaration must also exactly match the following:</span><span class="sxs-lookup"><span data-stu-id="a7242-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="a7242-114">The access level</span><span class="sxs-lookup"><span data-stu-id="a7242-114">The access level</span></span>

  - <span data-ttu-id="a7242-115">The return type, if any</span><span class="sxs-lookup"><span data-stu-id="a7242-115">The return type, if any</span></span>

- <span data-ttu-id="a7242-116">**Generic Signatures.**</span><span class="sxs-lookup"><span data-stu-id="a7242-116">**Generic Signatures.**</span></span> <span data-ttu-id="a7242-117">For a generic procedure, the signature includes the number of type parameters.</span><span class="sxs-lookup"><span data-stu-id="a7242-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="a7242-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span><span class="sxs-lookup"><span data-stu-id="a7242-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="a7242-119">**Additional Matching.**</span><span class="sxs-lookup"><span data-stu-id="a7242-119">**Additional Matching.**</span></span> <span data-ttu-id="a7242-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span><span class="sxs-lookup"><span data-stu-id="a7242-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="a7242-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="a7242-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="a7242-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="a7242-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="a7242-123">Constraint lists on each type parameter of a generic procedure</span><span class="sxs-lookup"><span data-stu-id="a7242-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="a7242-124">**Shadowing and Overriding.**</span><span class="sxs-lookup"><span data-stu-id="a7242-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="a7242-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span><span class="sxs-lookup"><span data-stu-id="a7242-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="a7242-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="a7242-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="a7242-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span><span class="sxs-lookup"><span data-stu-id="a7242-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="a7242-128">The `Overrides` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="a7242-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="a7242-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="a7242-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="a7242-130">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="a7242-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="a7242-131">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="a7242-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="a7242-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7242-132">See also</span></span>

- [<span data-ttu-id="a7242-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a7242-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="a7242-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="a7242-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="a7242-135">Substituível</span><span class="sxs-lookup"><span data-stu-id="a7242-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="a7242-136">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a7242-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="a7242-137">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7242-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="a7242-138">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7242-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a7242-139">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="a7242-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
