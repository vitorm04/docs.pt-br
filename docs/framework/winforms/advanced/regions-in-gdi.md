---
title: "Regiões no GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0525e7b58353909d41e5367aa52a17aa56bcd77c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="regions-in-gdi"></a><span data-ttu-id="82dba-102">Regiões no GDI+</span><span class="sxs-lookup"><span data-stu-id="82dba-102">Regions in GDI+</span></span>
<span data-ttu-id="82dba-103">Uma região é uma parte da área de exibição de um dispositivo de saída.</span><span class="sxs-lookup"><span data-stu-id="82dba-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="82dba-104">Regiões podem ser simples (um único retângulo) ou complexas (uma combinação de polígonos e curvas fechadas).</span><span class="sxs-lookup"><span data-stu-id="82dba-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="82dba-105">A ilustração a seguir mostra duas regiões: uma construída com base em um retângulo e outra construída com base em um demarcador.</span><span class="sxs-lookup"><span data-stu-id="82dba-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="82dba-106">![Regiões](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="82dba-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="82dba-107">Usando regiões</span><span class="sxs-lookup"><span data-stu-id="82dba-107">Using Regions</span></span>  
 <span data-ttu-id="82dba-108">Regiões geralmente são usadas para recortes e testes de clique.</span><span class="sxs-lookup"><span data-stu-id="82dba-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="82dba-109">Recorte significa restringir o desenho a uma determinada região da área de exibição, geralmente a parte que precisa ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="82dba-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="82dba-110">Testes de cliques significam verificar para determinar se o cursor está em uma determinada região da tela quando um botão do mouse é pressionado.</span><span class="sxs-lookup"><span data-stu-id="82dba-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="82dba-111">Você pode construir uma região com base em um retângulo ou um demarcador.</span><span class="sxs-lookup"><span data-stu-id="82dba-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="82dba-112">Você também pode criar regiões complexas combinando regiões existentes.</span><span class="sxs-lookup"><span data-stu-id="82dba-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="82dba-113">O <xref:System.Drawing.Region> classe fornece os seguintes métodos para a combinação de regiões: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, e <xref:System.Drawing.Region.Complement%2A>.</span><span class="sxs-lookup"><span data-stu-id="82dba-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="82dba-114">A interseção de duas regiões é o conjunto de todos os pontos que pertencem a ambas as regiões.</span><span class="sxs-lookup"><span data-stu-id="82dba-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="82dba-115">A união é o conjunto de todos os pontos que pertencem a uma, outra ou ambas as regiões.</span><span class="sxs-lookup"><span data-stu-id="82dba-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="82dba-116">O complemento de uma região é o conjunto de todos os pontos que não estão na região.</span><span class="sxs-lookup"><span data-stu-id="82dba-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="82dba-117">A ilustração a seguir mostra a interseção e união das duas regiões mostradas na ilustração anterior.</span><span class="sxs-lookup"><span data-stu-id="82dba-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="82dba-118">![Regiões](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="82dba-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="82dba-119">O <xref:System.Drawing.Region.Xor%2A> método, aplicado a um par de regiões, gera uma região que contém todos os pontos que pertencem a uma região ou o outro, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="82dba-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="82dba-120">O <xref:System.Drawing.Region.Exclude%2A> método, aplicado a um par de regiões, gera uma região que contém todos os pontos na primeira região que não estão na segunda região.</span><span class="sxs-lookup"><span data-stu-id="82dba-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="82dba-121">A ilustração a seguir mostra as regiões resultantes da aplicação de <xref:System.Drawing.Region.Xor%2A> e <xref:System.Drawing.Region.Exclude%2A> métodos para duas regiões mostrados no início deste tópico.</span><span class="sxs-lookup"><span data-stu-id="82dba-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="82dba-122">![Regiões](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="82dba-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="82dba-123">Para preencher uma região, é necessário um <xref:System.Drawing.Graphics> objeto, um <xref:System.Drawing.Brush> objeto e um <xref:System.Drawing.Region> objeto.</span><span class="sxs-lookup"><span data-stu-id="82dba-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="82dba-124">O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.FillRegion%2A> método e o <xref:System.Drawing.Brush> objeto armazena atributos de preenchimento, como cor ou o padrão.</span><span class="sxs-lookup"><span data-stu-id="82dba-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="82dba-125">O exemplo a seguir preenche uma região com uma cor sólida.</span><span class="sxs-lookup"><span data-stu-id="82dba-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="82dba-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82dba-126">See Also</span></span>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="82dba-127">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="82dba-127">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="82dba-128">Usando regiões</span><span class="sxs-lookup"><span data-stu-id="82dba-128">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
