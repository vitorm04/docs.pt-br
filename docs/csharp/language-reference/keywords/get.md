---
description: get – Referência de C#
title: get – Referência de C#
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139730"
---
# <a name="get-c-reference"></a><span data-ttu-id="b32d3-103">get (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b32d3-103">get (C# Reference)</span></span>

<span data-ttu-id="b32d3-104">A palavra-chave `get` define um método do *acessador* em uma propriedade ou um indexador que retorna o valor da propriedade ou o elemento do indexador.</span><span class="sxs-lookup"><span data-stu-id="b32d3-104">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="b32d3-105">Para obter mais informações, consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md), [Propriedades autoimplementadas](../../programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b32d3-105">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="b32d3-106">O exemplo a seguir define um acessador `get` e um acessador `set` para uma propriedade chamada `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="b32d3-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="b32d3-107">Ela usa um campo particular chamado `_seconds` para dar suporte ao valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="b32d3-107">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="b32d3-108">Geralmente, o acessador `get` consiste em uma única instrução que retorna um valor, como no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="b32d3-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="b32d3-109">Começando com o C# 7.0, você pode implementar o acessador `get` como um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="b32d3-109">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="b32d3-110">O exemplo a seguir implementa os acessadores `get` e `set` como membros aptos para expressão.</span><span class="sxs-lookup"><span data-stu-id="b32d3-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="b32d3-111">Para casos simples em que os acessadores `get` e `set` de uma propriedade não realizam nenhuma outra operação, a não ser a configuração ou a recuperação de um valor em um campo de suporte particular, você pode tirar proveito do suporte do compilador do C# para propriedades autoimplementadas.</span><span class="sxs-lookup"><span data-stu-id="b32d3-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="b32d3-112">O exemplo a seguir implementa `Hours` como uma propriedade autoimplementada.</span><span class="sxs-lookup"><span data-stu-id="b32d3-112">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b32d3-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b32d3-113">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b32d3-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b32d3-114">See also</span></span>

- [<span data-ttu-id="b32d3-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="b32d3-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b32d3-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b32d3-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b32d3-117">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b32d3-117">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b32d3-118">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b32d3-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
