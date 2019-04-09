---
title: 'Como: Desenhar texto para o segundo plano de um controle'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 76449c88f9a720741c8ed61255e04a40e6a8613f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128447"
---
# <a name="how-to-draw-text-to-a-controls-background"></a><span data-ttu-id="de146-102">Como: Desenhar texto para o segundo plano de um controle</span><span class="sxs-lookup"><span data-stu-id="de146-102">How to: Draw Text to a Control's Background</span></span>
<span data-ttu-id="de146-103">Você pode desenhar texto diretamente para o plano de fundo de um controle convertendo uma cadeia de caracteres de texto para um <xref:System.Windows.Media.FormattedText> do objeto e, em seguida, desenhando o objeto para o controle <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="de146-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="de146-104">Você também pode usar essa técnica para desenhar o plano de fundo dos objetos derivados de <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="de146-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="de146-105">![Controles exibindo texto como tela de fundo](./media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="de146-105">![Controls displaying text as background](./media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="de146-106">Exemplo de controles com telas de fundo de texto personalizado</span><span class="sxs-lookup"><span data-stu-id="de146-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="de146-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de146-107">Example</span></span>  
 <span data-ttu-id="de146-108">Para desenhar o plano de fundo de um controle, crie um novo <xref:System.Windows.Media.DrawingBrush> do objeto e desenhar o texto convertido para o objeto <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="de146-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="de146-109">Em seguida, atribua o novo <xref:System.Windows.Media.DrawingBrush> a propriedade de plano de fundo do controle.</span><span class="sxs-lookup"><span data-stu-id="de146-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="de146-110">O exemplo de código a seguir mostra como criar uma <xref:System.Windows.Media.FormattedText> do objeto e desenhar o plano de fundo de um <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Button> objeto.</span><span class="sxs-lookup"><span data-stu-id="de146-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="de146-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de146-111">See also</span></span>

- <xref:System.Windows.Media.FormattedText>
- [<span data-ttu-id="de146-112">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="de146-112">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
