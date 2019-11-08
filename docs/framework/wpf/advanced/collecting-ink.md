---
title: Coletar tinta em aplicativos do WPF
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
ms.openlocfilehash: 8109e0d6a746d6ca23c25643c510014c1a1e656c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740880"
---
# <a name="collect-ink"></a>Coletar tinta

A plataforma [Windows Presentation Foundation](../index.md) coleta tinta digital como uma parte importante da sua funcionalidade. Este tópico discute métodos para a coleta de tinta no Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Prerequisites

Para usar os exemplos a seguir, você deve primeiro instalar o Visual Studio e o SDK do Windows. Você também deve entender como escrever aplicativos para o WPF. Para obter mais informações sobre como começar a usar o WPF, consulte [Walkthrough: meu primeiro aplicativo de área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="use-the-inkcanvas-element"></a>Usar o elemento InkCanvas

O elemento <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> fornece a maneira mais fácil de coletar tinta no WPF. Use um elemento <xref:System.Windows.Controls.InkCanvas> para receber e exibir a entrada à tinta. Você normalmente insere tinta usando uma caneta, que interage com um digitalizador para produzir traços de tinta. Além disso, um mouse pode ser usado no lugar de uma caneta. Os traços criados são representados como objetos <xref:System.Windows.Ink.Stroke> e podem ser manipulados de forma programática e por entrada do usuário. O <xref:System.Windows.Controls.InkCanvas> permite que os usuários selecionem, modifiquem ou excluam um <xref:System.Windows.Ink.Stroke>existente.

Usando o XAML, você pode configurar a coleta de tinta tão facilmente quanto adicionar um elemento **InkCanvas** à sua árvore. O exemplo a seguir adiciona um <xref:System.Windows.Controls.InkCanvas> a um projeto padrão do WPF criado no Visual Studio:

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

O elemento **InkCanvas** também pode conter elementos filho, possibilitando a adição de recursos de anotação à tinta a praticamente qualquer tipo de elemento XAML. Por exemplo, para adicionar recursos de tinta a um elemento de texto, basta torná-lo um filho de um <xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

Adicionar suporte para marcar uma imagem com tinta é tão fácil quanto:

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>Modos de InkCollection

O <xref:System.Windows.Controls.InkCanvas> fornece suporte para vários modos de entrada por meio de sua propriedade <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.

### <a name="manipulate-ink"></a>Manipular tinta

O <xref:System.Windows.Controls.InkCanvas> fornece suporte para muitas operações de edição de tinta. Por exemplo, <xref:System.Windows.Controls.InkCanvas> dá suporte a apagamento de verso da caneta e nenhum código adicional é necessário para adicionar a funcionalidade ao elemento.

#### <a name="selection"></a>Seleção

Definir o modo de seleção é tão simples quanto definir a propriedade <xref:System.Windows.Controls.InkCanvasEditingMode> para **selecionar**.

O código a seguir define o modo de edição com base no valor de um <xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

Use a propriedade <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> para alterar a aparência dos traços de tinta. Por exemplo, o membro <xref:System.Windows.Ink.DrawingAttributes.Color%2A> de <xref:System.Windows.Ink.DrawingAttributes> define a cor da <xref:System.Windows.Ink.Stroke>renderizada.

O exemplo a seguir altera a cor dos traços selecionados para vermelho:

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

A propriedade <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> fornece acesso a propriedades como a altura, a largura e a cor dos traços a serem criados em uma <xref:System.Windows.Controls.InkCanvas>. Depois de alterar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, todos os traços futuros inseridos na <xref:System.Windows.Controls.InkCanvas> serão renderizados com os novos valores de propriedade.

Além de modificar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> no arquivo code-behind, você pode usar a sintaxe XAML para especificar <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Propriedades.

O exemplo a seguir demonstra como definir a propriedade <xref:System.Windows.Ink.DrawingAttributes.Color%2A>. Para usar esse código, crie um novo projeto do WPF chamado "HelloInkCanvas" no Visual Studio. Substitua o código no arquivo *MainWindow. XAML* pelo seguinte código:

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

Em seguida, adicione os seguintes manipuladores de eventos de botão ao arquivo code-behind, dentro da classe MainWindow:

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

Depois de copiar esse código, pressione **F5** no Visual Studio para executar o programa no depurador.

Observe como o <xref:System.Windows.Controls.StackPanel> coloca os botões na parte superior do <xref:System.Windows.Controls.InkCanvas>. Se você tentar passar a tinta sobre a parte superior dos botões, a <xref:System.Windows.Controls.InkCanvas> coleta e renderiza a tinta por trás dos botões. Isso ocorre porque os botões são irmãos da <xref:System.Windows.Controls.InkCanvas> em vez de filhos. Além disso, os botões estão mais altos na ordem z, de modo que a tinta é renderizada atrás deles.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
