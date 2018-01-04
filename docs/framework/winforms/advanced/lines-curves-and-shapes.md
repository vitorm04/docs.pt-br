---
title: Linhas, curvas e formas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [Windows Forms], filling
- splines [Windows Forms], drawing
- shapes. drawing
- lines [Windows Forms], drawing
- curves [Windows Forms], drawing
ms.assetid: ace6e8d4-4e94-486b-9681-758a6667dc7f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04d93203f98c91b0d5bbed5f833745a9bb9ab1d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lines-curves-and-shapes"></a><span data-ttu-id="28a9e-102">Linhas, curvas e formas</span><span class="sxs-lookup"><span data-stu-id="28a9e-102">Lines, Curves, and Shapes</span></span>
<span data-ttu-id="28a9e-103">A parte de gráficos vetoriais de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] é usada para desenhar linhas, curvas e para desenhar e preencher formas.</span><span class="sxs-lookup"><span data-stu-id="28a9e-103">The vector graphics portion of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is used to draw lines, draw curves, and to draw and fill shapes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28a9e-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="28a9e-104">In This Section</span></span>  
 [<span data-ttu-id="28a9e-105">Visão Geral de Gráficos Vetoriais</span><span class="sxs-lookup"><span data-stu-id="28a9e-105">Vector Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)  
 <span data-ttu-id="28a9e-106">Aborda gráficos vetoriais.</span><span class="sxs-lookup"><span data-stu-id="28a9e-106">Discusses vector graphics.</span></span>  
  
 [<span data-ttu-id="28a9e-107">Canetas, Linhas e Retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-107">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 <span data-ttu-id="28a9e-108">Discute como desenhar linhas e retângulos.</span><span class="sxs-lookup"><span data-stu-id="28a9e-108">Discusses drawing lines and rectangles.</span></span>  
  
 [<span data-ttu-id="28a9e-109">Elipses e Arcos no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-109">Ellipses and Arcs in GDI+</span></span>](../../../../docs/framework/winforms/advanced/ellipses-and-arcs-in-gdi.md)  
 <span data-ttu-id="28a9e-110">Define arcos e elipses e identifica as classes necessárias para desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="28a9e-110">Defines arcs and ellipses and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="28a9e-111">Polígonos no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-111">Polygons in GDI+</span></span>](../../../../docs/framework/winforms/advanced/polygons-in-gdi.md)  
 <span data-ttu-id="28a9e-112">Define polígonos e identifica as classes necessárias para desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="28a9e-112">Defines polygons and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="28a9e-113">Splines Cardinais no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-113">Cardinal Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cardinal-splines-in-gdi.md)  
 <span data-ttu-id="28a9e-114">Define splines cardinais e identifica as classes necessárias para desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="28a9e-114">Defines cardinal splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="28a9e-115">Splines de Bézier no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-115">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 <span data-ttu-id="28a9e-116">Define splines de Bézier e identifica as classes necessárias para desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="28a9e-116">Defines Bezier splines and identifies the classes needed to draw them.</span></span>  
  
 [<span data-ttu-id="28a9e-117">Caminhos de Elementos Gráficos no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-117">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)  
 <span data-ttu-id="28a9e-118">Descreve os caminhos e como criá-los e desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="28a9e-118">Describes paths and how to create and draw them.</span></span>  
  
 [<span data-ttu-id="28a9e-119">Pincéis e Formas Preenchidas no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-119">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 <span data-ttu-id="28a9e-120">Descreve os tipos de pincel e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="28a9e-120">Describes brush types and how to use them.</span></span>  
  
 [<span data-ttu-id="28a9e-121">Curvas Abertas e Fechadas no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-121">Open and Closed Curves in GDI+</span></span>](../../../../docs/framework/winforms/advanced/open-and-closed-curves-in-gdi.md)  
 <span data-ttu-id="28a9e-122">Define as curvas abertas e fechadas e como desenhá-las e preenchê-las.</span><span class="sxs-lookup"><span data-stu-id="28a9e-122">Defines open and closed curves and how to draw and fill them.</span></span>  
  
 [<span data-ttu-id="28a9e-123">Regiões no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-123">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 <span data-ttu-id="28a9e-124">Descreve os métodos associados a regiões.</span><span class="sxs-lookup"><span data-stu-id="28a9e-124">Describes the methods associated with regions.</span></span>  
  
 [<span data-ttu-id="28a9e-125">Restringir a Superfície de Desenho no GDI+</span><span class="sxs-lookup"><span data-stu-id="28a9e-125">Restricting the Drawing Surface in GDI+</span></span>](../../../../docs/framework/winforms/advanced/restricting-the-drawing-surface-in-gdi.md)  
 <span data-ttu-id="28a9e-126">Descreve distorção e como usá-la.</span><span class="sxs-lookup"><span data-stu-id="28a9e-126">Describes clipping and how to use it.</span></span>  
  
 [<span data-ttu-id="28a9e-127">Suavização com Linhas e Curvas</span><span class="sxs-lookup"><span data-stu-id="28a9e-127">Antialiasing with Lines and Curves</span></span>](../../../../docs/framework/winforms/advanced/antialiasing-with-lines-and-curves.md)  
 <span data-ttu-id="28a9e-128">Define a suavização e como usá-la ao desenhar linhas e curvas.</span><span class="sxs-lookup"><span data-stu-id="28a9e-128">Defines antialiasing and how use antialiasing when drawing lines and curves.</span></span>
