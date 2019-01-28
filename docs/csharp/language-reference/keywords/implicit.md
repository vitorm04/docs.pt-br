---
title: implicit – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: d3e1cb9d6fb37617c6e2aa7070b006c594d39762
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661705"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="b0b0b-102">implicit (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b0b0b-102">implicit (C# Reference)</span></span>

<span data-ttu-id="b0b0b-103">A palavra-chave `implicit` é usada para declarar um operador de conversão implícita de tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b0b0b-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="b0b0b-104">Use-a para habilitar conversões implícitas entre um tipo definido pelo usuário e outro tipo, se houver garantia de que a conversão não causará perda de dados.</span><span class="sxs-lookup"><span data-stu-id="b0b0b-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>

## <a name="example"></a><span data-ttu-id="b0b0b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b0b0b-105">Example</span></span>

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

<span data-ttu-id="b0b0b-106">Com a eliminação de conversões desnecessárias, as conversões implícitas podem melhorar a legibilidade do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="b0b0b-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="b0b0b-107">No entanto, como as conversões implícitas não exigem que os programadores convertam explicitamente de um tipo para outro, é necessário ter cuidado para evitar resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="b0b0b-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="b0b0b-108">De modo geral, operadores de conversão implícita nunca devem gerar exceções e perder informações, para que possam ser usados com segurança sem conhecimento do programador.</span><span class="sxs-lookup"><span data-stu-id="b0b0b-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="b0b0b-109">Se um operador de conversão não puder atender a esses critérios, ele deve ser marcado como `explicit`.</span><span class="sxs-lookup"><span data-stu-id="b0b0b-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="b0b0b-110">Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="b0b0b-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0b0b-111">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b0b0b-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0b0b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0b0b-112">See also</span></span>

- [<span data-ttu-id="b0b0b-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b0b0b-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0b0b-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b0b0b-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0b0b-115">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b0b0b-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b0b0b-116">explicit</span><span class="sxs-lookup"><span data-stu-id="b0b0b-116">explicit</span></span>](explicit.md)
- [<span data-ttu-id="b0b0b-117">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b0b0b-117">operator (C# Reference)</span></span>](operator.md)
- [<span data-ttu-id="b0b0b-118">Como: implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="b0b0b-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
