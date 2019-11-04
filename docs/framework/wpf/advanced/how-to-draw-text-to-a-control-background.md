---
title: Como desenhar texto para o plano de fundo de um controle
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 14300f763b67c6ac67ee408de2009c328d499c13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424383"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="5971c-102">Como desenhar texto para o plano de fundo de um controle</span><span class="sxs-lookup"><span data-stu-id="5971c-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="5971c-103">Você pode desenhar texto diretamente no plano de fundo de um controle convertendo uma cadeia de texto em um objeto <xref:System.Windows.Media.FormattedText> e, em seguida, desenhando o objeto para a <xref:System.Windows.Media.DrawingContext>do controle.</span><span class="sxs-lookup"><span data-stu-id="5971c-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="5971c-104">Você também pode usar essa técnica para desenhar o plano de fundo de objetos derivados de <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="5971c-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="5971c-105">![Captura de tela de controles que exibem texto como plano de fundo.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="5971c-105">![Screenshot of controls displaying text as background.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")</span></span>  
<span data-ttu-id="5971c-106">Exemplo de controles com telas de fundo de texto personalizado</span><span class="sxs-lookup"><span data-stu-id="5971c-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="5971c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5971c-107">Example</span></span>  
 <span data-ttu-id="5971c-108">Para desenhar o plano de fundo de um controle, crie um novo objeto <xref:System.Windows.Media.DrawingBrush> e desenhe o texto convertido no <xref:System.Windows.Media.DrawingContext>do objeto.</span><span class="sxs-lookup"><span data-stu-id="5971c-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="5971c-109">Em seguida, atribua o novo <xref:System.Windows.Media.DrawingBrush> à propriedade Background do controle.</span><span class="sxs-lookup"><span data-stu-id="5971c-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="5971c-110">O exemplo de código a seguir mostra como criar um objeto <xref:System.Windows.Media.FormattedText> e desenhar o plano de fundo de um <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Button> objeto.</span><span class="sxs-lookup"><span data-stu-id="5971c-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="5971c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5971c-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="5971c-112">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="5971c-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
