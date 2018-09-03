---
title: Palavra-chave contextual global (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 837245e31a9a795aa2f13cfc6c33fefb6402801d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43401068"
---
# <a name="global-c-reference"></a><span data-ttu-id="500dd-102">global (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="500dd-102">global (C# Reference)</span></span>

<span data-ttu-id="500dd-103">Quando a palavra-chave contextual `global` vem antes do [operador ::](../operators/namespace-alias-qualifer.md), refere-se ao namespace global, que é o namespace padrão para qualquer programa em C#, que não foi nomeado de outra maneira.</span><span class="sxs-lookup"><span data-stu-id="500dd-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="500dd-104">Para obter mais informações, consulte [Como usar o alias de namespace global](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="500dd-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="500dd-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="500dd-105">Example</span></span>

<span data-ttu-id="500dd-106">O exemplo a seguir mostra como usar a palavra-chave contextual `global` para especificar que a classe `TestApp` é definida no namespace global:</span><span class="sxs-lookup"><span data-stu-id="500dd-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="500dd-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="500dd-107">See also</span></span>

- [<span data-ttu-id="500dd-108">Namespaces</span><span class="sxs-lookup"><span data-stu-id="500dd-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)