---
title: Coletando tinta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ed657de0c0e4d07fcb10b099cbf5e5c80a71fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="collecting-ink"></a>Coletando tinta
A plataforma [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) coleta tinta digital como uma parte importante da sua funcionalidade. Este tópico discute métodos para coleta de tinta no [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para usar os exemplos a seguir, você deve primeiro instalar [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] e [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Você também deve compreender como escrever aplicativos para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações sobre como começar com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consulte [passo a passo: meu primeiro aplicativo de área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="using-the-inkcanvas-element"></a>Usando o elemento InkCanvas  
 O <xref:System.Windows.Controls.InkCanvas> elemento fornece a maneira mais fácil para coletar tinta em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O <xref:System.Windows.Controls.InkCanvas> elemento é semelhante do [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) de objeto o [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] e versões anteriores.  
  
 Use um <xref:System.Windows.Controls.InkCanvas> elemento para receber e exibir a entrada à tinta. Você normalmente insere tinta usando uma caneta, que interage com um digitalizador para produzir traços de tinta. Além disso, um mouse pode ser usado no lugar de uma caneta. Os traços criados são representados como <xref:System.Windows.Ink.Stroke> objetos e eles podem ser manipulados por meio de programação e pelo usuário de entrada. O <xref:System.Windows.Controls.InkCanvas> permite aos usuários selecionar, modificar ou excluir um existente <xref:System.Windows.Ink.Stroke>.  
  
 Usando XAML, você pode configurar a coleta de tinta com a mesma facilidade que adiciona um elemento `InkCanvas` à sua árvore. O exemplo a seguir adiciona uma <xref:System.Windows.Controls.InkCanvas> com um padrão de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projeto criado no [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 O elemento `InkCanvas` também pode conter elementos filho, tornando possível adicionar recursos de anotação a tinta a quase qualquer tipo de elemento XAML. Por exemplo, para adicionar recursos de tinta a um elemento de texto, simplesmente faça-o um filho de um <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 Adicionar suporte para marcação de uma imagem com tinta é igualmente fácil.  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>Modos de InkCollection  
 O <xref:System.Windows.Controls.InkCanvas> fornece suporte para vários modos de entrada pela sua <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> propriedade.  
  
### <a name="manipulating-ink"></a>Manipulando tinta  
 O <xref:System.Windows.Controls.InkCanvas> oferece suporte a muitas operações de edição de tinta. Por exemplo, <xref:System.Windows.Controls.InkCanvas> apagar dá suporte a parte posterior da caneta sem código adicional necessário para adicionar a funcionalidade ao elemento.  
  
#### <a name="selection"></a>Seleção  
 Configurar modo de seleção é tão simple quanto a configuração de <xref:System.Windows.Controls.InkCanvasEditingMode> propriedade **selecione**. O código a seguir define o modo de edição com base no valor de uma <xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 Use o <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriedade para alterar a aparência de traços de tinta. Por exemplo, o <xref:System.Windows.Ink.DrawingAttributes.Color%2A> membro <xref:System.Windows.Ink.DrawingAttributes> define a cor de renderizado <xref:System.Windows.Ink.Stroke>. O exemplo a seguir muda a cor dos traços selecionados para vermelho.  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 O <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedade fornece acesso às propriedades, como a altura, largura e cor dos traços a serem criados em um <xref:System.Windows.Controls.InkCanvas>. Depois que você alterar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, todos os traços futuros inseridos no <xref:System.Windows.Controls.InkCanvas> são renderizados com os novos valores de propriedade.  
  
 Além de modificar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> no arquivo code-behind, você pode usar sintaxe XAML para especificar <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedades. O código XAML a seguir demonstra como definir a <xref:System.Windows.Ink.DrawingAttributes.Color%2A> propriedade. Para usar esse código, crie um novo projeto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamado "HelloInkCanvas" no Visual Studio 2005. Substitua o código no arquivo Window1.xaml pelo código a seguir.  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 Em seguida, adicione os seguintes manipuladores de eventos de botão ao arquivo code-behind, dentro da classe Window1.  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 Após copiar esse código, pressione **F5** no Microsoft Visual Studio 2005 para executar o programa no depurador.  
  
 Observe como o <xref:System.Windows.Controls.StackPanel> coloca os botões na parte superior do <xref:System.Windows.Controls.InkCanvas>. Se você tentar na parte superior dos botões, o <xref:System.Windows.Controls.InkCanvas> coleta e processa a tinta atrás dos botões. Isso ocorre porque os botões são irmãos do <xref:System.Windows.Controls.InkCanvas> em vez de filhos. Além disso, os botões estão mais altos na ordem z, de modo que a tinta é renderizada atrás deles.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
