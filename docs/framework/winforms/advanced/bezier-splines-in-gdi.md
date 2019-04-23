---
title: Splines de Bézier no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107322"
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="cd598-102">Splines de Bézier no GDI+</span><span class="sxs-lookup"><span data-stu-id="cd598-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="cd598-103">Uma spline de Bézier é uma curva especificada por quatro pontos: dois pontos de extremidade (p1 e p2) e dois pontos de controle (c1 e c2).</span><span class="sxs-lookup"><span data-stu-id="cd598-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="cd598-104">A curva começa em p1 e termina em p2.</span><span class="sxs-lookup"><span data-stu-id="cd598-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="cd598-105">A curva não passa pelos pontos de controle, porém eles funcionam como ímãs, puxando a curva em determinadas direções e influenciando o modo de inclinação da curva.</span><span class="sxs-lookup"><span data-stu-id="cd598-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="cd598-106">A ilustração a seguir mostra uma curva de Bézier junto com seus pontos de extremidade e de controle.</span><span class="sxs-lookup"><span data-stu-id="cd598-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="cd598-107">![Splines de Bézier](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="cd598-107">![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="cd598-108">A curva começa em p1 e se move para o ponto de controle c1.</span><span class="sxs-lookup"><span data-stu-id="cd598-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="cd598-109">A linha tangente da curva em p1 é a linha desenhada de p1 a c1.</span><span class="sxs-lookup"><span data-stu-id="cd598-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="cd598-110">A linha tangente no ponto de extremidade em p2 é a linha desenhada de c2 a p2.</span><span class="sxs-lookup"><span data-stu-id="cd598-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="cd598-111">Desenhando splines de Bézier</span><span class="sxs-lookup"><span data-stu-id="cd598-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="cd598-112">Para desenhar uma spline de Bézier, você precisa de uma instância das <xref:System.Drawing.Graphics> classe e um <xref:System.Drawing.Pen>.</span><span class="sxs-lookup"><span data-stu-id="cd598-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="cd598-113">A instância das <xref:System.Drawing.Graphics> classe fornece a <xref:System.Drawing.Graphics.DrawBezier%2A> método e o <xref:System.Drawing.Pen> armazena atributos como largura e cor da linha usada para renderizar a curva.</span><span class="sxs-lookup"><span data-stu-id="cd598-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="cd598-114">O <xref:System.Drawing.Pen> é passado como um dos argumentos para o <xref:System.Drawing.Graphics.DrawBezier%2A> método.</span><span class="sxs-lookup"><span data-stu-id="cd598-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="cd598-115">Os argumentos restantes passados para o <xref:System.Drawing.Graphics.DrawBezier%2A> método são os pontos de extremidade e os pontos de controle.</span><span class="sxs-lookup"><span data-stu-id="cd598-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="cd598-116">O exemplo a seguir desenha uma spline de Bézier com ponto inicial (0, 0), pontos de controle (40, 20) e (80, 150) e ponto final (100, 10):</span><span class="sxs-lookup"><span data-stu-id="cd598-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="cd598-117">A ilustração a seguir mostra a curva, os pontos de controle e duas linhas tangentes.</span><span class="sxs-lookup"><span data-stu-id="cd598-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="cd598-118">![Splines de Bézier](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="cd598-118">![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="cd598-119">As splines de Bézier foram desenvolvidos originalmente por Pierre Bézier para projetos da indústria automotiva.</span><span class="sxs-lookup"><span data-stu-id="cd598-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="cd598-120">Desde então, elas se provaram úteis em vários tipos de projeto auxiliados por computador, sendo também usadas para definir os contornos de fontes.</span><span class="sxs-lookup"><span data-stu-id="cd598-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="cd598-121">Splines de Bézier podem gerar uma grande variedade de formas, algumas das quais são mostradas na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="cd598-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="cd598-122">![Demarcadores](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="cd598-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd598-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd598-123">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="cd598-124">Linhas, Curvas e Formas</span><span class="sxs-lookup"><span data-stu-id="cd598-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="cd598-125">Construir e Desenhar Curvas</span><span class="sxs-lookup"><span data-stu-id="cd598-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
- [<span data-ttu-id="cd598-126">Como: Criar objetos gráficos para desenho</span><span class="sxs-lookup"><span data-stu-id="cd598-126">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="cd598-127">Como: Criar uma caneta</span><span class="sxs-lookup"><span data-stu-id="cd598-127">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
