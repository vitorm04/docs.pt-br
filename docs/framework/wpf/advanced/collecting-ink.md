---
title: Coletar tinta em aplicativos WPF
ms.date: 08/15/2018
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
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666876"
---
# <a name="collect-ink"></a>Coletar tinta

A plataforma [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) coleta tinta digital como uma parte importante da sua funcionalidade. Este tópico discute métodos para coleta de tinta no Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Pré-requisitos

Para usar os exemplos a seguir, você deve primeiro instalar o Visual Studio e o [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Você também deve compreender como escrever aplicativos para o WPF. Para obter mais informações sobre a introdução ao WPF, consulte [instruções passo a passo: meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Use o elemento InkCanvas

O <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> elemento fornece a maneira mais fácil para coletar tinta no WPF. Use um <xref:System.Windows.Controls.InkCanvas> elemento para receber e exibir a entrada de tinta. Você normalmente insere tinta usando uma caneta, que interage com um digitalizador para produzir traços de tinta. Além disso, um mouse pode ser usado no lugar de uma caneta. Os traços criados são representados como <xref:System.Windows.Ink.Stroke> objetos e eles podem ser manipulados tanto programaticamente quanto por usuário de entrada. O <xref:System.Windows.Controls.InkCanvas> permite aos usuários selecionar, modificar ou excluir um existente <xref:System.Windows.Ink.Stroke>.

Usando XAML, você pode configurar a coleta de tinta tão facilmente quanto adicionar um **InkCanvas** elemento à sua árvore. O exemplo a seguir adiciona um <xref:System.Windows.Controls.InkCanvas> a um projeto do WPF padrão criado no Visual Studio:

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

O **InkCanvas** elemento também pode conter elementos filho, tornando possível adicionar recursos de anotação a tinta a quase qualquer tipo de elemento XAML. Por exemplo, para adicionar recursos de tinta a um elemento de texto, basta torná-lo um filho de um <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Adicionando suporte para marcação de uma imagem com tinta é tão fácil:

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>Modos de InkCollection

O <xref:System.Windows.Controls.InkCanvas> oferece suporte para vários modos de entrada pela sua <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> propriedade.

### <a name="manipulate-ink"></a>Manipular tinta

O <xref:System.Windows.Controls.InkCanvas> fornece suporte para muitas operações de edição de tinta. Por exemplo, <xref:System.Windows.Controls.InkCanvas> apagar dá suporte a traseira da caneta e nenhum código adicional é necessária para adicionar a funcionalidade para o elemento.

#### <a name="selection"></a>Seleção

Configurar modo de seleção é tão simple quanto a configuração do <xref:System.Windows.Controls.InkCanvasEditingMode> propriedade para **selecione**.

O código a seguir define o modo de edição com base no valor de um <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Use o <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriedade para alterar a aparência dos traços de tinta. Por exemplo, o <xref:System.Windows.Ink.DrawingAttributes.Color%2A> membro <xref:System.Windows.Ink.DrawingAttributes> define a cor do renderizado <xref:System.Windows.Ink.Stroke>.

O exemplo a seguir altera a cor dos traços selecionados para vermelho:

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

O <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedade fornece acesso a propriedades como altura, largura e cor dos traços a serem criados em um <xref:System.Windows.Controls.InkCanvas>. Depois que você alterar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, todos os traços futuros inseridos no <xref:System.Windows.Controls.InkCanvas> são renderizados com os novos valores de propriedade.

Além de modificar as <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> no arquivo code-behind, você pode usar a sintaxe XAML para especificar <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedades.

O exemplo a seguir demonstra como definir o <xref:System.Windows.Ink.DrawingAttributes.Color%2A> propriedade. Para usar esse código, crie um novo projeto WPF chamado "HelloInkCanvas" no Visual Studio. Substitua o código na *MainWindow. XAML* arquivo pelo código a seguir:

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Em seguida, adicione os seguintes manipuladores de eventos do botão para o arquivo code-behind, dentro da classe MainWindow:

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Após copiar esse código, pressione **F5** no Visual Studio para executar o programa no depurador.

Observe como o <xref:System.Windows.Controls.StackPanel> coloca os botões na parte superior do <xref:System.Windows.Controls.InkCanvas>. Se você tentar escrever à tinta na parte superior dos botões, o <xref:System.Windows.Controls.InkCanvas> coleta e renderiza a tinta atrás dos botões. Isso ocorre porque os botões são irmãos do <xref:System.Windows.Controls.InkCanvas> em vez de filhos. Além disso, os botões estão mais altos na ordem z, de modo que a tinta é renderizada atrás deles.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>