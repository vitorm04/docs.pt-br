---
title: Exemplo de classe COM – Guia de Programação em C#
description: Saiba como expor uma classe como um objeto COM em C#. Este exemplo adiciona código em arquivos. cs a um projeto e define o registro para a propriedade de interoperabilidade COM.
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 4ea66ba26595c5bae2e579d1cc85c4b0d58616df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303030"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="36867-104">Exemplo de classe COM (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="36867-104">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="36867-105">A seguir está um exemplo de uma classe que você poderia expor como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="36867-105">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="36867-106">Depois que esse código é colocado em um arquivo .cs e adicionado ao seu projeto, defina a propriedade **Registrar para interoperabilidade COM** como **True**.</span><span class="sxs-lookup"><span data-stu-id="36867-106">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="36867-107">Para obter mais informações, consulte [Como registrar um componente para interoperabilidade COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="36867-107">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="36867-108">A exposição de objetos do Visual C# para COM requer a declaração de uma interface de classe, de uma interface de eventos se necessário e da própria classe.</span><span class="sxs-lookup"><span data-stu-id="36867-108">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="36867-109">Os membros de classe devem seguir estas regras para ficarem visíveis ao COM:</span><span class="sxs-lookup"><span data-stu-id="36867-109">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="36867-110">A classe deve ser pública.</span><span class="sxs-lookup"><span data-stu-id="36867-110">The class must be public.</span></span>  
  
- <span data-ttu-id="36867-111">As propriedades, os métodos e os eventos devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="36867-111">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="36867-112">As propriedades e os métodos devem ser declarados na interface de classe.</span><span class="sxs-lookup"><span data-stu-id="36867-112">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="36867-113">Os eventos devem ser declarados na interface de eventos.</span><span class="sxs-lookup"><span data-stu-id="36867-113">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="36867-114">Outros membros públicos na classe que não são declarados nessas interfaces não estarão visíveis para COM, mas eles ficarão visíveis para outros objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="36867-114">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="36867-115">Para expor propriedades e métodos ao COM, você deve declará-los na interface de classe e marcá-los com um atributo `DispId` e implementá-los na classe.</span><span class="sxs-lookup"><span data-stu-id="36867-115">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="36867-116">A ordem na qual os membros são declarados na interface é a ordem usada para a vtable do COM.</span><span class="sxs-lookup"><span data-stu-id="36867-116">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="36867-117">Para expor eventos de sua classe, você deve declará-los na interface de eventos e marcá-los com um atributo `DispId`.</span><span class="sxs-lookup"><span data-stu-id="36867-117">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="36867-118">A classe não deve implementar essa interface.</span><span class="sxs-lookup"><span data-stu-id="36867-118">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="36867-119">A classe implementa a interface de classe. Ela pode implementar mais de uma interface, mas a primeira implementação será a interface de classe padrão.</span><span class="sxs-lookup"><span data-stu-id="36867-119">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="36867-120">Implemente os métodos e propriedades expostos ao COM aqui.</span><span class="sxs-lookup"><span data-stu-id="36867-120">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="36867-121">Eles devem ser marcados como públicos e devem corresponder às declarações na interface de classe.</span><span class="sxs-lookup"><span data-stu-id="36867-121">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="36867-122">Além disso, declare aqui os eventos acionados pela classe.</span><span class="sxs-lookup"><span data-stu-id="36867-122">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="36867-123">Eles devem ser marcados como públicos e devem corresponder às declarações na interface de eventos.</span><span class="sxs-lookup"><span data-stu-id="36867-123">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36867-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36867-124">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="36867-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="36867-125">See also</span></span>

- [<span data-ttu-id="36867-126">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="36867-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36867-127">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="36867-127">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="36867-128">Página de Build, Designer de Projeto (C#)</span><span class="sxs-lookup"><span data-stu-id="36867-128">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
