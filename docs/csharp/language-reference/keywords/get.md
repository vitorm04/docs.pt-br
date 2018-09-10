---
title: get (Referência de C#)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 182f7164ad929232c185903a3dbf024a2e5d22a7
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277595"
---
# <a name="get-c-reference"></a><span data-ttu-id="13336-102">get (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="13336-102">get (C# Reference)</span></span>

<span data-ttu-id="13336-103">A palavra-chave `get` define um método do *acessador* em uma propriedade ou um indexador que retorna o valor da propriedade ou o elemento do indexador.</span><span class="sxs-lookup"><span data-stu-id="13336-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="13336-104">Para obter mais informações, consulte [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexadores](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="13336-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="13336-105">O exemplo a seguir define um acessador `get` e um acessador `set` para uma propriedade chamada `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="13336-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="13336-106">Ela usa um campo particular chamado `_seconds` para dar suporte ao valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="13336-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="13336-107">Geralmente, o acessador `get` consiste em uma única instrução que retorna um valor, como no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="13336-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="13336-108">Começando com o C# 7.0, você pode implementar o acessador `get` como um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="13336-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="13336-109">O exemplo a seguir implementa os acessadores `get` e `set` como membros aptos para expressão.</span><span class="sxs-lookup"><span data-stu-id="13336-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="13336-110">Para casos simples em que os acessadores `get` e `set` de uma propriedade não realizam nenhuma outra operação, a não ser a configuração ou a recuperação de um valor em um campo de suporte particular, você pode tirar proveito do suporte do compilador do C# para propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="13336-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="13336-111">O exemplo a seguir implementa `Hours` como uma propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="13336-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="13336-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="13336-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13336-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13336-113">See Also</span></span>

- [<span data-ttu-id="13336-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="13336-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="13336-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="13336-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="13336-116">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="13336-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="13336-117">Propriedades</span><span class="sxs-lookup"><span data-stu-id="13336-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
