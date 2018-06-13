---
title: Como unir linhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: cecced7b32af7187cb1ef072921f0ff28f04adad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522009"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="2505b-102">Como unir linhas</span><span class="sxs-lookup"><span data-stu-id="2505b-102">How to: Join Lines</span></span>
<span data-ttu-id="2505b-103">Uma junção de linha é a área comum que é formada por duas linhas cujas extremidades se encontram ou se sobrepõem.</span><span class="sxs-lookup"><span data-stu-id="2505b-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> <span data-ttu-id="2505b-104">O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece três estilos de junção de linha: malhete, bisel e redonda.</span><span class="sxs-lookup"><span data-stu-id="2505b-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="2505b-105">Estilo de junção de linha é uma propriedade do <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="2505b-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="2505b-106">Quando você especifica um estilo de linha de junção para um <xref:System.Drawing.Pen> do objeto, que o estilo de junção será aplicado a todas as linhas conectadas em qualquer <xref:System.Drawing.Drawing2D.GraphicsPath> objeto desenhado usando essa caneta.</span><span class="sxs-lookup"><span data-stu-id="2505b-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="2505b-107">A ilustração a seguir mostra os resultados do exemplo de junção de linha biselada.</span><span class="sxs-lookup"><span data-stu-id="2505b-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="2505b-108">![Canetas](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="2505b-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="2505b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2505b-109">Example</span></span>  
 <span data-ttu-id="2505b-110">Você pode especificar o estilo de junção de linha usando o <xref:System.Drawing.Pen.LineJoin%2A> propriedade o <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="2505b-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="2505b-111">O exemplo demonstra uma junção de linha biselada entre uma linha horizontal e uma linha vertical.</span><span class="sxs-lookup"><span data-stu-id="2505b-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="2505b-112">No código a seguir, o valor <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atribuído para o <xref:System.Drawing.Pen.LineJoin%2A> propriedade é um membro do <xref:System.Drawing.Drawing2D.LineJoin> enumeração.</span><span class="sxs-lookup"><span data-stu-id="2505b-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="2505b-113">Os outros membros do <xref:System.Drawing.Drawing2D.LineJoin> enumeração são <xref:System.Drawing.Drawing2D.LineJoin.Miter> e <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="2505b-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2505b-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2505b-114">Compiling the Code</span></span>  
 <span data-ttu-id="2505b-115">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2505b-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2505b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2505b-116">See Also</span></span>  
 [<span data-ttu-id="2505b-117">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="2505b-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
