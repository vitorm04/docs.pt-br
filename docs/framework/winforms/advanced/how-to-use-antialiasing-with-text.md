---
title: Como usar suavização com texto
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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182479"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="e8420-102">Como usar suavização com texto</span><span class="sxs-lookup"><span data-stu-id="e8420-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="e8420-103">*Antialiasing* refere-se à suavização de bordas irregulares de gráficos e texto desenhados para melhorar sua aparência ou legibilidade.</span><span class="sxs-lookup"><span data-stu-id="e8420-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="e8420-104">Com as classes GDI+ gerenciadas, você pode renderizar texto antialiased de alta qualidade, bem como texto de menor qualidade.</span><span class="sxs-lookup"><span data-stu-id="e8420-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="e8420-105">Normalmente, renderização de maior qualidade leva mais tempo de processamento do que renderização de qualidade inferior.</span><span class="sxs-lookup"><span data-stu-id="e8420-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="e8420-106">Para definir o nível de <xref:System.Drawing.Graphics.TextRenderingHint%2A> qualidade <xref:System.Drawing.Graphics> do texto, defina <xref:System.Drawing.Text.TextRenderingHint> a propriedade de a para um dos elementos da enumeração</span><span class="sxs-lookup"><span data-stu-id="e8420-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8420-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8420-107">Example</span></span>  
 <span data-ttu-id="e8420-108">O exemplo de código a seguir desenha texto com duas configurações de qualidade diferentes.</span><span class="sxs-lookup"><span data-stu-id="e8420-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 <span data-ttu-id="e8420-109">A ilustração a seguir mostra a saída do código de exemplo:</span><span class="sxs-lookup"><span data-stu-id="e8420-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Captura de tela que mostra texto com duas configurações de qualidade diferentes.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8420-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e8420-111">Compiling the Code</span></span>  
 <span data-ttu-id="e8420-112">O exemplo de código anterior foi projetado para <xref:System.Windows.Forms.PaintEventArgs> `e`ser usado com <xref:System.Windows.Forms.PaintEventHandler>formulários do Windows, e requer , que é um parâmetro de .</span><span class="sxs-lookup"><span data-stu-id="e8420-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8420-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8420-113">See also</span></span>

- [<span data-ttu-id="e8420-114">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="e8420-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
