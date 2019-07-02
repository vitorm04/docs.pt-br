---
title: Construindo e desenhando curvas
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 4c1b0cc6c6f878569fcf0c392f1b6f9683ec8afc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506107"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="23587-102">Construindo e desenhando curvas</span><span class="sxs-lookup"><span data-stu-id="23587-102">Constructing and Drawing Curves</span></span>
<span data-ttu-id="23587-103">GDI+ dá suporte a vários tipos de curvas: elipses, arcos, splines cardinais e splines de Bézier.</span><span class="sxs-lookup"><span data-stu-id="23587-103">GDI+ supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="23587-104">Uma elipse é definida por seu retângulo delimitador; um arco é uma parte de uma elipse definida por um ângulo inicial e um ângulo de flecha.</span><span class="sxs-lookup"><span data-stu-id="23587-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="23587-105">Um spline cardinal é definido por uma matriz de pontos e um parâmetro de tensão – a curva passa suavemente por cada ponto na matriz e o parâmetro de tensão influencia a maneira como a curva se dobra.</span><span class="sxs-lookup"><span data-stu-id="23587-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="23587-106">Um spline de Bézier é definido por dois pontos de extremidade e dois pontos de controle. A curva não passa pelos pontos de controle, mas os pontos de controle influenciam a direção e dobram conforme a curva passa de um ponto de extremidade para o outro.</span><span class="sxs-lookup"><span data-stu-id="23587-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23587-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="23587-107">In This Section</span></span>  
 [<span data-ttu-id="23587-108">Como: Desenhar splines cardinais</span><span class="sxs-lookup"><span data-stu-id="23587-108">How to: Draw Cardinal Splines</span></span>](how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="23587-109">Descreve splines cardinais e como desenhá-los.</span><span class="sxs-lookup"><span data-stu-id="23587-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="23587-110">Como: Desenhar um único Spline de Bézier</span><span class="sxs-lookup"><span data-stu-id="23587-110">How to: Draw a Single Bézier Spline</span></span>](how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="23587-111">Descreve um spline de Bézier e como desenhá-lo.</span><span class="sxs-lookup"><span data-stu-id="23587-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="23587-112">Como: Desenhar uma sequência de Splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="23587-112">How to: Draw a Sequence of Bézier Splines</span></span>](how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="23587-113">Explica como desenhar vários splines de Bézier em sequência.</span><span class="sxs-lookup"><span data-stu-id="23587-113">Explains how to draw several Bézier splines in sequence.</span></span>
