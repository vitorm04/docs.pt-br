---
title: Como criar texto vertical
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182555"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="3d459-102">Como criar texto vertical</span><span class="sxs-lookup"><span data-stu-id="3d459-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="3d459-103">Você pode <xref:System.Drawing.StringFormat> usar um objeto para especificar que o texto seja desenhado verticalmente e não horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="3d459-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d459-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d459-104">Example</span></span>  
 <span data-ttu-id="3d459-105">O exemplo a seguir <xref:System.Drawing.StringFormatFlags.DirectionVertical> atribui <xref:System.Drawing.StringFormat.FormatFlags%2A> o <xref:System.Drawing.StringFormat> valor à propriedade de um objeto.</span><span class="sxs-lookup"><span data-stu-id="3d459-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="3d459-106">Esse <xref:System.Drawing.StringFormat> objeto é <xref:System.Drawing.Graphics.DrawString%2A> passado para <xref:System.Drawing.Graphics> o método da classe.</span><span class="sxs-lookup"><span data-stu-id="3d459-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="3d459-107">O <xref:System.Drawing.StringFormatFlags.DirectionVertical> valor é um <xref:System.Drawing.StringFormatFlags> membro da enumeração.</span><span class="sxs-lookup"><span data-stu-id="3d459-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="3d459-108">A ilustração a seguir mostra o texto vertical:</span><span class="sxs-lookup"><span data-stu-id="3d459-108">The following illustration shows the vertical text:</span></span>
  
 ![Gráfico que mostra texto de fonte vertical.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d459-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="3d459-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="3d459-111">O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e` usado com formulários <xref:System.Windows.Forms.PaintEventHandler>do Windows, e requer , que é um parâmetro de .</span><span class="sxs-lookup"><span data-stu-id="3d459-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d459-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="3d459-112">See also</span></span>

- [<span data-ttu-id="3d459-113">Como Desenhar Texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="3d459-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
