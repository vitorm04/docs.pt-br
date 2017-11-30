---
title: Como desenhar texto para a tela de fundo de um controle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0c98422e337678e68a8e4b72979635e8c867b4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a><span data-ttu-id="ac2a9-102">Como desenhar texto para a tela de fundo de um controle</span><span class="sxs-lookup"><span data-stu-id="ac2a9-102">How to: Draw Text to a Control&#39;s Background</span></span>
<span data-ttu-id="ac2a9-103">Você pode desenhar texto diretamente para o plano de fundo de um controle ao converter uma cadeia de caracteres de texto para um <xref:System.Windows.Media.FormattedText> de objeto e, em seguida, o objeto de desenho para o controle <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="ac2a9-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="ac2a9-104">Você também pode usar essa técnica para desenhar o plano de fundo dos objetos derivados da <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="ac2a9-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="ac2a9-105">![Exibindo texto como plano de fundo de controles](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="ac2a9-105">![Controls displaying text as background](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="ac2a9-106">Exemplo de controles com telas de fundo de texto personalizado</span><span class="sxs-lookup"><span data-stu-id="ac2a9-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac2a9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac2a9-107">Example</span></span>  
 <span data-ttu-id="ac2a9-108">Para desenhar o plano de fundo de um controle, crie um novo <xref:System.Windows.Media.DrawingBrush> de objeto e desenhar o texto convertido para o objeto <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="ac2a9-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="ac2a9-109">Em seguida, atribua o novo <xref:System.Windows.Media.DrawingBrush> a propriedade de plano de fundo do controle.</span><span class="sxs-lookup"><span data-stu-id="ac2a9-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="ac2a9-110">O exemplo de código a seguir mostra como criar um <xref:System.Windows.Media.FormattedText> de objeto e desenhar o plano de fundo de um <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Button> objeto.</span><span class="sxs-lookup"><span data-stu-id="ac2a9-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="ac2a9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac2a9-111">See Also</span></span>  
 <xref:System.Windows.Media.FormattedText>  
 [<span data-ttu-id="ac2a9-112">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="ac2a9-112">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
