---
title: 'Como: desenhar uma linha tracejada personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109181"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="ebb27-102">Como: desenhar uma linha tracejada personalizada</span><span class="sxs-lookup"><span data-stu-id="ebb27-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="ebb27-103">oferece diversos estilos de traço que estão listados no <xref:System.Drawing.Drawing2D.DashStyle> enumeração.</span><span class="sxs-lookup"><span data-stu-id="ebb27-103">provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="ebb27-104">Se esses estilos de traço padrão não atenderem às suas necessidades, será possível criar um padrão de traço personalizado.</span><span class="sxs-lookup"><span data-stu-id="ebb27-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebb27-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebb27-105">Example</span></span>  
 <span data-ttu-id="ebb27-106">Para desenhar uma linha tracejada personalizada, coloque os comprimentos dos traços e espaços em uma matriz e atribua a matriz como o valor da <xref:System.Drawing.Pen.DashPattern%2A> propriedade de um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="ebb27-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="ebb27-107">O exemplo a seguir desenha uma linha tracejada personalizada com base na matriz de `{5, 2, 15, 4}`.</span><span class="sxs-lookup"><span data-stu-id="ebb27-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="ebb27-108">Se você multiplicar os elementos da matriz pela largura da caneta de 5, você obterá `{25, 10, 75, 20}`.</span><span class="sxs-lookup"><span data-stu-id="ebb27-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="ebb27-109">Os traços exibidos alternam de comprimento entre 25 e 75 e os espaços alternam de comprimento entre 10 e 20.</span><span class="sxs-lookup"><span data-stu-id="ebb27-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="ebb27-110">A ilustração a seguir mostra a linha tracejada resultante.</span><span class="sxs-lookup"><span data-stu-id="ebb27-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="ebb27-111">Observe que o traço final deve ser menor do que 25 unidades para que a linha possa terminar em (405, 5).</span><span class="sxs-lookup"><span data-stu-id="ebb27-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="ebb27-112">![Ilustração que mostra uma linha tracejada. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="ebb27-112">![Illustration that shows a dashed line.](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebb27-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ebb27-113">Compiling the Code</span></span>  
 <span data-ttu-id="ebb27-114">Criar um formulário do Windows e lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos.</span><span class="sxs-lookup"><span data-stu-id="ebb27-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="ebb27-115">Cole o código anterior para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ebb27-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb27-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebb27-116">See also</span></span>

- [<span data-ttu-id="ebb27-117">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="ebb27-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
