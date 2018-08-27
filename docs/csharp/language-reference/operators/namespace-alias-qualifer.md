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
ms.openlocfilehash: 480ed224d1994dac926dfc78d59e227c8d1e8f36
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934989"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a87c4-102">Operador :: (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a87c4-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="a87c4-103">O qualificador alias de namespace (`::`) é usado para pesquisar identificadores.</span><span class="sxs-lookup"><span data-stu-id="a87c4-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="a87c4-104">Ele sempre está posicionado entre dois identificadores, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="a87c4-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="a87c4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a87c4-105">Remarks</span></span>  
 <span data-ttu-id="a87c4-106">O qualificador alias de namespace pode ser `global`.</span><span class="sxs-lookup"><span data-stu-id="a87c4-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="a87c4-107">Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="a87c4-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="a87c4-108">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="a87c4-108">For More Information</span></span>  
 <span data-ttu-id="a87c4-109">Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="a87c4-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="a87c4-110">Como usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="a87c4-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a87c4-111">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a87c4-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a87c4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a87c4-112">See Also</span></span>

- [<span data-ttu-id="a87c4-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a87c4-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a87c4-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a87c4-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a87c4-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="a87c4-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="a87c4-116">Palavras-chave de namespace</span><span class="sxs-lookup"><span data-stu-id="a87c4-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="a87c4-117">. ??</span><span class="sxs-lookup"><span data-stu-id="a87c4-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="a87c4-118">Alias extern</span><span class="sxs-lookup"><span data-stu-id="a87c4-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
