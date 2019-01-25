---
title: 'Como: Criar figuras usando linhas, curvas e formas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: cb0b13b8c7b27d6c85cc969f10c126df26a14acf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707824"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="0b836-102">Como: Criar figuras usando linhas, curvas e formas</span><span class="sxs-lookup"><span data-stu-id="0b836-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="0b836-103">Para criar uma figura, construa uma <xref:System.Drawing.Drawing2D.GraphicsPath>e, em seguida, chamar métodos, como <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> e <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, para adicionar primitivos ao caminho.</span><span class="sxs-lookup"><span data-stu-id="0b836-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b836-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b836-104">Example</span></span>  
 <span data-ttu-id="0b836-105">Os exemplos de código a seguir criam caminhos que têm figuras:</span><span class="sxs-lookup"><span data-stu-id="0b836-105">The following code examples create paths that have figures:</span></span>  
  
-   <span data-ttu-id="0b836-106">O primeiro exemplo cria um caminho que contém uma figura única.</span><span class="sxs-lookup"><span data-stu-id="0b836-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="0b836-107">A figura consiste em um único arco. O arco tem um ângulo de flecha de -180 graus, no sentido anti-horário no sistema de coordenadas padrão.</span><span class="sxs-lookup"><span data-stu-id="0b836-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
-   <span data-ttu-id="0b836-108">O segundo exemplo cria um caminho que contém duas figuras.</span><span class="sxs-lookup"><span data-stu-id="0b836-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="0b836-109">A primeira figura é um arco seguido por uma linha.</span><span class="sxs-lookup"><span data-stu-id="0b836-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="0b836-110">A segunda figura é uma linha seguida por uma curva seguida por uma linha.</span><span class="sxs-lookup"><span data-stu-id="0b836-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="0b836-111">A primeira figura foi deixada aberta e a segunda figura está fechada.</span><span class="sxs-lookup"><span data-stu-id="0b836-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b836-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0b836-112">Compiling the Code</span></span>  
 <span data-ttu-id="0b836-113">Os exemplos anteriores são projetados para uso com o Windows Forms e exigem <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0b836-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b836-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b836-114">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="0b836-115">Construindo e desenhando demarcadores</span><span class="sxs-lookup"><span data-stu-id="0b836-115">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
- [<span data-ttu-id="0b836-116">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="0b836-116">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
