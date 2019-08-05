---
title: 'Como: usar o alias de namespace global – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: f44bb1f010f154973fc6982882c9b5a09528da76
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629446"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="ec4df-102">Como: usar o alias de namespace global (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ec4df-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="ec4df-103">A capacidade de acessar um membro no [namespace](../../../csharp/language-reference/keywords/namespace.md) global é útil quando o membro estiver oculto por outra entidade com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="ec4df-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="ec4df-104">Por exemplo, no código a seguir, `Console` resolve para `TestApp.Console` em vez de para o tipo `Console` no namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="ec4df-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="ec4df-105">Usar `System.Console` ainda resulta em um erro, pois o namespace `System` está oculto pela classe `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="ec4df-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="ec4df-106">No entanto, é possível contornar esse erro usando `global::System.Console`, assim:</span><span class="sxs-lookup"><span data-stu-id="ec4df-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="ec4df-107">Quando o identificador à esquerda for `global`, a pesquisa do identificador à direita começa no namespace global.</span><span class="sxs-lookup"><span data-stu-id="ec4df-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="ec4df-108">Por exemplo, a declaração a seguir faz referência a `TestApp` como um membro do espaço global.</span><span class="sxs-lookup"><span data-stu-id="ec4df-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="ec4df-109">Obviamente, criar seus próprios namespaces chamados `System` não é recomendado e é improvável que qualquer código em que isso ocorra seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="ec4df-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="ec4df-110">No entanto, em projetos grandes, há uma possibilidade bem real de que a duplicação do namespace ocorra, de uma forma ou de outra.</span><span class="sxs-lookup"><span data-stu-id="ec4df-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="ec4df-111">Nessas situações, o qualificador de namespace global é a garantia de que é possível especificar o namespace raiz.</span><span class="sxs-lookup"><span data-stu-id="ec4df-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec4df-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec4df-112">Example</span></span>  
 <span data-ttu-id="ec4df-113">Neste exemplo, o namespace `System` é usado para incluir a classe `TestClass`, portanto, `global::System.Console` deve ser usado para referenciar a classe `System.Console`, que está oculta pelo namespace `System`.</span><span class="sxs-lookup"><span data-stu-id="ec4df-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="ec4df-114">Além disso, o alias `colAlias` é usado para fazer referência ao namespace `System.Collections`; portanto, a instância de um <xref:System.Collections.Hashtable?displayProperty=nameWithType> foi criada usando este alias em vez do namespace.</span><span class="sxs-lookup"><span data-stu-id="ec4df-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]  
  
<span data-ttu-id="ec4df-115">**A 1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="ec4df-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="ec4df-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec4df-116">See also</span></span>

- [<span data-ttu-id="ec4df-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ec4df-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ec4df-118">Namespaces</span><span class="sxs-lookup"><span data-stu-id="ec4df-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="ec4df-119">:: ??</span><span class="sxs-lookup"><span data-stu-id="ec4df-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="ec4df-120">extern</span><span class="sxs-lookup"><span data-stu-id="ec4df-120">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
