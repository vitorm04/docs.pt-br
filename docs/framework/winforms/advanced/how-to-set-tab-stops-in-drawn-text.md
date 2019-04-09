---
title: 'Como: definir paradas de tabulação em um texto desenhado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 68dbebfc4fab773fe749f9443d0c61883099d2ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197484"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="4ca11-102">Como: definir paradas de tabulação em um texto desenhado</span><span class="sxs-lookup"><span data-stu-id="4ca11-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="4ca11-103">Você pode definir paradas de tabulação para texto chamando o <xref:System.Drawing.StringFormat.SetTabStops%2A> método de um <xref:System.Drawing.StringFormat> objeto e, em seguida, passando <xref:System.Drawing.StringFormat> do objeto para o <xref:System.Drawing.Graphics.DrawString%2A> método da <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="4ca11-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ca11-104">O <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> faz não oferecem suporte à adição de paradas de tabulação para texto desenhado, embora você possa expandir uma guia existente deixará de usar o <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> sinalizador.</span><span class="sxs-lookup"><span data-stu-id="4ca11-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ca11-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ca11-105">Example</span></span>  
 <span data-ttu-id="4ca11-106">O exemplo a seguir define as paradas de tabulação em 150, 250 e 350.</span><span class="sxs-lookup"><span data-stu-id="4ca11-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="4ca11-107">Em seguida, o código exibe uma lista com guias de nomes e pontuações de teste.</span><span class="sxs-lookup"><span data-stu-id="4ca11-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="4ca11-108">A ilustração a seguir mostra o texto com guias:</span><span class="sxs-lookup"><span data-stu-id="4ca11-108">The following illustration shows the tabbed text:</span></span>  
  
 ![Captura de tela que mostra uma lista com guias de nomes e pontuações.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="4ca11-110">O código a seguir passa dois argumentos para o <xref:System.Drawing.StringFormat.SetTabStops%2A> método.</span><span class="sxs-lookup"><span data-stu-id="4ca11-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="4ca11-111">O segundo argumento é uma matriz que contém os deslocamentos de guia.</span><span class="sxs-lookup"><span data-stu-id="4ca11-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="4ca11-112">O primeiro argumento passado para <xref:System.Drawing.StringFormat.SetTabStops%2A> é 0, que indica que o primeiro deslocamento na matriz é medido da posição 0, a borda esquerda do retângulo delimitador.</span><span class="sxs-lookup"><span data-stu-id="4ca11-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ca11-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="4ca11-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4ca11-114">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="4ca11-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca11-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ca11-115">See also</span></span>

- [<span data-ttu-id="4ca11-116">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="4ca11-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="4ca11-117">Como: desenhar texto com o GDI</span><span class="sxs-lookup"><span data-stu-id="4ca11-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
