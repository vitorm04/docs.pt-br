---
title: Exemplo de classe COM – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 4ae3a9b09d67896336e3230caca67e3b40c6a676
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635995"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="4de81-102">Exemplo de classe COM (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4de81-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="4de81-103">A seguir está um exemplo de uma classe que você poderia expor como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="4de81-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="4de81-104">Depois que esse código é colocado em um arquivo .cs e adicionado ao seu projeto, defina a propriedade **Registrar para interoperabilidade COM** como **True**.</span><span class="sxs-lookup"><span data-stu-id="4de81-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="4de81-105">Para obter mais informações, confira [Como: registrar um componente para interoperabilidade COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4de81-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="4de81-106">A exposição de objetos do Visual C# para COM requer a declaração de uma interface de classe, de uma interface de eventos se necessário e da própria classe.</span><span class="sxs-lookup"><span data-stu-id="4de81-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="4de81-107">Os membros de classe devem seguir estas regras para ficarem visíveis ao COM:</span><span class="sxs-lookup"><span data-stu-id="4de81-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="4de81-108">A classe deve ser pública.</span><span class="sxs-lookup"><span data-stu-id="4de81-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="4de81-109">As propriedades, os métodos e os eventos devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="4de81-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="4de81-110">As propriedades e os métodos devem ser declarados na interface de classe.</span><span class="sxs-lookup"><span data-stu-id="4de81-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="4de81-111">Os eventos devem ser declarados na interface de eventos.</span><span class="sxs-lookup"><span data-stu-id="4de81-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="4de81-112">Os outros membros públicos na classe que não forem declarados nessas interfaces não estarão visíveis para o COM, mas eles estarão visíveis para outros objetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4de81-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="4de81-113">Para expor propriedades e métodos ao COM, você deve declará-los na interface de classe e marcá-los com um atributo `DispId` e implementá-los na classe.</span><span class="sxs-lookup"><span data-stu-id="4de81-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="4de81-114">A ordem na qual os membros são declarados na interface é a ordem usada para a vtable do COM.</span><span class="sxs-lookup"><span data-stu-id="4de81-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="4de81-115">Para expor eventos de sua classe, você deve declará-los na interface de eventos e marcá-los com um atributo `DispId`.</span><span class="sxs-lookup"><span data-stu-id="4de81-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="4de81-116">A classe não deve implementar essa interface.</span><span class="sxs-lookup"><span data-stu-id="4de81-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="4de81-117">A classe implementa a interface de classe. Ela pode implementar mais de uma interface, mas a primeira implementação será a interface de classe padrão.</span><span class="sxs-lookup"><span data-stu-id="4de81-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="4de81-118">Implemente os métodos e propriedades expostos ao COM aqui.</span><span class="sxs-lookup"><span data-stu-id="4de81-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="4de81-119">Eles devem ser marcados como públicos e devem corresponder às declarações na interface de classe.</span><span class="sxs-lookup"><span data-stu-id="4de81-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="4de81-120">Além disso, declare aqui os eventos acionados pela classe.</span><span class="sxs-lookup"><span data-stu-id="4de81-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="4de81-121">Eles devem ser marcados como públicos e devem corresponder às declarações na interface de eventos.</span><span class="sxs-lookup"><span data-stu-id="4de81-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4de81-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4de81-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4de81-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4de81-123">See also</span></span>

- [<span data-ttu-id="4de81-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4de81-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4de81-125">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="4de81-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
- [<span data-ttu-id="4de81-126">Página de Build, Designer de Projeto (C#)</span><span class="sxs-lookup"><span data-stu-id="4de81-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
