---
title: 'Como: Selecionar tinta em um controle personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
ms.openlocfilehash: 5c9b2f3d64e4cbb309772d6a1d9fa88f589df84c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173584"
---
# <a name="how-to-select-ink-from-a-custom-control"></a>Como: Selecionar tinta em um controle personalizado
Adicionando um <xref:System.Windows.Ink.IncrementalLassoHitTester> ao seu controle personalizado, você pode habilitar o controle para que um usuário possa selecionar tinta com uma ferramenta de Laço, semelhante à forma como o <xref:System.Windows.Controls.InkCanvas> seleciona tinta com um laço.  
  
 Este exemplo pressupõe que você esteja familiarizado com a criação de um controle personalizado habilitado para tinta.  Para criar um controle personalizado que aceite entrada de tinta, consulte [Criando um controle de entrada de tinta](creating-an-ink-input-control.md).  
  
## <a name="example"></a>Exemplo  
 Quando o usuário desenha um laço, o <xref:System.Windows.Ink.IncrementalLassoHitTester> prevê quais traços estarão dentro de limites do Laço depois que o usuário completá-lo.  Traços determinados como estando dentro dos limites do caminho do laço podem ser pensados como selecionados.  Traços selecionados também podem se tornar não selecionados.  Por exemplo, se o usuário inverter a direção enquanto desenha o laço, o <xref:System.Windows.Ink.IncrementalLassoHitTester> poderá cancelar a seleção de alguns traços.  
  
 O <xref:System.Windows.Ink.IncrementalLassoHitTester> aciona o <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> evento, que permite que seu controle personalizado a responder enquanto o usuário está desenhando o laço.  Por exemplo, você pode alterar a aparência dos traços conforme o usuário os marca e desmarca.  
  
## <a name="managing-the-ink-mode"></a>Gerenciando o modo de tinta  
 É útil para o usuário que o laço apareça de modo diferente da tinta no seu controle. Para fazer isso, seu controle personalizado deve controlar de se o usuário está escrevendo ou selecionando tinta. A maneira mais fácil de fazer isso é declarar uma enumeração com dois valores: um para indicar que o usuário está escrevendo tinta e outro para indicar que o usuário está selecionando tinta.  
  
 [!code-csharp[HowToSelectInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 Em seguida, adicione dois <xref:System.Windows.Ink.DrawingAttributes> à classe: um para utilizar quando o usuário grava tinta, outro para utilizar quando o usuário selecionar tinta.  No construtor, inicialize o <xref:System.Windows.Ink.DrawingAttributes> e anexe ambos <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> eventos para o mesmo manipulador de eventos. Em seguida, defina as <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriedade do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à tinta <xref:System.Windows.Ink.DrawingAttributes>.  
  
 [!code-csharp[HowToSelectInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 Adicione uma propriedade que exponha o modo de seleção. Quando o usuário altera o modo de seleção, defina a <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> propriedade do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ao apropriado <xref:System.Windows.Ink.DrawingAttributes> do objeto e, em seguida, anexe novamente o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> propriedade para o <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#5](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 Expor o <xref:System.Windows.Ink.DrawingAttributes> como propriedades para que os aplicativos possam determinar a aparência dos traços de tinta e traços de seleção.  
  
 [!code-csharp[HowToSelectInk#6](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 Quando uma propriedade de um <xref:System.Windows.Ink.DrawingAttributes> objeto alterações, o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> deve ser anexado novamente para o <xref:System.Windows.Controls.InkPresenter>.  No manipulador de eventos para o <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> eventos, anexar novamente o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> para o <xref:System.Windows.Controls.InkPresenter>.  
  
 [!code-csharp[HowToSelectInk#7](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a>Usando o IncrementalLassoHitTester  
 Criar e inicializar um <xref:System.Windows.Ink.StrokeCollection> que contém os traços selecionados.  
  
 [!code-csharp[HowToSelectInk#8](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 Quando o usuário começa a desenhar um traço, seja com tinta ou laço, desmarque quaisquer traços selecionados. Em seguida, se o usuário está desenhando um laço, crie uma <xref:System.Windows.Ink.IncrementalLassoHitTester> chamando <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, assine o <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> eventos e chamadas <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>. Esse código pode ser um método separado e chamado a partir de <xref:System.Windows.UIElement.OnStylusDown%2A> e <xref:System.Windows.UIElement.OnMouseDown%2A> métodos.  
  
 [!code-csharp[HowToSelectInk#9](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 Adicione os pontos da caneta para o <xref:System.Windows.Ink.IncrementalLassoHitTester> enquanto o usuário desenha o laço.  Chame o método a seguir da <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, e <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> métodos.  
  
 [!code-csharp[HowToSelectInk#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 Manipular o <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> eventos para responder quando o usuário seleciona e desmarca os traços.  O <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> classe tem o <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> e <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> propriedades que obtêm os traços marcados e desmarcadas, respectivamente.  
  
 [!code-csharp[HowToSelectInk#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 Quando o usuário termina de desenhar o laço, cancele a assinatura do <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> eventos e chamadas <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.  
  
 [!code-csharp[HowToSelectInk#12](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a>Juntando as peças.  
 O exemplo a seguir é um controle personalizado que permite que um usuário selecione tinta com um laço.  
  
 [!code-csharp[HowToSelectInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Ink.IncrementalLassoHitTester>
- <xref:System.Windows.Ink.StrokeCollection>
- <xref:System.Windows.Input.StylusPointCollection>
- [Criando um controle de entrada de tinta](creating-an-ink-input-control.md)
