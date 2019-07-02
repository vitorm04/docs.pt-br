---
title: 'Como: unir linhas'
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
ms.openlocfilehash: 362ce0c701d6e5f640fecd143a60cf471045629c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505871"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="387d5-102">Como: unir linhas</span><span class="sxs-lookup"><span data-stu-id="387d5-102">How to: Join Lines</span></span>
<span data-ttu-id="387d5-103">Uma junção de linha é a área comum que é formada por duas linhas cujas extremidades se encontram ou se sobrepõem.</span><span class="sxs-lookup"><span data-stu-id="387d5-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> <span data-ttu-id="387d5-104">GDI+ fornece três estilos de junção de linha: Malhete, Bisel e redonda.</span><span class="sxs-lookup"><span data-stu-id="387d5-104">GDI+ provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="387d5-105">Estilo da linha de junção é uma propriedade do <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="387d5-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="387d5-106">Quando você especifica um estilo de junção de linha para um <xref:System.Drawing.Pen> do objeto, que o estilo de junção será aplicado a todas as linhas conectadas em qualquer <xref:System.Drawing.Drawing2D.GraphicsPath> objeto desenhado usando essa caneta.</span><span class="sxs-lookup"><span data-stu-id="387d5-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="387d5-107">A ilustração a seguir mostra os resultados do exemplo de junção de linha biselada.</span><span class="sxs-lookup"><span data-stu-id="387d5-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 ![Ilustração que mostra linhas unidas.](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a><span data-ttu-id="387d5-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="387d5-109">Example</span></span>  
 <span data-ttu-id="387d5-110">Você pode especificar o estilo de junção de linha usando o <xref:System.Drawing.Pen.LineJoin%2A> propriedade do <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="387d5-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="387d5-111">O exemplo demonstra uma junção de linha biselada entre uma linha horizontal e uma linha vertical.</span><span class="sxs-lookup"><span data-stu-id="387d5-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="387d5-112">No código a seguir, o valor <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atribuídas para o <xref:System.Drawing.Pen.LineJoin%2A> propriedade é um membro do <xref:System.Drawing.Drawing2D.LineJoin> enumeração.</span><span class="sxs-lookup"><span data-stu-id="387d5-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="387d5-113">Os outros membros dos <xref:System.Drawing.Drawing2D.LineJoin> enumeração estão <xref:System.Drawing.Drawing2D.LineJoin.Miter> e <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="387d5-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="387d5-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="387d5-114">Compiling the Code</span></span>  
 <span data-ttu-id="387d5-115">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="387d5-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="387d5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="387d5-116">See also</span></span>

- [<span data-ttu-id="387d5-117">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="387d5-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
