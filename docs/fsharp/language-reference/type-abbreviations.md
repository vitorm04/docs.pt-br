---
title: Abreviações de tipo (F#)
description: 'Saiba mais sobre as abreviações de tipo F # para dar um nome mais significativo de um tipo para facilitar a leitura do código.'
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708978"
---
# <a name="type-abbreviations"></a><span data-ttu-id="4c23b-103">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="4c23b-103">Type Abbreviations</span></span>

<span data-ttu-id="4c23b-104">Um *abreviação de tipo* é um alias ou nome alternativo para um tipo.</span><span class="sxs-lookup"><span data-stu-id="4c23b-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c23b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c23b-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="4c23b-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c23b-106">Remarks</span></span>

<span data-ttu-id="4c23b-107">Você pode usar as abreviações de tipo para fornecer um tipo de um nome mais significativo, para facilitar a leitura do código.</span><span class="sxs-lookup"><span data-stu-id="4c23b-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="4c23b-108">Você também pode usá-los para criar um nome fácil de usar para um tipo que de outra forma inconveniente para gravar. Além disso, você pode usar as abreviações de tipo para torná-lo mais fácil de alterar um tipo subjacente, sem alterar o código que usa o tipo.</span><span class="sxs-lookup"><span data-stu-id="4c23b-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="4c23b-109">A seguir é uma abreviação de tipo simples.</span><span class="sxs-lookup"><span data-stu-id="4c23b-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="4c23b-110">Acessibilidade de abreviações de tipo padrão é `public`.</span><span class="sxs-lookup"><span data-stu-id="4c23b-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="4c23b-111">Abreviações de tipo podem incluir parâmetros genéricos, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4c23b-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="4c23b-112">No código anterior, `Transform` é uma abreviação de tipo que representa uma função que aceita um único argumento de qualquer tipo e que retorna um único valor desse mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="4c23b-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="4c23b-113">Abreviações de tipo não são preservadas no código MSIL do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c23b-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="4c23b-114">Portanto, quando você usa um assembly F # de outra linguagem do .NET Framework, você deve usar o nome do tipo subjacente para uma abreviação de tipo.</span><span class="sxs-lookup"><span data-stu-id="4c23b-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="4c23b-115">Abreviações de tipo também podem ser usadas em unidades de medida.</span><span class="sxs-lookup"><span data-stu-id="4c23b-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="4c23b-116">Para obter mais informações, consulte [unidades de medida](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="4c23b-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c23b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c23b-117">See also</span></span>

- [<span data-ttu-id="4c23b-118">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4c23b-118">F# Language Reference</span></span>](index.md)
