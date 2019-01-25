---
title: 'Como: Usar uma caneta para desenhar linhas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: e24d02c2c6ab7537f968c013eb91838eb0bb812a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730926"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="362bd-102">Como: Usar uma caneta para desenhar linhas</span><span class="sxs-lookup"><span data-stu-id="362bd-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="362bd-103">Para desenhar linhas, você precisa de uma <xref:System.Drawing.Graphics> objeto e um <xref:System.Drawing.Pen> objeto.</span><span class="sxs-lookup"><span data-stu-id="362bd-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="362bd-104">O <xref:System.Drawing.Graphics> objeto fornece os <xref:System.Drawing.Graphics.DrawLine%2A> método e o <xref:System.Drawing.Pen> objeto armazena recursos da linha, como cor e largura.</span><span class="sxs-lookup"><span data-stu-id="362bd-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="362bd-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="362bd-105">Example</span></span>  
 <span data-ttu-id="362bd-106">O exemplo a seguir desenha uma linha de (10, 20) para (300, 100).</span><span class="sxs-lookup"><span data-stu-id="362bd-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="362bd-107">A primeira instrução usa o <xref:System.Drawing.Pen.%23ctor%2A> construtor de classe para criar uma caneta preta.</span><span class="sxs-lookup"><span data-stu-id="362bd-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="362bd-108">Um argumento passado para o <xref:System.Drawing.Pen.%23ctor%2A> construtor é um <xref:System.Drawing.Color> objeto criado com o <xref:System.Drawing.Color.FromArgb%2A> método.</span><span class="sxs-lookup"><span data-stu-id="362bd-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="362bd-109">Os valores usados para criar o <xref:System.Drawing.Color> objeto — (255, 0, 0, 0) — correspondem aos componentes alfabéticos, vermelhos, verdes e azuis da cor.</span><span class="sxs-lookup"><span data-stu-id="362bd-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="362bd-110">Esses valores definem uma caneta preta opaca.</span><span class="sxs-lookup"><span data-stu-id="362bd-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="362bd-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="362bd-111">Compiling the Code</span></span>  
 <span data-ttu-id="362bd-112">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="362bd-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362bd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="362bd-113">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="362bd-114">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="362bd-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="362bd-115">Canetas, Linhas e Retângulos no GDI+</span><span class="sxs-lookup"><span data-stu-id="362bd-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
