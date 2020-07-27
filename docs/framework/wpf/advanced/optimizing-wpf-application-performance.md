---
title: Otimizar o desempenho do aplicativo
description: Use esses recursos para melhorar o desempenho de aplicativos Windows Presentation Foundation, como planejamento de desempenho e aproveitamento do hardware.
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 165caaf102a66988db0254839a947b8e262a386d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166327"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="43728-103">Otimizando o desempenho do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="43728-103">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="43728-104">Esta seção destina-se a ser uma referência para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] desenvolvedores de aplicativos que estão procurando maneiras de melhorar o desempenho de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="43728-104">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="43728-105">Se você for um desenvolvedor que é novo no Microsoft .NET Framework e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , primeiro, deve se familiarizar com ambas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="43728-105">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="43728-106">Esta seção pressupõe o conhecimento prático de ambos, e é escrito para programadores que já conhecem o suficiente para colocar seus aplicativos em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="43728-106">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43728-107">Os dados de desempenho fornecidos nesta seção são baseados em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos executados em um PC de 2,8 GHz com 512 de RAM e uma placa gráfica ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="43728-107">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43728-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="43728-108">In This Section</span></span>  
 [<span data-ttu-id="43728-109">Planejando-se para desempenho do aplicativo</span><span class="sxs-lookup"><span data-stu-id="43728-109">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="43728-110">Aproveitar o hardware</span><span class="sxs-lookup"><span data-stu-id="43728-110">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="43728-111">Layout e design</span><span class="sxs-lookup"><span data-stu-id="43728-111">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="43728-112">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="43728-112">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="43728-113">Comportamento do objeto</span><span class="sxs-lookup"><span data-stu-id="43728-113">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="43728-114">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="43728-114">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="43728-115">Texto</span><span class="sxs-lookup"><span data-stu-id="43728-115">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="43728-116">Associação de dados</span><span class="sxs-lookup"><span data-stu-id="43728-116">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="43728-117">Controles</span><span class="sxs-lookup"><span data-stu-id="43728-117">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="43728-118">Outras recomendações de desempenho</span><span class="sxs-lookup"><span data-stu-id="43728-118">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="43728-119">Tempo de inicialização do aplicativo</span><span class="sxs-lookup"><span data-stu-id="43728-119">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="43728-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="43728-120">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="43728-121">Camadas de renderização de gráficos</span><span class="sxs-lookup"><span data-stu-id="43728-121">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="43728-122">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="43728-122">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="43728-123">Layout</span><span class="sxs-lookup"><span data-stu-id="43728-123">Layout</span></span>](layout.md)
- [<span data-ttu-id="43728-124">Árvores no WPF</span><span class="sxs-lookup"><span data-stu-id="43728-124">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="43728-125">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="43728-125">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="43728-126">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="43728-126">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="43728-127">Visão geral das propriedades de dependência</span><span class="sxs-lookup"><span data-stu-id="43728-127">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="43728-128">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="43728-128">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="43728-129">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="43728-129">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="43728-130">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="43728-130">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="43728-131">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="43728-131">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="43728-132">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="43728-132">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="43728-133">Visão geral da ligação de dados</span><span class="sxs-lookup"><span data-stu-id="43728-133">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="43728-134">Visão geral de navegação</span><span class="sxs-lookup"><span data-stu-id="43728-134">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="43728-135">Dicas e truques de animação</span><span class="sxs-lookup"><span data-stu-id="43728-135">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="43728-136">Passo a passo: armazenar dados de aplicativo em cache em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="43728-136">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
