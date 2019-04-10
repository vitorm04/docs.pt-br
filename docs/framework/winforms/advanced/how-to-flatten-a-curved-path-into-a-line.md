---
title: 'Como: nivelar um caminho curvo em uma linha'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a151b4244e14d3704fd5fa1c55de92211981232f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215151"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="e3fc7-102">Como: nivelar um caminho curvo em uma linha</span><span class="sxs-lookup"><span data-stu-id="e3fc7-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="e3fc7-103">Um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena uma sequência de linhas e splines de Bézier.</span><span class="sxs-lookup"><span data-stu-id="e3fc7-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="e3fc7-104">Você pode adicionar vários tipos de curvas (elipses, arcos, splines cardinais) para um caminho, mas cada curva é convertida em uma spline de Bézier antes de serem armazenado no caminho.</span><span class="sxs-lookup"><span data-stu-id="e3fc7-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="e3fc7-105">Mesclar um caminho consiste em converter cada spline de Bézier no caminho em uma sequência de linhas retas.</span><span class="sxs-lookup"><span data-stu-id="e3fc7-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="e3fc7-106">A ilustração a seguir mostra um caminho de antes e depois do ajuste.</span><span class="sxs-lookup"><span data-stu-id="e3fc7-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="e3fc7-107">![Linhas retas e curvas](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="e3fc7-107">![Straight Lines and Curves](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="e3fc7-108">Para mesclar um caminho</span><span class="sxs-lookup"><span data-stu-id="e3fc7-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="e3fc7-109">Chame o <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método de um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto.</span><span class="sxs-lookup"><span data-stu-id="e3fc7-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="e3fc7-110">O <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método recebe um argumento de planeza que especifica a distância máxima entre o caminho mesclado e o caminho original.</span><span class="sxs-lookup"><span data-stu-id="e3fc7-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3fc7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3fc7-111">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [<span data-ttu-id="e3fc7-112">Linhas, curvas e formas</span><span class="sxs-lookup"><span data-stu-id="e3fc7-112">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="e3fc7-113">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="e3fc7-113">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
