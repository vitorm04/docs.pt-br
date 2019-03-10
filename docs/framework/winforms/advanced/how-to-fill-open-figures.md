---
title: 'Como: Preencher figuras abertas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
ms.openlocfilehash: e9743d3268a7a2acfb6266872c3346a05269c369
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702718"
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="a1ff3-102">Como: Preencher figuras abertas</span><span class="sxs-lookup"><span data-stu-id="a1ff3-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="a1ff3-103">Você pode preencher um caminho passando um <xref:System.Drawing.Drawing2D.GraphicsPath> do objeto para o <xref:System.Drawing.Graphics.FillPath%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="a1ff3-104">O <xref:System.Drawing.Graphics.FillPath%2A> método preenche o caminho de acordo com o modo de preenchimento (contorno ou alternativo) definido atualmente para o caminho.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="a1ff3-105">Se o caminho tiver figuras abertas, ele será preenchido como se essas figuras que foram fechadas.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="a1ff3-106">fecha uma figura desenhando uma linha reta do ponto final para o seu ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-106">closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1ff3-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1ff3-107">Example</span></span>  
 <span data-ttu-id="a1ff3-108">O exemplo a seguir cria um caminho que tem uma figura aberta (um arco) e uma figura fechada (uma elipse).</span><span class="sxs-lookup"><span data-stu-id="a1ff3-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="a1ff3-109">O <xref:System.Drawing.Graphics.FillPath%2A> método preenche o caminho de acordo com o modo de preenchimento padrão, que é <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="a1ff3-110">A ilustração a seguir mostra a saída do código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="a1ff3-111">Observe que o caminho é preenchido (acordo com a <xref:System.Drawing.Drawing2D.FillMode.Alternate>) como se a figura aberta estivesse fechada por uma linha reta do ponto final para o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="a1ff3-112">![Preencher caminho aberto](./media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="a1ff3-112">![Fill Open Path](./media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1ff3-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a1ff3-113">Compiling the Code</span></span>  
 <span data-ttu-id="a1ff3-114">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a1ff3-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ff3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1ff3-115">See also</span></span>
- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="a1ff3-116">Caminhos de Elementos Gráficos no GDI+</span><span class="sxs-lookup"><span data-stu-id="a1ff3-116">Graphics Paths in GDI+</span></span>](graphics-paths-in-gdi.md)
