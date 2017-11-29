---
title: "Abreviações de tipo (F#)"
description: "Saiba mais sobre F # abreviações de tipo para dar um nome mais significativo de um tipo para facilitar a leitura do código."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a><span data-ttu-id="594d5-104">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="594d5-104">Type Abbreviations</span></span>

<span data-ttu-id="594d5-105">Um *abreviação de tipo* é um alias ou nome alternativo para um tipo.</span><span class="sxs-lookup"><span data-stu-id="594d5-105">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="594d5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="594d5-106">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="594d5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="594d5-107">Remarks</span></span>
<span data-ttu-id="594d5-108">Você pode usar as abreviações de tipo para dar um nome mais significativo, de um tipo para facilitar a leitura do código.</span><span class="sxs-lookup"><span data-stu-id="594d5-108">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="594d5-109">Você também pode usá-los para criar um nome fácil de usar um tipo que está inconveniente para gravar. Além disso, você pode usar abreviações de tipo para tornar mais fácil alterar um tipo subjacente sem alterar o código que usa o tipo.</span><span class="sxs-lookup"><span data-stu-id="594d5-109">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="594d5-110">A seguir é uma abreviação de tipo simples.</span><span class="sxs-lookup"><span data-stu-id="594d5-110">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="594d5-111">Abreviações de tipo podem incluir parâmetros genéricos, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="594d5-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="594d5-112">No código anterior, `Transform` é uma abreviação de tipo que representa uma função que aceita um único argumento de qualquer tipo e que retorna um único valor do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="594d5-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="594d5-113">Abreviações de tipo não são preservadas no código MSIL do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="594d5-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="594d5-114">Portanto, quando você usa um assembly F # de outra linguagem do .NET Framework, você deve usar o nome do tipo base para uma abreviação de tipo.</span><span class="sxs-lookup"><span data-stu-id="594d5-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="594d5-115">Abreviações de tipo também podem ser usadas em unidades de medida.</span><span class="sxs-lookup"><span data-stu-id="594d5-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="594d5-116">Para obter mais informações, consulte [unidades de medida](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="594d5-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="594d5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="594d5-117">See Also</span></span>
[<span data-ttu-id="594d5-118">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="594d5-118">F# Language Reference</span></span>](index.md)

