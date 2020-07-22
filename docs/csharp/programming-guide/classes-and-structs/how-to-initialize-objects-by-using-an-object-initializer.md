---
title: Como inicializar objetos usando um inicializador de objeto-guia de programação C#
description: Saiba como usar inicializadores de objeto para inicializar objetos de tipo em C# sem invocar um construtor. Use um inicializador de objeto para definir um tipo anônimo.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0781b168b0ae8b8383affe19d2721da67f662045
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865028"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="8cdf6-104">Como inicializar objetos usando um inicializador de objeto (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="8cdf6-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="8cdf6-105">Você pode usar os inicializadores de objeto para inicializar objetos de tipo de maneira declarativa, sem invocar explicitamente um construtor para o tipo.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="8cdf6-106">Os exemplos a seguir mostram como usar os inicializadores de objeto com objetos nomeados.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="8cdf6-107">O compilador processa os inicializadores de objetos ao acessar, primeiro, o construtor de instância padrão e, em seguida, processar as inicializações de membro.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-107">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="8cdf6-108">Portanto, se o construtor sem parâmetros for declarado como `private` na classe, os inicializadores de objeto que exigem acesso público falharão.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="8cdf6-109">Se você estiver definindo um tipo anônimo, é necessário usar um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="8cdf6-110">Para obter mais informações, consulte [como retornar subconjuntos de propriedades de elemento em uma consulta](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="8cdf6-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cdf6-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8cdf6-111">Example</span></span>  

<span data-ttu-id="8cdf6-112">O exemplo a seguir mostra como inicializar um novo tipo `StudentName`, usando inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="8cdf6-113">Este exemplo define as propriedades de `StudentName` tipo:</span><span class="sxs-lookup"><span data-stu-id="8cdf6-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="8cdf6-114">Os inicializadores de objeto podem ser usados para definir indexadores em um objeto.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="8cdf6-115">O exemplo a seguir define uma classe `BaseballTeam` que usa um indexador para obter e definir jogadores em posições diferentes.</span><span class="sxs-lookup"><span data-stu-id="8cdf6-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="8cdf6-116">O inicializador pode atribuir jogadores com base na abreviação da posição ou no número usado para cada scorecard de beisebol de posição:</span><span class="sxs-lookup"><span data-stu-id="8cdf6-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="8cdf6-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="8cdf6-117">See also</span></span>

- [<span data-ttu-id="8cdf6-118">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8cdf6-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8cdf6-119">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="8cdf6-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
