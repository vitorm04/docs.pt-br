---
title: Palavra-chave contextual global – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: b9273feb38b14dce61facc0f59b0890c431b9a7a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240784"
---
# <a name="global-c-reference"></a><span data-ttu-id="7794d-102">global (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7794d-102">global (C# Reference)</span></span>

<span data-ttu-id="7794d-103">Quando a palavra-chave contextual `global` vem antes do [operador ::](../operators/namespace-alias-qualifer.md), refere-se ao namespace global, que é o namespace padrão para qualquer programa em C#, que não foi nomeado de outra maneira.</span><span class="sxs-lookup"><span data-stu-id="7794d-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="7794d-104">Confira mais informações em [Como: usar o alias de namespace global](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="7794d-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="7794d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7794d-105">Example</span></span>

<span data-ttu-id="7794d-106">O exemplo a seguir mostra como usar a palavra-chave contextual `global` para especificar que a classe `TestApp` é definida no namespace global:</span><span class="sxs-lookup"><span data-stu-id="7794d-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="7794d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7794d-107">See also</span></span>

- [<span data-ttu-id="7794d-108">Namespaces</span><span class="sxs-lookup"><span data-stu-id="7794d-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)