---
title: set (Referência de C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a><span data-ttu-id="137a9-102">set (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="137a9-102">set (C# Reference)</span></span>
<span data-ttu-id="137a9-103">A palavra-chave `set` define um método *acessador* em uma propriedade ou indexador que atribui um valor ao elemento da propriedade ou do elemento.</span><span class="sxs-lookup"><span data-stu-id="137a9-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="137a9-104">Para obter mais informações e exemplos, consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexadores](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="137a9-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="137a9-105">O exemplo a seguir define um acessador `get` e um acessador `set` para uma propriedade chamada `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="137a9-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="137a9-106">Ela usa um campo particular chamado `_seconds` para dar suporte ao valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="137a9-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="137a9-107">Geralmente, o acessador `set` consiste em uma única instrução que retorna um valor, como no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="137a9-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="137a9-108">Começando com o C# 7, você pode implementar o acessador `set` como um membro com corpo de expressão.</span><span class="sxs-lookup"><span data-stu-id="137a9-108">Starting with C# 7, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="137a9-109">O exemplo a seguir implementa os acessadores `get` e `set` como membros com corpo de expressão.</span><span class="sxs-lookup"><span data-stu-id="137a9-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="137a9-110">Para casos simples em que os acessadores `get` e `set` de uma propriedade não realizam nenhuma outra operação, a não ser a configuração ou a recuperação de um valor em um campo de suporte particular, você pode tirar proveito do suporte do compilador do C# para propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="137a9-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="137a9-111">O exemplo a seguir implementa `Hours` como uma propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="137a9-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="137a9-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="137a9-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="137a9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="137a9-113">See Also</span></span>  
 [<span data-ttu-id="137a9-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="137a9-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="137a9-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="137a9-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="137a9-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="137a9-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="137a9-117">Propriedades</span><span class="sxs-lookup"><span data-stu-id="137a9-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
