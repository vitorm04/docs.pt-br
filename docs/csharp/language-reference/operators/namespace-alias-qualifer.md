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
ms.openlocfilehash: c494e8dbb18f44ce5520b21800a21d3feb03da59
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025066"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="47695-102">Operador :: (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="47695-102">:: operator (C# reference)</span></span>

<span data-ttu-id="47695-103">O qualificador alias de namespace (`::`) é usado para pesquisar identificadores.</span><span class="sxs-lookup"><span data-stu-id="47695-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="47695-104">Ele sempre está posicionado entre dois identificadores, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="47695-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="47695-105">O operador `::` também pode ser usado com uma *diretiva alias de uso*:</span><span class="sxs-lookup"><span data-stu-id="47695-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="47695-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="47695-106">Remarks</span></span>

<span data-ttu-id="47695-107">O qualificador alias de namespace pode ser `global`.</span><span class="sxs-lookup"><span data-stu-id="47695-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="47695-108">Isso invoca uma pesquisa no namespace global, em vez de um namespace com alias.</span><span class="sxs-lookup"><span data-stu-id="47695-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="47695-109">Para obter mais informações</span><span class="sxs-lookup"><span data-stu-id="47695-109">For more information</span></span>

<span data-ttu-id="47695-110">Para obter um exemplo de como usar o operador `::`, consulte a seção a seguir:</span><span class="sxs-lookup"><span data-stu-id="47695-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="47695-111">Como: usar o alias de namespace global</span><span class="sxs-lookup"><span data-stu-id="47695-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="47695-112">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="47695-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="47695-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47695-113">See also</span></span>

- [<span data-ttu-id="47695-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="47695-114">C# reference</span></span>](../index.md)
- [<span data-ttu-id="47695-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="47695-115">C# operators</span></span>](index.md)
- [<span data-ttu-id="47695-116">Operador .</span><span class="sxs-lookup"><span data-stu-id="47695-116">. operator</span></span>](member-access-operators.md#member-access-operator-)
- [<span data-ttu-id="47695-117">Alias extern</span><span class="sxs-lookup"><span data-stu-id="47695-117">extern alias</span></span>](../keywords/extern-alias.md)
