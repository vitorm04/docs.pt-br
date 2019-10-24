---
title: Palavra-chave bool – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771854"
---
# <a name="bool-c-reference"></a><span data-ttu-id="243fa-102">bool (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="243fa-102">bool (C# Reference)</span></span>

<span data-ttu-id="243fa-103">A palavra-chave `bool` é um alias de <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="243fa-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="243fa-104">Ela é usada para declarar variáveis para armazenar os valores boolianos: [true](true-literal.md) e [false](false-literal.md).</span><span class="sxs-lookup"><span data-stu-id="243fa-104">It is used to declare variables to store the Boolean values: [true](true-literal.md) and [false](false-literal.md).</span></span>

> [!NOTE]
> <span data-ttu-id="243fa-105">Use o tipo `bool?`, se você precisar oferecer suporte à lógica de três valores, por exemplo, ao trabalhar com bancos de dados que dão suporte a um tipo booliano de três valores.</span><span class="sxs-lookup"><span data-stu-id="243fa-105">Use the `bool?` type, if you need to support the three-valued logic, for example, when you work with databases that support a three-valued Boolean type.</span></span> <span data-ttu-id="243fa-106">Para os operandos `bool?`, os operadores `&` e `|` predefinidos oferecem suporte à lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="243fa-106">For the `bool?` operands, the predefined `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="243fa-107">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="243fa-107">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

## <a name="literals"></a><span data-ttu-id="243fa-108">Literais</span><span class="sxs-lookup"><span data-stu-id="243fa-108">Literals</span></span>

<span data-ttu-id="243fa-109">Você pode atribuir um valor booliano a uma variável `bool`.</span><span class="sxs-lookup"><span data-stu-id="243fa-109">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="243fa-110">Você também pode atribuir uma expressão que é calculada como `bool` para um variável `bool`.</span><span class="sxs-lookup"><span data-stu-id="243fa-110">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

<span data-ttu-id="243fa-111">O valor padrão de uma variável `bool` é `false`.</span><span class="sxs-lookup"><span data-stu-id="243fa-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="243fa-112">O valor padrão de uma variável `bool?` é `null`.</span><span class="sxs-lookup"><span data-stu-id="243fa-112">The default value of a `bool?` variable is `null`.</span></span>

## <a name="conversions"></a><span data-ttu-id="243fa-113">Conversões</span><span class="sxs-lookup"><span data-stu-id="243fa-113">Conversions</span></span>

<span data-ttu-id="243fa-114">No C++, um valor do tipo `bool` pode ser convertido em um valor do tipo `int`. Em outras palavras, `false` é equivalente a zero e `true` é equivalente a valores diferentes de zero.</span><span class="sxs-lookup"><span data-stu-id="243fa-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="243fa-115">No C#, não há conversão entre o tipo `bool` e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="243fa-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="243fa-116">Por exemplo, a seguinte instrução `if` é inválida no C#:</span><span class="sxs-lookup"><span data-stu-id="243fa-116">For example, the following `if` statement is invalid in C#:</span></span>

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

<span data-ttu-id="243fa-117">Para testar uma variável do tipo `int`, você precisa compará-la explicitamente com um valor, como zero, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="243fa-117">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a><span data-ttu-id="243fa-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="243fa-118">Example</span></span>

<span data-ttu-id="243fa-119">Neste exemplo, você insere um caractere do teclado e o programa verifica se o caractere de entrada é uma letra.</span><span class="sxs-lookup"><span data-stu-id="243fa-119">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="243fa-120">Se for uma letra, ele verificará se é maiúscula ou minúscula.</span><span class="sxs-lookup"><span data-stu-id="243fa-120">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="243fa-121">Essas verificações são executadas com o <xref:System.Char.IsLetter%2A> e o <xref:System.Char.IsLower%2A>, ambos os quais retornam o tipo `bool`:</span><span class="sxs-lookup"><span data-stu-id="243fa-121">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="243fa-122">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="243fa-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="243fa-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="243fa-123">See also</span></span>

- [<span data-ttu-id="243fa-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="243fa-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="243fa-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="243fa-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="243fa-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="243fa-126">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="243fa-127">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="243fa-127">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="243fa-128">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="243fa-128">Built-In Types Table</span></span>](./built-in-types-table.md)
