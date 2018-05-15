---
title: Abreviações de tipo (F#)
description: 'Saiba mais sobre F # abreviações de tipo para dar um nome mais significativo de um tipo para facilitar a leitura do código.'
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="type-abbreviations"></a><span data-ttu-id="e5c2f-103">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="e5c2f-103">Type Abbreviations</span></span>

<span data-ttu-id="e5c2f-104">Um *abreviação de tipo* é um alias ou nome alternativo para um tipo.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5c2f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5c2f-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="e5c2f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5c2f-106">Remarks</span></span>
<span data-ttu-id="e5c2f-107">Você pode usar as abreviações de tipo para dar um nome mais significativo, de um tipo para facilitar a leitura do código.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="e5c2f-108">Você também pode usá-los para criar um nome fácil de usar um tipo que está inconveniente para gravar. Além disso, você pode usar abreviações de tipo para tornar mais fácil alterar um tipo subjacente sem alterar o código que usa o tipo.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="e5c2f-109">A seguir é uma abreviação de tipo simples.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="e5c2f-110">Acessibilidade de abreviações de tipo padrão é `public`.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="e5c2f-111">Abreviações de tipo podem incluir parâmetros genéricos, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="e5c2f-112">No código anterior, `Transform` é uma abreviação de tipo que representa uma função que aceita um único argumento de qualquer tipo e que retorna um único valor do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="e5c2f-113">Abreviações de tipo não são preservadas no código MSIL do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="e5c2f-114">Portanto, quando você usa um assembly F # de outra linguagem do .NET Framework, você deve usar o nome do tipo base para uma abreviação de tipo.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="e5c2f-115">Abreviações de tipo também podem ser usadas em unidades de medida.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="e5c2f-116">Para obter mais informações, consulte [unidades de medida](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="e5c2f-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e5c2f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5c2f-117">See Also</span></span>
[<span data-ttu-id="e5c2f-118">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="e5c2f-118">F# Language Reference</span></span>](index.md)

