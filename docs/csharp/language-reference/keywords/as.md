---
title: as (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45648377"
---
# <a name="as-c-reference"></a><span data-ttu-id="eee28-102">as (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="eee28-102">as (C# Reference)</span></span>
<span data-ttu-id="eee28-103">Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="eee28-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="eee28-104">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="eee28-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="eee28-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="eee28-105">Remarks</span></span>  
 <span data-ttu-id="eee28-106">O operador `as` é como uma operação de conversão.</span><span class="sxs-lookup"><span data-stu-id="eee28-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="eee28-107">No entanto, se a conversão não for possível, `as` retorna `null` em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="eee28-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="eee28-108">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="eee28-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="eee28-109">O código é equivalente à expressão a seguir, exceto que a variável `expression` é avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="eee28-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="eee28-110">Observe que o operador `as` executa somente conversões de referência, conversões que permitem valor nulo e conversões boxing.</span><span class="sxs-lookup"><span data-stu-id="eee28-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="eee28-111">O operador `as` não pode realizar outras conversões, como conversões definidas pelo usuário que, em vez disso, devem ser realizadas usando expressões de conversão.</span><span class="sxs-lookup"><span data-stu-id="eee28-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eee28-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eee28-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="eee28-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="eee28-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eee28-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eee28-114">See Also</span></span>  
- [<span data-ttu-id="eee28-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="eee28-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="eee28-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="eee28-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="eee28-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="eee28-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="eee28-118">is</span><span class="sxs-lookup"><span data-stu-id="eee28-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="eee28-119">Operador ?:</span><span class="sxs-lookup"><span data-stu-id="eee28-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="eee28-120">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="eee28-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
