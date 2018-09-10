---
title: Como inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0b103513bdcdef42c61172d1cc0ee096264a9559
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521549"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="155b2-102">Como inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="155b2-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="155b2-103">Você pode usar os inicializadores de objeto para inicializar objetos de tipo de maneira declarativa, sem invocar explicitamente um construtor para o tipo.</span><span class="sxs-lookup"><span data-stu-id="155b2-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="155b2-104">Os exemplos a seguir mostram como usar os inicializadores de objeto com objetos nomeados.</span><span class="sxs-lookup"><span data-stu-id="155b2-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="155b2-105">O compilador processa os inicializadores de objetos ao acessar, primeiro, o construtor de instância padrão e, em seguida, processar as inicializações de membro.</span><span class="sxs-lookup"><span data-stu-id="155b2-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="155b2-106">Portanto, se o construtor padrão for declarado como `private` na classe, os inicializadores de objeto que exigem acesso público falharão.</span><span class="sxs-lookup"><span data-stu-id="155b2-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="155b2-107">Se você estiver definindo um tipo anônimo, é necessário usar um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="155b2-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="155b2-108">Para obter mais informações, consulte [Como retornar subconjuntos de propriedades de elementos em uma consulta](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="155b2-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="155b2-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="155b2-109">Example</span></span>  
 <span data-ttu-id="155b2-110">O exemplo a seguir mostra como inicializar um novo tipo `StudentName`, usando inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="155b2-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="155b2-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="155b2-111">Example</span></span>  
 <span data-ttu-id="155b2-112">O exemplo a seguir mostra como inicializar uma coleção de tipos `StudentName`, usando um inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="155b2-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="155b2-113">Observe que um inicializador de coleção é uma série de inicializadores de objeto separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="155b2-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="155b2-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="155b2-114">Compiling the Code</span></span>  
 <span data-ttu-id="155b2-115">Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="155b2-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155b2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="155b2-116">See Also</span></span>

- [<span data-ttu-id="155b2-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="155b2-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="155b2-118">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="155b2-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
