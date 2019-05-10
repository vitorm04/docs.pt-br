---
title: 'Como: desenhar uma linha com terminações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: 682474120cbeeeb4cb83b69188a5a125228279d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631640"
---
# <a name="how-to-draw-a-line-with-line-caps"></a><span data-ttu-id="5a98d-102">Como: desenhar uma linha com terminações</span><span class="sxs-lookup"><span data-stu-id="5a98d-102">How to: Draw a Line with Line Caps</span></span>
<span data-ttu-id="5a98d-103">Você pode desenhar o início ou término de uma linha em uma das várias formas chamadas terminações de linha.</span><span class="sxs-lookup"><span data-stu-id="5a98d-103">You can draw the start or end of a line in one of several shapes called line caps.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="5a98d-104">dá suporte a várias terminações de linha, como round, quadrado, losango e ponta de seta.</span><span class="sxs-lookup"><span data-stu-id="5a98d-104">supports several line caps, such as round, square, diamond, and arrowhead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a98d-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a98d-105">Example</span></span>  
 <span data-ttu-id="5a98d-106">Você pode especificar as terminações de linha para o início de uma linha (início cap), a fim de uma linha (limite de extremidade) ou os traços de uma linha tracejada (limite do traço).</span><span class="sxs-lookup"><span data-stu-id="5a98d-106">You can specify line caps for the start of a line (start cap), the end of a line (end cap), or the dashes of a dashed line (dash cap).</span></span>  
  
 <span data-ttu-id="5a98d-107">O exemplo a seguir desenha uma linha com uma ponta de seta em uma extremidade e uma extremidade redonda na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="5a98d-107">The following example draws a line with an arrowhead at one end and a round cap at the other end.</span></span> <span data-ttu-id="5a98d-108">A ilustração mostra a linha resultante:</span><span class="sxs-lookup"><span data-stu-id="5a98d-108">The illustration shows the resulting line:</span></span>  
  
 ![Ilustração que mostra uma linha com uma extremidade arredondada.](./media/how-to-draw-a-line-with-line-caps/line-cap-arrowhead-example.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a98d-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5a98d-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="5a98d-111">Criar um formulário do Windows e lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos.</span><span class="sxs-lookup"><span data-stu-id="5a98d-111">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="5a98d-112">Cole o código de exemplo para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos passando `e` como <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="5a98d-112">Paste the example code into the <xref:System.Windows.Forms.Control.Paint> event handler passing `e` as <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a98d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a98d-113">See also</span></span>

- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [<span data-ttu-id="5a98d-114">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5a98d-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5a98d-115">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="5a98d-115">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
