---
title: as – Referência de C#
ms.custom: seodec18
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 84e599340877ce52dc6242ea259c69672915c546
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422020"
---
# <a name="as-c-reference"></a><span data-ttu-id="27986-102">as (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="27986-102">as (C# Reference)</span></span>
<span data-ttu-id="27986-103">Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="27986-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="27986-104">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="27986-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="27986-105">Como mostrado no exemplo, você precisa comparar o resultado da expressão `as` com `null` para verificar se uma conversão foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="27986-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="27986-106">A partir do C# 7.0, você pode usar a expressão [is](is.md) para testar se uma conversão foi bem-sucedida e, condicionalmente, atribuir uma variável quando a conversão for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="27986-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="27986-107">Em muitos cenários, é mais conciso do que usar o operador `as`.</span><span class="sxs-lookup"><span data-stu-id="27986-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="27986-108">Para saber mais, confira a seção [Padrão de tipo](is.md#type) do artigo [operador `is`](is.md).</span><span class="sxs-lookup"><span data-stu-id="27986-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="27986-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="27986-109">Remarks</span></span>  
 <span data-ttu-id="27986-110">O operador `as` é como uma operação de conversão.</span><span class="sxs-lookup"><span data-stu-id="27986-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="27986-111">No entanto, se a conversão não for possível, `as` retorna `null` em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="27986-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="27986-112">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="27986-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="27986-113">O código é equivalente à expressão a seguir, exceto que a variável `expression` é avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="27986-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="27986-114">Observe que o operador `as` executa somente conversões de referência, conversões que permitem valor nulo e conversões boxing.</span><span class="sxs-lookup"><span data-stu-id="27986-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="27986-115">O operador `as` não pode realizar outras conversões, como conversões definidas pelo usuário que, em vez disso, devem ser realizadas usando expressões de conversão.</span><span class="sxs-lookup"><span data-stu-id="27986-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27986-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27986-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="27986-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="27986-117">C# Language Specification</span></span>  

<span data-ttu-id="27986-118">Para obter mais informações, veja [O operador as](~/_csharplang/spec/expressions.md#the-as-operator) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="27986-118">For more information, see [The as operator](~/_csharplang/spec/expressions.md#the-as-operator) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="27986-119">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="27986-119">The language specification is the definitive source for C# syntax and usage.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="27986-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27986-120">See also</span></span>

- [<span data-ttu-id="27986-121">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="27986-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="27986-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="27986-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="27986-123">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="27986-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="27986-124">is</span><span class="sxs-lookup"><span data-stu-id="27986-124">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="27986-125">?: ??</span><span class="sxs-lookup"><span data-stu-id="27986-125">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)
