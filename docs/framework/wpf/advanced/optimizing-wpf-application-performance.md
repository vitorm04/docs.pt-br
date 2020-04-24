---
title: Otimizar o desempenho do aplicativo
ms.date: 03/30/2017
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
ms.openlocfilehash: 54d69e87ef2a9c5318e394422e3bcfcabcc76210
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646256"
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="6574a-102">Otimizando o desempenho do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="6574a-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="6574a-103">Esta seção destina-se [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] como uma referência para desenvolvedores de aplicativos que estão procurando maneiras de melhorar o desempenho de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6574a-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="6574a-104">Se você é um desenvolvedor que é novo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]no Microsoft .NET Framework e, você deve primeiro se familiarizar com ambas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="6574a-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="6574a-105">Esta seção assume o conhecimento de trabalho de ambos, e é escrita para programadores que já sabem o suficiente para colocar suas aplicações em funcionamento.</span><span class="sxs-lookup"><span data-stu-id="6574a-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6574a-106">Os dados de desempenho fornecidos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesta seção são baseados em aplicativos executados em um PC de 2,8 GHz com 512 RAM e uma placa gráfica ATI Radeon 9700.</span><span class="sxs-lookup"><span data-stu-id="6574a-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6574a-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6574a-107">In This Section</span></span>  
 [<span data-ttu-id="6574a-108">Planejando-se para desempenho do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6574a-108">Planning for Application Performance</span></span>](planning-for-application-performance.md)  
  
 [<span data-ttu-id="6574a-109">Aproveitar o hardware</span><span class="sxs-lookup"><span data-stu-id="6574a-109">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="6574a-110">Layout e design</span><span class="sxs-lookup"><span data-stu-id="6574a-110">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="6574a-111">Elementos gráficos e geração de imagens 2D</span><span class="sxs-lookup"><span data-stu-id="6574a-111">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="6574a-112">Comportamento do objeto</span><span class="sxs-lookup"><span data-stu-id="6574a-112">Object Behavior</span></span>](optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="6574a-113">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6574a-113">Application Resources</span></span>](optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="6574a-114">Texto</span><span class="sxs-lookup"><span data-stu-id="6574a-114">Text</span></span>](optimizing-performance-text.md)  
  
 [<span data-ttu-id="6574a-115">Vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="6574a-115">Data Binding</span></span>](optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="6574a-116">Controles</span><span class="sxs-lookup"><span data-stu-id="6574a-116">Controls</span></span>](optimizing-performance-controls.md)  
  
 [<span data-ttu-id="6574a-117">Outras recomendações de desempenho</span><span class="sxs-lookup"><span data-stu-id="6574a-117">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="6574a-118">Tempo de inicialização do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6574a-118">Application Startup Time</span></span>](application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="6574a-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="6574a-119">See also</span></span>

- <xref:System.Windows.Media.RenderOptions>
- <xref:System.Windows.Media.RenderCapability>
- [<span data-ttu-id="6574a-120">Camadas de renderização de gráficos</span><span class="sxs-lookup"><span data-stu-id="6574a-120">Graphics Rendering Tiers</span></span>](graphics-rendering-tiers.md)
- [<span data-ttu-id="6574a-121">Visão geral de renderização de gráficos do WPF</span><span class="sxs-lookup"><span data-stu-id="6574a-121">WPF Graphics Rendering Overview</span></span>](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [<span data-ttu-id="6574a-122">Layout</span><span class="sxs-lookup"><span data-stu-id="6574a-122">Layout</span></span>](layout.md)
- [<span data-ttu-id="6574a-123">Árvores no WPF</span><span class="sxs-lookup"><span data-stu-id="6574a-123">Trees in WPF</span></span>](trees-in-wpf.md)
- [<span data-ttu-id="6574a-124">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="6574a-124">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="6574a-125">Usando objetos DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="6574a-125">Using DrawingVisual Objects</span></span>](../graphics-multimedia/using-drawingvisual-objects.md)
- [<span data-ttu-id="6574a-126">Visão geral de propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="6574a-126">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="6574a-127">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="6574a-127">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="6574a-128">Recursos XAML</span><span class="sxs-lookup"><span data-stu-id="6574a-128">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="6574a-129">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="6574a-129">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="6574a-130">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="6574a-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
- [<span data-ttu-id="6574a-131">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="6574a-131">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="6574a-132">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="6574a-132">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6574a-133">Visão geral da navegação</span><span class="sxs-lookup"><span data-stu-id="6574a-133">Navigation Overview</span></span>](../app-development/navigation-overview.md)
- [<span data-ttu-id="6574a-134">Dicas e truques de animação</span><span class="sxs-lookup"><span data-stu-id="6574a-134">Animation Tips and Tricks</span></span>](../graphics-multimedia/animation-tips-and-tricks.md)
- [<span data-ttu-id="6574a-135">Passo a passo: armazenar dados de aplicativo em cache em um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="6574a-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](walkthrough-caching-application-data-in-a-wpf-application.md)
