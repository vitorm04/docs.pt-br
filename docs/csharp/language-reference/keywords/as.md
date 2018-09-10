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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44098851"
---
# <a name="as-c-reference"></a><span data-ttu-id="c68ff-102">as (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c68ff-102">as (C# Reference)</span></span>
<span data-ttu-id="c68ff-103">Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="c68ff-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="c68ff-104">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="c68ff-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="c68ff-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c68ff-105">Remarks</span></span>  
 <span data-ttu-id="c68ff-106">O operador `as` é como uma operação de conversão.</span><span class="sxs-lookup"><span data-stu-id="c68ff-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="c68ff-107">No entanto, se a conversão não for possível, `as` retorna `null` em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c68ff-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="c68ff-108">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c68ff-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="c68ff-109">O código é equivalente à expressão a seguir, exceto que a variável `expression` é avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c68ff-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="c68ff-110">Observe que o operador `as` executa somente conversões de referência, conversões que permitem valor nulo e conversões boxing.</span><span class="sxs-lookup"><span data-stu-id="c68ff-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="c68ff-111">O operador `as` não pode realizar outras conversões, como conversões definidas pelo usuário que, em vez disso, devem ser realizadas usando expressões de conversão.</span><span class="sxs-lookup"><span data-stu-id="c68ff-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c68ff-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c68ff-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="c68ff-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c68ff-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c68ff-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c68ff-114">See Also</span></span>  
- [<span data-ttu-id="c68ff-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c68ff-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c68ff-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c68ff-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c68ff-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="c68ff-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c68ff-118">is</span><span class="sxs-lookup"><span data-stu-id="c68ff-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="c68ff-119">Operador ?:</span><span class="sxs-lookup"><span data-stu-id="c68ff-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="c68ff-120">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="c68ff-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
