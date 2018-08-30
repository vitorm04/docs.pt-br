---
title: Palavra-chave operator (referência em C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929866"
---
# <a name="operator-c-reference"></a><span data-ttu-id="96100-102">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="96100-102">operator (C# Reference)</span></span>

<span data-ttu-id="96100-103">Use a palavra-chave `operator` para sobrecarregar um operador interno ou para fornecer uma conversão definida pelo usuário em uma declaração de classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="96100-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

## <a name="example"></a><span data-ttu-id="96100-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96100-104">Example</span></span>

<span data-ttu-id="96100-105">A seguir, temos uma classe bastante simplificada para números fracionários.</span><span class="sxs-lookup"><span data-stu-id="96100-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="96100-106">Ela sobrecarrega os operadores `+` e `*` para executar multiplicação e adição fracionária e também fornece um operador de conversão que converte um tipo `Fraction` em um tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="96100-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="96100-107">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="96100-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="96100-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96100-108">See also</span></span>

- [<span data-ttu-id="96100-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="96100-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="96100-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="96100-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="96100-111">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="96100-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="96100-112">implicit</span><span class="sxs-lookup"><span data-stu-id="96100-112">implicit</span></span>](implicit.md)
- [<span data-ttu-id="96100-113">explicit</span><span class="sxs-lookup"><span data-stu-id="96100-113">explicit</span></span>](explicit.md)
- [<span data-ttu-id="96100-114">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="96100-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
