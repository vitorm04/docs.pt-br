---
title: 'Como: inicializar objetos usando um inicializador de objeto – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 2ac4242eb1bd24fd54cc1eca97acb96f39cc050b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607024"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="9c517-102">Como: inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9c517-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>

<span data-ttu-id="9c517-103">Você pode usar os inicializadores de objeto para inicializar objetos de tipo de maneira declarativa, sem invocar explicitamente um construtor para o tipo.</span><span class="sxs-lookup"><span data-stu-id="9c517-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="9c517-104">Os exemplos a seguir mostram como usar os inicializadores de objeto com objetos nomeados.</span><span class="sxs-lookup"><span data-stu-id="9c517-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="9c517-105">O compilador processa os inicializadores de objetos ao acessar, primeiro, o construtor de instância padrão e, em seguida, processar as inicializações de membro.</span><span class="sxs-lookup"><span data-stu-id="9c517-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="9c517-106">Portanto, se o construtor padrão for declarado como `private` na classe, os inicializadores de objeto que exigem acesso público falharão.</span><span class="sxs-lookup"><span data-stu-id="9c517-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="9c517-107">Se você estiver definindo um tipo anônimo, é necessário usar um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="9c517-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="9c517-108">Para obter mais informações, confira [Como: retornar subconjuntos de propriedades de elementos em uma consulta](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="9c517-108">For more information, see [How to: Return Subsets of Element Properties in a Query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c517-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c517-109">Example</span></span>  

<span data-ttu-id="9c517-110">O exemplo a seguir mostra como inicializar um novo tipo `StudentName`, usando inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="9c517-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="9c517-111">Este exemplo define as propriedades de `StudentName` tipo:</span><span class="sxs-lookup"><span data-stu-id="9c517-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="9c517-112">Os inicializadores de objeto podem ser usados para definir indexadores em um objeto.</span><span class="sxs-lookup"><span data-stu-id="9c517-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="9c517-113">O exemplo a seguir define uma classe `BaseballTeam` que usa um indexador para obter e definir jogadores em posições diferentes.</span><span class="sxs-lookup"><span data-stu-id="9c517-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="9c517-114">O inicializador pode atribuir jogadores com base na abreviação da posição ou no número usado para cada scorecard de beisebol de posição:</span><span class="sxs-lookup"><span data-stu-id="9c517-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="9c517-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c517-115">See also</span></span>

- [<span data-ttu-id="9c517-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9c517-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9c517-117">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="9c517-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
