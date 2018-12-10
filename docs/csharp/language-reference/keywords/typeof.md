---
title: typeof (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 039294d17d25d1d8775e7f92f46f5f57f2ac3212
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146674"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="8ee75-102">typeof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8ee75-102">typeof (C# Reference)</span></span>

<span data-ttu-id="8ee75-103">Usado para obter o objeto `System.Type` para um tipo.</span><span class="sxs-lookup"><span data-stu-id="8ee75-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="8ee75-104">Uma expressão `typeof` usa o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="8ee75-104">A `typeof` expression takes the following form:</span></span>

```csharp
System.Type type = typeof(int);
```

## <a name="remarks"></a><span data-ttu-id="8ee75-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ee75-105">Remarks</span></span>

<span data-ttu-id="8ee75-106">Para obter o tipo de tempo de execução de uma expressão, você pode usar o método do .NET Framework <xref:System.Object.GetType%2A>, assim como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ee75-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>

```csharp
int i = 0;
System.Type type = i.GetType();
```

<span data-ttu-id="8ee75-107">O operador `typeof` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="8ee75-107">The `typeof` operator cannot be overloaded.</span></span>

<span data-ttu-id="8ee75-108">O operador `typeof` também pode ser usado em tipos genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="8ee75-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="8ee75-109">Tipos com mais de um parâmetro de tipo devem ter o número apropriado de vírgulas na especificação.</span><span class="sxs-lookup"><span data-stu-id="8ee75-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="8ee75-110">O exemplo a seguir mostra como determinar se o tipo de retorno de um método é um <xref:System.Collections.Generic.IEnumerable%601> genérico.</span><span class="sxs-lookup"><span data-stu-id="8ee75-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="8ee75-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> retornará `null` se o tipo de retorno não for um tipo genérico <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="8ee75-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>

[!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]

## <a name="example"></a><span data-ttu-id="8ee75-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ee75-112">Example</span></span>

[!code-csharp[csrefKeywordsOperator#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#12)] 

## <a name="example"></a><span data-ttu-id="8ee75-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ee75-113">Example</span></span>

<span data-ttu-id="8ee75-114">Este exemplo usa o método <xref:System.Object.GetType%2A> para determinar o tipo que é usado para conter o resultado de um cálculo numérico.</span><span class="sxs-lookup"><span data-stu-id="8ee75-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="8ee75-115">Isso depende dos requisitos de armazenamento do número resultante.</span><span class="sxs-lookup"><span data-stu-id="8ee75-115">This depends on the storage requirements of the resulting number.</span></span>

[!code-csharp[csrefKeywordsOperator#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="8ee75-116">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8ee75-116">C# language specification</span></span>

<span data-ttu-id="8ee75-117">Para obter mais informações, veja [O operador typeof](~/_csharplang/spec/expressions.md#the-typeof-operator) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ee75-117">For more information, see [The typeof operator](~/_csharplang/spec/expressions.md#the-typeof-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="8ee75-118">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="8ee75-118">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ee75-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ee75-119">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- [<span data-ttu-id="8ee75-120">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8ee75-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="8ee75-121">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8ee75-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8ee75-122">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="8ee75-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="8ee75-123">is</span><span class="sxs-lookup"><span data-stu-id="8ee75-123">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="8ee75-124">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="8ee75-124">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)