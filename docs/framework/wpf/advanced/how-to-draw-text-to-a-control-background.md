---
title: 'Como: Desenhar texto para o plano de fundo de um controle'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: 9be4eb92021a62baaf6b43198587616d00cc265e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259248"
---
# <a name="how-to-draw-text-to-a-controls-background"></a>Como: Desenhar texto para o plano de fundo de um controle
Você pode desenhar texto diretamente para o plano de fundo de um controle convertendo uma cadeia de caracteres de texto para um <xref:System.Windows.Media.FormattedText> do objeto e, em seguida, desenhando o objeto para o controle <xref:System.Windows.Media.DrawingContext>. Você também pode usar essa técnica para desenhar o plano de fundo dos objetos derivados de <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.StackPanel>.  
  
 ![Controles exibindo texto como tela de fundo](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Exemplo de controles com telas de fundo de texto personalizado  
  
## <a name="example"></a>Exemplo  
 Para desenhar o plano de fundo de um controle, crie um novo <xref:System.Windows.Media.DrawingBrush> do objeto e desenhar o texto convertido para o objeto <xref:System.Windows.Media.DrawingContext>. Em seguida, atribua o novo <xref:System.Windows.Media.DrawingBrush> a propriedade de plano de fundo do controle.  
  
 O exemplo de código a seguir mostra como criar uma <xref:System.Windows.Media.FormattedText> do objeto e desenhar o plano de fundo de um <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Button> objeto.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.FormattedText>
- [Desenhando texto formatado](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
