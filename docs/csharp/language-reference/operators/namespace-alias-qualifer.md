---
title: 'Operador :: – referência do C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 0b456ed3ce9965ef389d8ce40167afa4ac33da18
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422528"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="fc136-102">Operador :: (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="fc136-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="fc136-103">O qualificador alias de namespace (`::`) é usado para pesquisar identificadores.</span><span class="sxs-lookup"><span data-stu-id="fc136-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="fc136-104">Ele sempre está posicionado entre dois identificadores, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="fc136-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="fc136-105">O operador `::` também pode ser usado com uma *diretiva alias de uso*:</span><span class="sxs-lookup"><span data-stu-id="fc136-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="fc136-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc136-106">Remarks</span></span>

<span data-ttu-id="fc136-107">O qualificador alias de namespace pode ser `global`.</span><span class="sxs-lookup"><span data-stu-id="fc136-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="fc136-108">Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="fc136-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="fc136-109">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="fc136-109">For more information</span></span>

<span data-ttu-id="fc136-110">Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="fc136-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="fc136-111">Como: usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="fc136-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="fc136-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fc136-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fc136-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc136-113">See also</span></span>

- [<span data-ttu-id="fc136-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fc136-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc136-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fc136-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc136-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="fc136-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="fc136-117">Operador .</span><span class="sxs-lookup"><span data-stu-id="fc136-117">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="fc136-118">Alias extern</span><span class="sxs-lookup"><span data-stu-id="fc136-118">extern alias</span></span>](../keywords/extern-alias.md)
