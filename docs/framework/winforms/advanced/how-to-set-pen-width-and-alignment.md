---
title: 'Como: Largura da caneta conjunto e alinhamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: d1a465fb7c1cd6d4064a077e592daefebf590714
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564819"
---
# <a name="how-to-set-pen-width-and-alignment"></a><span data-ttu-id="cc8a9-102">Como: Largura da caneta conjunto e alinhamento</span><span class="sxs-lookup"><span data-stu-id="cc8a9-102">How to: Set Pen Width and Alignment</span></span>
<span data-ttu-id="cc8a9-103">Quando você cria um <xref:System.Drawing.Pen>, você pode fornecer a largura da caneta como um dos argumentos para o construtor.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-103">When you create a <xref:System.Drawing.Pen>, you can supply the pen width as one of the arguments to the constructor.</span></span> <span data-ttu-id="cc8a9-104">Você também pode alterar a largura da caneta com a <xref:System.Drawing.Pen.Width%2A> propriedade do <xref:System.Drawing.Pen> classe.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-104">You can also change the pen width with the <xref:System.Drawing.Pen.Width%2A> property of the <xref:System.Drawing.Pen> class.</span></span>  
  
 <span data-ttu-id="cc8a9-105">Uma linha teórica tem uma largura de 0.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-105">A theoretical line has a width of 0.</span></span> <span data-ttu-id="cc8a9-106">Quando você desenha uma linha com um pixel de largura, os pixels são centralizados na linha teórica.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-106">When you draw a line that is 1 pixel wide, the pixels are centered on the theoretical line.</span></span> <span data-ttu-id="cc8a9-107">Se você desenhar uma linha contendo mais de um pixel de largura, os pixels serão centralizados na linha teórica ou aparecerão em um dos lados da linha teórica.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-107">If you draw a line that is more than one pixel wide, the pixels are either centered on the theoretical line or appear to one side of the theoretical line.</span></span> <span data-ttu-id="cc8a9-108">Você pode definir a propriedade de alinhamento da caneta de um <xref:System.Drawing.Pen> para determinar como os pixels desenhados com essa caneta serão posicionados em relação ao linhas teóricas.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-108">You can set the pen alignment property of a <xref:System.Drawing.Pen> to determine how the pixels drawn with that pen will be positioned relative to theoretical lines.</span></span>  
  
 <span data-ttu-id="cc8a9-109">Os valores <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, e <xref:System.Drawing.Drawing2D.PenAlignment.Inset> que aparecem nas seguintes exemplos de código são membros do <xref:System.Drawing.Drawing2D.PenAlignment> enumeração.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-109">The values <xref:System.Drawing.Drawing2D.PenAlignment.Center>, <xref:System.Drawing.Drawing2D.PenAlignment.Outset>, and <xref:System.Drawing.Drawing2D.PenAlignment.Inset> that appear in the following code examples are members of the <xref:System.Drawing.Drawing2D.PenAlignment> enumeration.</span></span>  
  
 <span data-ttu-id="cc8a9-110">O exemplo de código a seguir desenha uma linha duas vezes: uma vez com uma caneta preta da largura 1 e uma vez com uma caneta verde da largura 10.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-110">The following code example draws a line twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
### <a name="to-vary-the-width-of-a-pen"></a><span data-ttu-id="cc8a9-111">Variar a largura da caneta</span><span class="sxs-lookup"><span data-stu-id="cc8a9-111">To vary the width of a pen</span></span>  
  
-   <span data-ttu-id="cc8a9-112">Defina o valor da <xref:System.Drawing.Pen.Alignment%2A> propriedade para <xref:System.Drawing.Drawing2D.PenAlignment.Center> (o padrão) para especificar que os pixels desenhados com a caneta verde serão centralizados na linha teórica.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-112">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> (the default) to specify that pixels drawn with the green pen will be centered on the theoretical line.</span></span> <span data-ttu-id="cc8a9-113">A ilustração a seguir mostra a linha resultante.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-113">The following illustration shows the resulting line.</span></span>  
  
     <span data-ttu-id="cc8a9-114">![Canetas](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span><span class="sxs-lookup"><span data-stu-id="cc8a9-114">![Pens](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")</span></span>  
  
     <span data-ttu-id="cc8a9-115">O exemplo de código a seguir desenha um retângulo duas vezes: uma vez com uma caneta preta da largura 1 e uma vez com uma caneta verde da largura 10.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-115">The following code example draws a rectangle twice: once with a black pen of width 1 and once with a green pen of width 10.</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a><span data-ttu-id="cc8a9-116">Alterar o alinhamento de uma caneta</span><span class="sxs-lookup"><span data-stu-id="cc8a9-116">To change the alignment of a pen</span></span>  
  
-   <span data-ttu-id="cc8a9-117">Defina o valor da <xref:System.Drawing.Pen.Alignment%2A> propriedade para <xref:System.Drawing.Drawing2D.PenAlignment.Center> para especificar que os pixels desenhados com a caneta verde serão centralizados no limite do retângulo.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-117">Set the value of the <xref:System.Drawing.Pen.Alignment%2A> property to <xref:System.Drawing.Drawing2D.PenAlignment.Center> to specify that the pixels drawn with the green pen will be centered on the boundary of the rectangle.</span></span>  
  
     <span data-ttu-id="cc8a9-118">A ilustração a seguir mostra o retângulo resultante.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-118">The following illustration shows the resulting rectangle.</span></span>  
  
     <span data-ttu-id="cc8a9-119">![Canetas](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span><span class="sxs-lookup"><span data-stu-id="cc8a9-119">![Pens](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a><span data-ttu-id="cc8a9-120">Criar uma caneta de baixo-relevo</span><span class="sxs-lookup"><span data-stu-id="cc8a9-120">To create an inset pen</span></span>  
  
-   <span data-ttu-id="cc8a9-121">Altere o alinhamento da caneta verde modificando a terceira instrução no exemplo de código anterior da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cc8a9-121">Change the green pen's alignment by modifying the third statement in the preceding code example as follows:</span></span>  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     <span data-ttu-id="cc8a9-122">Agora os pixels na linha verde larga aparecem no interior do retângulo conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="cc8a9-122">Now the pixels in the wide green line appear on the inside of the rectangle as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="cc8a9-123">![Canetas](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span><span class="sxs-lookup"><span data-stu-id="cc8a9-123">![Pens](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc8a9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc8a9-124">See also</span></span>
- [<span data-ttu-id="cc8a9-125">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="cc8a9-125">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="cc8a9-126">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc8a9-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
