---
title: 'Como: Controlar quando o texto de TextBox atualiza a origem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: d1d624d7550a1135431b7fffc7450e3a510855a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966461"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Como: Controlar quando o texto de TextBox atualiza a origem
Este tópico descreve como usar a propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para controlar o tempo das atualizações de origem de associação. O tópico usa o controle <xref:System.Windows.Controls.TextBox> como um exemplo.  
  
## <a name="example"></a>Exemplo  
 A propriedade <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> tem um valor <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> padrão de <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Isso significa que, se um aplicativo tem um <xref:System.Windows.Controls.TextBox> com uma propriedade <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> associada a dados, o texto digitado no <xref:System.Windows.Controls.TextBox> não atualiza a origem até que o <xref:System.Windows.Controls.TextBox> perca o foco (por exemplo, quando você clica fora do <xref:System.Windows.Controls.TextBox>).  
  
 Se você quiser que a origem seja atualizada enquanto você digita, defina o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da associação como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. No exemplo a seguir, as linhas realçadas de código mostram que as propriedades `Text` tanto do <xref:System.Windows.Controls.TextBox> quanto do <xref:System.Windows.Controls.TextBlock> são associadas à mesma propriedade de origem. A propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da associação <xref:System.Windows.Controls.TextBox> é definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 Como resultado, o <xref:System.Windows.Controls.TextBlock> mostra o mesmo texto (porque a origem é alterada) à medida que o usuário insere texto <xref:System.Windows.Controls.TextBox>no, conforme ilustrado pela seguinte captura de tela do exemplo:  
  
 ![Captura de tela que mostra vinculação de dados simples.](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)  
  
 Se você tiver uma caixa de diálogo ou um formulário editável do usuário e desejar adiar as atualizações de origem até que o usuário termine de editar os campos e clique em "OK" <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> , você poderá definir o valor <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>de suas associações como, como no exemplo a seguir:  
  
 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Quando você define o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor como <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, o valor de origem só é alterado quando o aplicativo <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> chama o método. O exemplo a seguir mostra como chamar <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> para `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
> Você pode usar a mesma técnica para propriedades de outros controles, mas tenha em mente que a maioria das outras propriedades tem <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> um valor <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>padrão de. Para obter mais informações, consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> a página de propriedades.  
  
> [!NOTE]
> A <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Propriedade lida com as atualizações de origem e, portanto, <xref:System.Windows.Data.BindingMode.TwoWay> é <xref:System.Windows.Data.BindingMode.OneWayToSource> relevante apenas para associações ou. Para <xref:System.Windows.Data.BindingMode.TwoWay>que as associaçõesfuncionem,oobjetodeorigemprecisafornecernotificaçõesdealteraçãodepropriedade.<xref:System.Windows.Data.BindingMode.OneWayToSource> Você pode consultar os exemplos citados neste tópico para obter mais informações. Além disso, você pode examinar [Implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Consulte também

- [Tópicos de instruções](data-binding-how-to-topics.md)
