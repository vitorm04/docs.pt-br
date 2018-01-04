---
title: Como nivelar um demarcador curvo em uma linha
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="6945b-102">Como nivelar um demarcador curvo em uma linha</span><span class="sxs-lookup"><span data-stu-id="6945b-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="6945b-103">Um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto armazena uma sequência de splines de Bézier e linhas.</span><span class="sxs-lookup"><span data-stu-id="6945b-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="6945b-104">Você pode adicionar vários tipos de curvas (elipses, arcos, splines cardinais) em um caminho, mas cada curva é convertida em um spline de Bézier antes de ser armazenado no caminho.</span><span class="sxs-lookup"><span data-stu-id="6945b-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="6945b-105">Mesclar um caminho consiste em converter cada spline de Bézier no caminho em uma sequência de linhas retas.</span><span class="sxs-lookup"><span data-stu-id="6945b-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="6945b-106">A ilustração a seguir mostra um caminho antes e após mesclar.</span><span class="sxs-lookup"><span data-stu-id="6945b-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="6945b-107">![Linhas retas e curvas](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="6945b-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="6945b-108">Para mesclar um caminho</span><span class="sxs-lookup"><span data-stu-id="6945b-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="6945b-109">chamar o <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método de um <xref:System.Drawing.Drawing2D.GraphicsPath> objeto.</span><span class="sxs-lookup"><span data-stu-id="6945b-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="6945b-110">O <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> método recebe um argumento de achatamento que especifica a distância máxima entre o caminho mesclado e o caminho original.</span><span class="sxs-lookup"><span data-stu-id="6945b-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6945b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6945b-111">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [<span data-ttu-id="6945b-112">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="6945b-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="6945b-113">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="6945b-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
