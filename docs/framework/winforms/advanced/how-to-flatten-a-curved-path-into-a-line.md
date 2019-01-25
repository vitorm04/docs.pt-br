---
title: 'Como: Nivelar um demarcador curvo em uma linha'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: aa47a655417cdf82d79fb222dc6ff6f6d8c3a947
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601812"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="96898-102">Como: Nivelar um demarcador curvo em uma linha</span><span class="sxs-lookup"><span data-stu-id="96898-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="96898-103">Um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena uma sequência de linhas e splines de Bézier.</span><span class="sxs-lookup"><span data-stu-id="96898-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="96898-104">Você pode adicionar vários tipos de curvas (elipses, arcos, splines cardinais) para um caminho, mas cada curva é convertida em uma spline de Bézier antes de serem armazenado no caminho.</span><span class="sxs-lookup"><span data-stu-id="96898-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="96898-105">Mesclar um caminho consiste em converter cada spline de Bézier no caminho em uma sequência de linhas retas.</span><span class="sxs-lookup"><span data-stu-id="96898-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="96898-106">A ilustração a seguir mostra um caminho de antes e depois do ajuste.</span><span class="sxs-lookup"><span data-stu-id="96898-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="96898-107">![Linhas retas e curvas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="96898-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="96898-108">Para mesclar um caminho</span><span class="sxs-lookup"><span data-stu-id="96898-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="96898-109">Chame o <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método de um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto.</span><span class="sxs-lookup"><span data-stu-id="96898-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="96898-110">O <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método recebe um argumento de planeza que especifica a distância máxima entre o caminho mesclado e o caminho original.</span><span class="sxs-lookup"><span data-stu-id="96898-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96898-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96898-111">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [<span data-ttu-id="96898-112">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="96898-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="96898-113">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="96898-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
