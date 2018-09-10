---
title: 'Operador :: (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 077d5835b372897cbe797385271effc5d00bf6e3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525650"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d1edb-102">Operador :: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d1edb-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="d1edb-103">O qualificador alias de namespace (`::`) é usado para pesquisar identificadores.</span><span class="sxs-lookup"><span data-stu-id="d1edb-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="d1edb-104">Ele sempre está posicionado entre dois identificadores, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="d1edb-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  

<span data-ttu-id="d1edb-105">O operador `::` também pode ser usado com uma *diretiva alias de uso*:</span><span class="sxs-lookup"><span data-stu-id="d1edb-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="d1edb-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1edb-106">Remarks</span></span>  
 <span data-ttu-id="d1edb-107">O qualificador alias de namespace pode ser `global`.</span><span class="sxs-lookup"><span data-stu-id="d1edb-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="d1edb-108">Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="d1edb-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="d1edb-109">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="d1edb-109">For More Information</span></span>  
 <span data-ttu-id="d1edb-110">Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="d1edb-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="d1edb-111">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="d1edb-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d1edb-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d1edb-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1edb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1edb-113">See Also</span></span>

- [<span data-ttu-id="d1edb-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d1edb-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d1edb-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d1edb-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d1edb-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d1edb-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="d1edb-117">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="d1edb-117">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="d1edb-118">. ??</span><span class="sxs-lookup"><span data-stu-id="d1edb-118">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="d1edb-119">Alias extern</span><span class="sxs-lookup"><span data-stu-id="d1edb-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
