---
title: Como inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8e9130983aabe991660ff4cca90b33609f86c158
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="ca326-102">Como inicializar objetos usando um inicializador de objeto (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ca326-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="ca326-103">Você pode usar os inicializadores de objeto para inicializar objetos de tipo de maneira declarativa, sem invocar explicitamente um construtor para o tipo.</span><span class="sxs-lookup"><span data-stu-id="ca326-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="ca326-104">Os exemplos a seguir mostram como usar os inicializadores de objeto com objetos nomeados.</span><span class="sxs-lookup"><span data-stu-id="ca326-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="ca326-105">O compilador processa os inicializadores de objetos ao acessar, primeiro, o construtor de instância padrão e, em seguida, processar as inicializações de membro.</span><span class="sxs-lookup"><span data-stu-id="ca326-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="ca326-106">Portanto, se o construtor padrão for declarado como `private` na classe, os inicializadores de objeto que exigem acesso público falharão.</span><span class="sxs-lookup"><span data-stu-id="ca326-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="ca326-107">Se você estiver definindo um tipo anônimo, é necessário usar um inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="ca326-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="ca326-108">Para obter mais informações, consulte [Como retornar subconjuntos de propriedades de elementos em uma consulta](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="ca326-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca326-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca326-109">Example</span></span>  
 <span data-ttu-id="ca326-110">O exemplo a seguir mostra como inicializar um novo tipo `StudentName`, usando inicializadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="ca326-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ca326-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca326-111">Example</span></span>  
 <span data-ttu-id="ca326-112">O exemplo a seguir mostra como inicializar uma coleção de tipos `StudentName`, usando um inicializador de coleção.</span><span class="sxs-lookup"><span data-stu-id="ca326-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="ca326-113">Observe que um inicializador de coleção é uma série de inicializadores de objeto separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="ca326-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca326-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ca326-114">Compiling the Code</span></span>  
 <span data-ttu-id="ca326-115">Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ca326-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca326-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca326-116">See Also</span></span>  
 [<span data-ttu-id="ca326-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ca326-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ca326-118">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="ca326-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
