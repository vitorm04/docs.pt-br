---
title: Palavra-chave operator (referência em C#)
description: Saiba como sobrecarregar um operador interno de C#
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: 1e11d7767b61becc39b1158fae9cb2abe997e4bd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47209366"
---
# <a name="operator-c-reference"></a><span data-ttu-id="e223f-103">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e223f-103">operator (C# Reference)</span></span>

<span data-ttu-id="e223f-104">Use a palavra-chave `operator` para sobrecarregar um operador interno ou para fornecer uma conversão definida pelo usuário em uma declaração de classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="e223f-104">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

<span data-ttu-id="e223f-105">Para sobrecarregar um operador em uma classe ou struct personalizada, você pode criar uma declaração do operador no tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="e223f-105">To overload an operator on a custom class or struct, you create an operator declaration in the corresponding type.</span></span> <span data-ttu-id="e223f-106">A declaração do operador que sobrecarrega um operador interno de C# deve satisfazer as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="e223f-106">The operator declaration that overloads a built-in C# operator must satisfy the following rules:</span></span>

- <span data-ttu-id="e223f-107">Ela inclui os modificadores `public` e `static`.</span><span class="sxs-lookup"><span data-stu-id="e223f-107">It includes both a `public` and a `static` modifier.</span></span>
- <span data-ttu-id="e223f-108">Ela inclui `operator X` em que `X` é o nome ou símbolo do operador que está sendo sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="e223f-108">It includes `operator X` where `X` is the name or symbol of the operator being overloaded.</span></span>
- <span data-ttu-id="e223f-109">Operadores unários têm um parâmetro e operadores binários têm dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e223f-109">Unary operators have one parameter, and binary operators have two parameters.</span></span> <span data-ttu-id="e223f-110">Em cada caso, pelo menos um parâmetro deve ser do mesmo tipo que a classe ou struct que declara o operador.</span><span class="sxs-lookup"><span data-stu-id="e223f-110">In each case, at least one parameter must be the same type as the class or struct that declares the operator.</span></span>

<span data-ttu-id="e223f-111">Para obter informações sobre como definir operadores de conversão, consulte os artigos das palavras-chave [explícitas](explicit.md) e [implícitas](implicit.md).</span><span class="sxs-lookup"><span data-stu-id="e223f-111">For information about how to define conversion operators, see the [explicit](explicit.md) and [implicit](implicit.md) keyword articles.</span></span>

<span data-ttu-id="e223f-112">Para uma visão geral de operadores em C# que podem ser sobrecarregados, consulte o artigo [Operadores sobrecarregáveis](../../programming-guide/statements-expressions-operators/overloadable-operators.md).</span><span class="sxs-lookup"><span data-stu-id="e223f-112">For an overview of the C# operators that can be overloaded, see the [Overloadable operators](../../programming-guide/statements-expressions-operators/overloadable-operators.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="e223f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e223f-113">Example</span></span>

<span data-ttu-id="e223f-114">O exemplo a seguir define um tipo `Fraction` que representa números fracionários.</span><span class="sxs-lookup"><span data-stu-id="e223f-114">The following example defines a `Fraction` type that represents fractional numbers.</span></span> <span data-ttu-id="e223f-115">Ela sobrecarrega os operadores `+` e `*` para executar multiplicação e adição fracionária e também fornece um operador de conversão que converte um tipo `Fraction` em um tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="e223f-115">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="e223f-116">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e223f-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e223f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e223f-117">See also</span></span>

- [<span data-ttu-id="e223f-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e223f-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e223f-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e223f-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e223f-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e223f-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e223f-121">implicit</span><span class="sxs-lookup"><span data-stu-id="e223f-121">implicit</span></span>](implicit.md)
- [<span data-ttu-id="e223f-122">explicit</span><span class="sxs-lookup"><span data-stu-id="e223f-122">explicit</span></span>](explicit.md)
- [<span data-ttu-id="e223f-123">Operadores sobrecarregáveis</span><span class="sxs-lookup"><span data-stu-id="e223f-123">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="e223f-124">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="e223f-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
