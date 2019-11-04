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
# <a name="how-to-draw-text-to-a-controls-background"></a>Como desenhar texto para o plano de fundo de um controle
Você pode desenhar texto diretamente no plano de fundo de um controle convertendo uma cadeia de texto em um objeto <xref:System.Windows.Media.FormattedText> e, em seguida, desenhando o objeto para a <xref:System.Windows.Media.DrawingContext>do controle. Você também pode usar essa técnica para desenhar o plano de fundo de objetos derivados de <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.StackPanel>.  
  
 ![Captura de tela de controles que exibem texto como plano de fundo.](./media/how-to-draw-text-to-a-control-background/draw-text-background.png "DrawText2Background01")  
Exemplo de controles com telas de fundo de texto personalizado  
  
## <a name="example"></a>Exemplo  
 Para desenhar o plano de fundo de um controle, crie um novo objeto <xref:System.Windows.Media.DrawingBrush> e desenhe o texto convertido no <xref:System.Windows.Media.DrawingContext>do objeto. Em seguida, atribua o novo <xref:System.Windows.Media.DrawingBrush> à propriedade Background do controle.  
  
 O exemplo de código a seguir mostra como criar um objeto <xref:System.Windows.Media.FormattedText> e desenhar o plano de fundo de um <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Button> objeto.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.FormattedText>
- [Desenhando texto formatado](drawing-formatted-text.md)
