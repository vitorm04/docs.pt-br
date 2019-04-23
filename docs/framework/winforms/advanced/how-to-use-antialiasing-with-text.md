---
title: 'Como: usar suavização com texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 24d1b1dfbe955bcfa98a16c3be592ab837ec0182
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227607"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="7e7bd-102">Como: usar suavização com texto</span><span class="sxs-lookup"><span data-stu-id="7e7bd-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="7e7bd-103">*Suavização* refere-se para a suavização de bordas irregulares de desenhado de gráficos e texto para aprimorar sua aparência ou a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="7e7bd-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="7e7bd-104">Com o gerenciado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, você pode renderizar texto de com suavização de alta qualidade, bem como texto de qualidade inferior.</span><span class="sxs-lookup"><span data-stu-id="7e7bd-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="7e7bd-105">Normalmente, a renderização de qualidade superior leva mais tempo de processamento de renderização de qualidade inferior.</span><span class="sxs-lookup"><span data-stu-id="7e7bd-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="7e7bd-106">Para definir o nível de qualidade do texto, defina as <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriedade de um <xref:System.Drawing.Graphics> a um dos elementos do <xref:System.Drawing.Text.TextRenderingHint> enumeração</span><span class="sxs-lookup"><span data-stu-id="7e7bd-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e7bd-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e7bd-107">Example</span></span>  
 <span data-ttu-id="7e7bd-108">O exemplo de código a seguir desenha texto com duas configurações de qualidade diferente.</span><span class="sxs-lookup"><span data-stu-id="7e7bd-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 <span data-ttu-id="7e7bd-109">A ilustração a seguir mostra a saída do exemplo de código:</span><span class="sxs-lookup"><span data-stu-id="7e7bd-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Captura de tela que mostra o texto com duas configurações de qualidade diferente.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e7bd-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="7e7bd-111">Compiling the Code</span></span>  
 <span data-ttu-id="7e7bd-112">O exemplo de código anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="7e7bd-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7bd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e7bd-113">See also</span></span>

- [<span data-ttu-id="7e7bd-114">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="7e7bd-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
