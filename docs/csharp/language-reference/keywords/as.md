---
title: "as (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7a55c696ac295eee8d5d35ed56038f3c4a90b215
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="as-c-reference"></a><span data-ttu-id="68dfe-102">as (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="68dfe-102">as (C# Reference)</span></span>
<span data-ttu-id="68dfe-103">Você pode usar o operador `as` para realizar determinados tipos de conversões entre tipos de referência compatíveis ou [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="68dfe-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="68dfe-104">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="68dfe-104">The following code shows an example.</span></span>  
  
 <span data-ttu-id="68dfe-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="68dfe-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68dfe-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="68dfe-106">Remarks</span></span>  
 <span data-ttu-id="68dfe-107">O operador `as` é como uma operação de conversão.</span><span class="sxs-lookup"><span data-stu-id="68dfe-107">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="68dfe-108">No entanto, se a conversão não for possível, `as` retorna `null` em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="68dfe-108">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="68dfe-109">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="68dfe-109">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="68dfe-110">O código é equivalente à expressão a seguir, exceto que a variável `expression` é avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="68dfe-110">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="68dfe-111">Observe que o operador `as` executa somente conversões de referência, conversões que permitem valor nulo e conversões boxing.</span><span class="sxs-lookup"><span data-stu-id="68dfe-111">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="68dfe-112">O operador `as` não pode realizar outras conversões, como conversões definidas pelo usuário que, em vez disso, devem ser realizadas usando expressões de conversão.</span><span class="sxs-lookup"><span data-stu-id="68dfe-112">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68dfe-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68dfe-113">Example</span></span>  
 <span data-ttu-id="68dfe-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="68dfe-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="68dfe-115">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="68dfe-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68dfe-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68dfe-116">See Also</span></span>  
 <span data-ttu-id="68dfe-117">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="68dfe-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="68dfe-118">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="68dfe-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="68dfe-119">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="68dfe-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="68dfe-120">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="68dfe-120">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="68dfe-121">[Operador ?:](../../../csharp/language-reference/operators/conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="68dfe-121">[?: Operator](../../../csharp/language-reference/operators/conditional-operator.md) </span></span>  
 [<span data-ttu-id="68dfe-122">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="68dfe-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

