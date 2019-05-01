---
title: Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 3d628d75b75c311c266648886b3b971c4833d172
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972244"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="b03ac-102">Desenvolvendo controles dos Windows Forms personalizados com o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b03ac-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="b03ac-103">Os controles do Windows Forms são componentes reutilizáveis que encapsulam a funcionalidade de interface do usuário e são usados em aplicativos Windows do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="b03ac-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="b03ac-104">O Windows Forms não só fornece vários controles prontos para usar como também proporciona a infraestrutura para desenvolver seus próprios controles.</span><span class="sxs-lookup"><span data-stu-id="b03ac-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="b03ac-105">É possível combinar os controles existentes, ampliar os controles existentes e fazer seus controles personalizados.</span><span class="sxs-lookup"><span data-stu-id="b03ac-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="b03ac-106">Esta seção fornece informações básicas e exemplos para ajudar a desenvolver controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b03ac-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b03ac-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b03ac-107">In This Section</span></span>  
 [<span data-ttu-id="b03ac-108">Visão geral do uso de controles no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-108">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="b03ac-109">Destaca os elementos essenciais do uso de controles em aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b03ac-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="b03ac-110">Variedades de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="b03ac-110">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="b03ac-111">Descreve os diferentes tipos de controles personalizados, você pode criar com o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="b03ac-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="b03ac-112">Noções básicas sobre o desenvolvimento de controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-112">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="b03ac-113">Fala sobre os primeiros passos no desenvolvimento de um controle do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b03ac-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="b03ac-114">Propriedades em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-114">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="b03ac-115">Mostra como adicionar propriedades aos controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b03ac-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b03ac-116">Eventos em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-116">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="b03ac-117">Descreve como manipular e definir eventos nos controles do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b03ac-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b03ac-118">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-118">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="b03ac-119">Descreve os atributos que você pode aplicar a propriedades ou outros membros de seus controles e componentes personalizados.</span><span class="sxs-lookup"><span data-stu-id="b03ac-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="b03ac-120">Pintura e renderização de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="b03ac-120">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="b03ac-121">Mostra como personalizar a aparência de seus controles.</span><span class="sxs-lookup"><span data-stu-id="b03ac-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="b03ac-122">Layout em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-122">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="b03ac-123">Mostra como criar layouts para seus controles e formulários.</span><span class="sxs-lookup"><span data-stu-id="b03ac-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="b03ac-124">Multithreading em controles do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b03ac-124">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="b03ac-125">Mostra como implementar controles multithreaded.</span><span class="sxs-lookup"><span data-stu-id="b03ac-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b03ac-126">Referência</span><span class="sxs-lookup"><span data-stu-id="b03ac-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="b03ac-127">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="b03ac-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="b03ac-128">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="b03ac-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b03ac-129">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b03ac-129">Related Sections</span></span>  
 <span data-ttu-id="b03ac-130">[Atributos de tempo de design para componentes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b03ac-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="b03ac-131">Lista atributos de metadados para aplicar a componentes e controles para que eles sejam exibidos corretamente em tempo de design em designers visuais.</span><span class="sxs-lookup"><span data-stu-id="b03ac-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="b03ac-132">[Estendendo o suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b03ac-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="b03ac-133">Descreve como implementar classes como editores e designers que fornecem suporte ao tempo de design.</span><span class="sxs-lookup"><span data-stu-id="b03ac-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="b03ac-134">[Como: Controles e componentes de licença](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b03ac-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="b03ac-135">Descreve como implementar licenciamento em seus controles e componentes.</span><span class="sxs-lookup"><span data-stu-id="b03ac-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="b03ac-136">Consulte também [Desenvolvendo controles do Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b03ac-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>
