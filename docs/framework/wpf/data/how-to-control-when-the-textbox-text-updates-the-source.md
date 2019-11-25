---
title: Como controlar quando o texto de TextBox atualiza a origem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: b211eb67e3bac95f74255935a39cc0d6aec61531
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974783"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Como controlar quando o texto de TextBox atualiza a origem
Este tópico descreve como usar a propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para controlar a temporização de atualizações de origem de associação. O tópico usa o controle de <xref:System.Windows.Controls.TextBox> como um exemplo.

## <a name="example"></a>Exemplo
 A propriedade <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> tem um valor de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> padrão de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Isso significa que, se um aplicativo tiver um <xref:System.Windows.Controls.TextBox> com uma propriedade de <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> associada a dados, o texto digitado na <xref:System.Windows.Controls.TextBox> não atualizará a origem até que a <xref:System.Windows.Controls.TextBox> perca o foco (por exemplo, quando você clicar fora da <xref:System.Windows.Controls.TextBox>).

 Se você quiser que a origem seja atualizada enquanto digita, defina o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da associação como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. No exemplo a seguir, as linhas de código realçadas mostram que as propriedades de `Text` de <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBlock> estão associadas à mesma propriedade de origem. A propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da Associação de <xref:System.Windows.Controls.TextBox> é definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 Como resultado, o <xref:System.Windows.Controls.TextBlock> mostra o mesmo texto (porque a origem é alterada) à medida que o usuário insere texto na <xref:System.Windows.Controls.TextBox>, conforme ilustrado pela seguinte captura de tela do exemplo:

 ![Captura de tela que mostra vinculação de dados simples.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 Se você tiver uma caixa de diálogo ou um formulário editável do usuário e desejar adiar as atualizações de origem até que o usuário termine de editar os campos e clique em "OK", você poderá definir o valor <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> de suas associações para <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, como no exemplo a seguir:

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 Quando você define o valor de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> como <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, o valor de origem só é alterado quando o aplicativo chama o método <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>. O exemplo a seguir mostra como chamar <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> para `itemNameTextBox`:

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> Você pode usar a mesma técnica para propriedades de outros controles, mas tenha em mente que a maioria das outras propriedades tem um valor de <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> padrão de <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Para obter mais informações, consulte a página de propriedades <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.

> [!NOTE]
> A propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> lida com atualizações de origem e, portanto, só é relevante para <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> associações. Para que as associações de <xref:System.Windows.Data.BindingMode.TwoWay> e <xref:System.Windows.Data.BindingMode.OneWayToSource> funcionem, o objeto de origem precisa fornecer notificações de alteração de propriedade. Você pode consultar os exemplos citados neste tópico para obter mais informações. Além disso, você pode examinar [Implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md).

## <a name="see-also"></a>Consulte também

- [Tópicos explicativos](data-binding-how-to-topics.md)
