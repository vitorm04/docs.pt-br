---
title: "Operador :: (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c2163-102">Operador :: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c2163-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="c2163-103">O qualificador alias de namespace (`::`) é usado para pesquisar identificadores.</span><span class="sxs-lookup"><span data-stu-id="c2163-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="c2163-104">Ele sempre está posicionado entre dois identificadores, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="c2163-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="c2163-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2163-105">Remarks</span></span>  
 <span data-ttu-id="c2163-106">O qualificador alias de namespace pode ser `global`.</span><span class="sxs-lookup"><span data-stu-id="c2163-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="c2163-107">Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="c2163-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="c2163-108">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="c2163-108">For More Information</span></span>  
 <span data-ttu-id="c2163-109">Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="c2163-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="c2163-110">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="c2163-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2163-111">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c2163-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2163-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2163-112">See Also</span></span>  
 [<span data-ttu-id="c2163-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="c2163-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c2163-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c2163-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c2163-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="c2163-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="c2163-116">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="c2163-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="c2163-117">. ??</span><span class="sxs-lookup"><span data-stu-id="c2163-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="c2163-118">Alias extern</span><span class="sxs-lookup"><span data-stu-id="c2163-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
