---
title: Matrizes de tipo implícito – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705711"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="d14ef-102">Matrizes de tipo implícito (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d14ef-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="d14ef-103">É possível criar uma matriz de tipo implícito na qual o tipo da instância da matriz é inferido com base nos elementos especificados no inicializador de matriz.</span><span class="sxs-lookup"><span data-stu-id="d14ef-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="d14ef-104">As regras para qualquer variável de tipo implícito também se aplicam a matrizes de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="d14ef-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="d14ef-105">Para obter mais informações, consulte [Variáveis locais de tipo implícito](../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="d14ef-105">For more information, see [Implicitly Typed Local Variables](../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="d14ef-106">Geralmente, as matrizes de tipo implícito são usadas em expressões de consulta juntamente com objetos e tipos anônimos e inicializadores de coleção.</span><span class="sxs-lookup"><span data-stu-id="d14ef-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>

<span data-ttu-id="d14ef-107">Os exemplos a seguir mostram como criar uma matriz de tipo implícito:</span><span class="sxs-lookup"><span data-stu-id="d14ef-107">The following examples show how to create an implicitly-typed array:</span></span>

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

<span data-ttu-id="d14ef-108">No exemplo anterior, observe que, com as matrizes de tipo implícito, não são usados colchetes do lado esquerdo da instrução de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d14ef-108">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="d14ef-109">Observe também que as matrizes denteadas são inicializadas usando `new []` assim como matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="d14ef-109">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>

## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="d14ef-110">Matrizes de tipo implícito em Inicializadores de objeto</span><span class="sxs-lookup"><span data-stu-id="d14ef-110">Implicitly-typed Arrays in Object Initializers</span></span>

<span data-ttu-id="d14ef-111">Ao criar um tipo anônimo que contém uma matriz, ela deve ser de tipo implícito no inicializador de objeto do tipo.</span><span class="sxs-lookup"><span data-stu-id="d14ef-111">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="d14ef-112">No exemplo a seguir, `contacts` é uma matriz de tipo implícito de tipos anônimos, cada um contém uma matriz denominada `PhoneNumbers`.</span><span class="sxs-lookup"><span data-stu-id="d14ef-112">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="d14ef-113">Observe que a palavra-chave `var` não é usada dentro dos inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="d14ef-113">Note that the `var` keyword is not used inside the object initializers.</span></span>

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a><span data-ttu-id="d14ef-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d14ef-114">See also</span></span>

- [<span data-ttu-id="d14ef-115">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="d14ef-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d14ef-116">Variáveis locais digitadas implicitamente</span><span class="sxs-lookup"><span data-stu-id="d14ef-116">Implicitly Typed Local Variables</span></span>](../classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="d14ef-117">Matrizes</span><span class="sxs-lookup"><span data-stu-id="d14ef-117">Arrays</span></span>](./index.md)
- [<span data-ttu-id="d14ef-118">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="d14ef-118">Anonymous Types</span></span>](../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="d14ef-119">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="d14ef-119">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="d14ef-120">Var</span><span class="sxs-lookup"><span data-stu-id="d14ef-120">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="d14ef-121">LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="d14ef-121">LINQ in C#</span></span>](../../linq/index.md)
