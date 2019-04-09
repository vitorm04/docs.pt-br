---
title: 'Como: preencher uma forma com um padrão em hachura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118112"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="de849-102">Como: preencher uma forma com um padrão em hachura</span><span class="sxs-lookup"><span data-stu-id="de849-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="de849-103">Um padrão de hachura é feito de duas cores: um para o plano de fundo e outro para as linhas que formam o padrão no plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="de849-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="de849-104">Para preencher uma forma fechada com um padrão de hachura, use um <xref:System.Drawing.Drawing2D.HatchBrush> objeto.</span><span class="sxs-lookup"><span data-stu-id="de849-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="de849-105">O exemplo a seguir demonstra como preencher uma elipse com um padrão de hachura:</span><span class="sxs-lookup"><span data-stu-id="de849-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="de849-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de849-106">Example</span></span>  
 <span data-ttu-id="de849-107">O <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> construtor usa três argumentos: o estilo de hachura, a cor da linha de hachura e a cor do plano de fundo.</span><span class="sxs-lookup"><span data-stu-id="de849-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="de849-108">O argumento de estilo de hachura pode ser qualquer valor da <xref:System.Drawing.Drawing2D.HatchStyle> enumeração.</span><span class="sxs-lookup"><span data-stu-id="de849-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="de849-109">Há mais de 50 elementos no <xref:System.Drawing.Drawing2D.HatchStyle> enumeração; alguns deles elementos são mostrados na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="de849-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="de849-110">A ilustração a seguir mostra a elipse preenchida.</span><span class="sxs-lookup"><span data-stu-id="de849-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="de849-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="de849-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de849-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="de849-112">Compiling the Code</span></span>  
 <span data-ttu-id="de849-113">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="de849-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de849-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de849-114">See also</span></span>

- [<span data-ttu-id="de849-115">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="de849-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
