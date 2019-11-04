---
title: Otimizando o desempenho do aplicativo WPF
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 98c7022eab9153808d47d7da69c23349032165c3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460855"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="89e1f-102">Otimizando o desempenho do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="89e1f-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="89e1f-103">Esta seção destina-se a ser uma referência para os desenvolvedores de aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] que estão procurando maneiras de melhorar o desempenho de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="89e1f-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="89e1f-104">Se você for um desenvolvedor que é novo no Microsoft .NET Framework e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], primeiro você deve se familiarizar com ambas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="89e1f-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="89e1f-105">Esta seção pressupõe o conhecimento prático de ambos, e é escrito para programadores que já conhecem o suficiente para colocar seus aplicativos em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="89e1f-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89e1f-106">Os dados de desempenho fornecidos nesta seção se baseiam em aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] executados em um PC de 2,8 GHz com 512 de RAM e uma placa gráfica ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="89e1f-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89e1f-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="89e1f-107">In This Section</span></span>  
 [<span data-ttu-id="89e1f-108">Planejando para desempenho do aplicativo</span><span class="sxs-lookup"><span data-stu-id="89e1f-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="89e1f-109">Aproveitando o hardware</span><span class="sxs-lookup"><span data-stu-id="89e1f-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="89e1f-110">Layout e design</span><span class="sxs-lookup"><span data-stu-id="89e1f-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="89e1f-111">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="89e1f-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="89e1f-112">Comportamento do objeto</span><span class="sxs-lookup"><span data-stu-id="89e1f-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="89e1f-113">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="89e1f-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="89e1f-114">Texto</span><span class="sxs-lookup"><span data-stu-id="89e1f-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="89e1f-115">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="89e1f-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="89e1f-116">Controles</span><span class="sxs-lookup"><span data-stu-id="89e1f-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="89e1f-117">Outras recomendações de desempenho</span><span class="sxs-lookup"><span data-stu-id="89e1f-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="89e1f-118">Tempo de inicialização do aplicativo</span><span class="sxs-lookup"><span data-stu-id="89e1f-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="89e1f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89e1f-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="89e1f-120">Camadas de renderização de gráficos</span><span class="sxs-lookup"><span data-stu-id="89e1f-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="89e1f-121">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="89e1f-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="89e1f-122">Layout</span><span class="sxs-lookup"><span data-stu-id="89e1f-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="89e1f-123">Árvores no WPF</span><span class="sxs-lookup"><span data-stu-id="89e1f-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="89e1f-124">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="89e1f-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="89e1f-125">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="89e1f-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="89e1f-126">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="89e1f-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="89e1f-127">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="89e1f-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="89e1f-128">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="89e1f-128">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="89e1f-129">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="89e1f-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="89e1f-130">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="89e1f-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="89e1f-131">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="89e1f-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="89e1f-132">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="89e1f-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="89e1f-133">Visão geral de navegação</span><span class="sxs-lookup"><span data-stu-id="89e1f-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="89e1f-134">Dicas e truques de animação</span><span class="sxs-lookup"><span data-stu-id="89e1f-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="89e1f-135">Passo a passo: armazenando dados de aplicativo em cache em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="89e1f-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
