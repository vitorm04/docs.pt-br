---
title: Abreviações de tipo
description: Saiba mais F# sobre abreviações de tipo para dar a um tipo um nome mais significativo a fim de facilitar a leitura do código.
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630206"
---
# <a name="type-abbreviations"></a><span data-ttu-id="17073-103">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="17073-103">Type Abbreviations</span></span>

<span data-ttu-id="17073-104">Uma *abreviação de tipo* é um alias ou nome alternativo para um tipo.</span><span class="sxs-lookup"><span data-stu-id="17073-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="17073-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17073-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="17073-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="17073-106">Remarks</span></span>

<span data-ttu-id="17073-107">Você pode usar abreviações de tipo para dar a um tipo um nome mais significativo, a fim de facilitar a leitura do código.</span><span class="sxs-lookup"><span data-stu-id="17073-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="17073-108">Você também pode usá-los para criar um nome fácil de usar para um tipo que, de outra forma, é difícil de gravar. Além disso, você pode usar abreviações de tipo para facilitar a alteração de um tipo subjacente sem alterar todo o código que usa o tipo.</span><span class="sxs-lookup"><span data-stu-id="17073-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="17073-109">A seguir está uma abreviação de tipo simples.</span><span class="sxs-lookup"><span data-stu-id="17073-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="17073-110">A acessibilidade do tipo abreviações usa como `public`padrão.</span><span class="sxs-lookup"><span data-stu-id="17073-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="17073-111">As abreviações de tipo podem incluir parâmetros genéricos, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="17073-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="17073-112">No código anterior, `Transform` é uma abreviação de tipo que representa uma função que usa um único argumento de qualquer tipo e que retorna um único valor desse mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="17073-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="17073-113">As abreviações de tipo não são preservadas no código .NET Framework MSIL.</span><span class="sxs-lookup"><span data-stu-id="17073-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="17073-114">Portanto, ao usar um F# assembly de outro idioma de .NET Framework, você deve usar o nome de tipo subjacente para uma abreviação de tipo.</span><span class="sxs-lookup"><span data-stu-id="17073-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="17073-115">As abreviações de tipo também podem ser usadas em unidades de medida.</span><span class="sxs-lookup"><span data-stu-id="17073-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="17073-116">Para obter mais informações, consulte [unidades de medida](units-of-measure.md).</span><span class="sxs-lookup"><span data-stu-id="17073-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17073-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17073-117">See also</span></span>

- [<span data-ttu-id="17073-118">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="17073-118">F# Language Reference</span></span>](index.md)
