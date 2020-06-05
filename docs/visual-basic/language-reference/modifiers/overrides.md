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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392022"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="070db-102">Substituições (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="070db-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="070db-103">Especifica que uma propriedade ou procedimento substitui uma propriedade nomeada de forma idêntica ou procedimento herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="070db-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="070db-104">Regras</span><span class="sxs-lookup"><span data-stu-id="070db-104">Rules</span></span>

- <span data-ttu-id="070db-105">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="070db-105">**Declaration Context.**</span></span> <span data-ttu-id="070db-106">Você pode usar `Overrides` somente em uma instrução de declaração de propriedade ou de procedimento.</span><span class="sxs-lookup"><span data-stu-id="070db-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="070db-107">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="070db-107">**Combined Modifiers.**</span></span> <span data-ttu-id="070db-108">Você não pode especificar `Overrides` juntos com `Shadows` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="070db-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="070db-109">Como um elemento de substituição é implicitamente substituível, você não pode combinar `Overridable` com `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="070db-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="070db-110">**Assinaturas correspondentes.**</span><span class="sxs-lookup"><span data-stu-id="070db-110">**Matching Signatures.**</span></span> <span data-ttu-id="070db-111">A assinatura dessa declaração deve corresponder exatamente à *assinatura* da propriedade ou do procedimento que ela substitui.</span><span class="sxs-lookup"><span data-stu-id="070db-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="070db-112">Isso significa que as listas de parâmetros devem ter o mesmo número de parâmetros, na mesma ordem, com os mesmos tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="070db-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="070db-113">Além da assinatura, a declaração de substituição também deve corresponder exatamente ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="070db-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="070db-114">O nível de acesso</span><span class="sxs-lookup"><span data-stu-id="070db-114">The access level</span></span>

  - <span data-ttu-id="070db-115">O tipo de retorno, se houver</span><span class="sxs-lookup"><span data-stu-id="070db-115">The return type, if any</span></span>

- <span data-ttu-id="070db-116">**Assinaturas genéricas.**</span><span class="sxs-lookup"><span data-stu-id="070db-116">**Generic Signatures.**</span></span> <span data-ttu-id="070db-117">Para um procedimento genérico, a assinatura inclui o número de parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="070db-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="070db-118">Portanto, a declaração de substituição também deve corresponder à versão da classe base nesse aspecto.</span><span class="sxs-lookup"><span data-stu-id="070db-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="070db-119">**Correspondência adicional.**</span><span class="sxs-lookup"><span data-stu-id="070db-119">**Additional Matching.**</span></span> <span data-ttu-id="070db-120">Além de corresponder à assinatura da versão da classe base, essa declaração também deve corresponder aos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="070db-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="070db-121">Modificador de nível de acesso (como [público](public.md))</span><span class="sxs-lookup"><span data-stu-id="070db-121">Access-level modifier (such as [Public](public.md))</span></span>

  - <span data-ttu-id="070db-122">Mecanismo de passagem de cada parâmetro ([ByVal](byval.md) ou [ByRef](byref.md))</span><span class="sxs-lookup"><span data-stu-id="070db-122">Passing mechanism of each parameter ([ByVal](byval.md) or [ByRef](byref.md))</span></span>

  - <span data-ttu-id="070db-123">Listas de restrição em cada parâmetro de tipo de um procedimento genérico</span><span class="sxs-lookup"><span data-stu-id="070db-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="070db-124">**Sombreamento e substituição.**</span><span class="sxs-lookup"><span data-stu-id="070db-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="070db-125">Sombreamento e substituição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="070db-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="070db-126">Para obter mais informações, consulte [sombreamento em Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="070db-126">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="070db-127">Se você usar `Overrides` o, o compilador adicionará implicitamente `Overloads` para que suas APIs de biblioteca trabalhem com o C# mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="070db-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="070db-128">O `Overrides` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="070db-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="070db-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="070db-129">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="070db-130">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="070db-130">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="070db-131">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="070db-131">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="070db-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="070db-132">See also</span></span>

- [<span data-ttu-id="070db-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="070db-133">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="070db-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="070db-134">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="070db-135">Substituível</span><span class="sxs-lookup"><span data-stu-id="070db-135">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="070db-136">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="070db-136">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="070db-137">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="070db-137">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="070db-138">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="070db-138">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="070db-139">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="070db-139">Type List</span></span>](../statements/type-list.md)
