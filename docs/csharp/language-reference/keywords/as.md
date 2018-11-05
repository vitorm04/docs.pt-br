---
title: as (Referência de C#)
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: ce3163f7d957df96a5c0304adc0b3083d8e20104
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122599"
---
# <a name="as-c-reference"></a><span data-ttu-id="c20ed-102">as (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c20ed-102">as (C# Reference)</span></span>
<span data-ttu-id="c20ed-103">Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c20ed-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="c20ed-104">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="c20ed-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

<span data-ttu-id="c20ed-105">Como mostrado no exemplo, você precisa comparar o resultado da expressão `as` com `null` para verificar se uma conversão foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c20ed-105">As the example shows, you need to compare the result of the `as` expression with `null` to check if a conversion is successful.</span></span> <span data-ttu-id="c20ed-106">A partir do C# 7.0, você pode usar a expressão [is](is.md) para testar se uma conversão foi bem-sucedida e, condicionalmente, atribuir uma variável quando a conversão for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c20ed-106">Beginning with C# 7.0, you can use the [is](is.md) expression both to test that a conversion succeeds and conditionally assign a variable when the conversion succeeds.</span></span> <span data-ttu-id="c20ed-107">Em muitos cenários, é mais conciso do que usar o operador `as`.</span><span class="sxs-lookup"><span data-stu-id="c20ed-107">In many scenarios, it's more concise than using the `as` operator.</span></span> <span data-ttu-id="c20ed-108">Para saber mais, confira a seção [Padrão de tipo](is.md#type) do artigo [operador `is`](is.md).</span><span class="sxs-lookup"><span data-stu-id="c20ed-108">For more information, see the [Type pattern](is.md#type) section of the [`is` operator](is.md) article.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="c20ed-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c20ed-109">Remarks</span></span>  
 <span data-ttu-id="c20ed-110">O operador `as` é como uma operação de conversão.</span><span class="sxs-lookup"><span data-stu-id="c20ed-110">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="c20ed-111">No entanto, se a conversão não for possível, `as` retorna `null` em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c20ed-111">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="c20ed-112">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c20ed-112">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="c20ed-113">O código é equivalente à expressão a seguir, exceto que a variável `expression` é avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c20ed-113">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="c20ed-114">Observe que o operador `as` executa somente conversões de referência, conversões que permitem valor nulo e conversões boxing.</span><span class="sxs-lookup"><span data-stu-id="c20ed-114">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="c20ed-115">O operador `as` não pode realizar outras conversões, como conversões definidas pelo usuário que, em vez disso, devem ser realizadas usando expressões de conversão.</span><span class="sxs-lookup"><span data-stu-id="c20ed-115">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c20ed-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c20ed-116">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="c20ed-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c20ed-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c20ed-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c20ed-118">See Also</span></span>  
- [<span data-ttu-id="c20ed-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c20ed-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c20ed-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c20ed-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c20ed-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c20ed-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c20ed-122">is</span><span class="sxs-lookup"><span data-stu-id="c20ed-122">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="c20ed-123">Operador ?:</span><span class="sxs-lookup"><span data-stu-id="c20ed-123">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="c20ed-124">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="c20ed-124">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
