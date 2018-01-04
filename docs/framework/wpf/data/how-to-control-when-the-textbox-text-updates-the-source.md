---
title: Como controlar quando o texto de TextBox atualiza a origem
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
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c503eb3300aba4a44c5a013c62942e7a171ae96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>Como controlar quando o texto de TextBox atualiza a origem
Este tópico descreve como usar o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade para controlar o intervalo das atualizações de fonte de associação. O tópico usa o <xref:System.Windows.Controls.TextBox> controle como um exemplo.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> propriedade tem um padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Isso significa que se um aplicativo tem um <xref:System.Windows.Controls.TextBox> com uma associação de dados <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> propriedade, o texto que você digita no <xref:System.Windows.Controls.TextBox> não atualizar a fonte até que o <xref:System.Windows.Controls.TextBox> perde o foco (por exemplo, quando você clicar fora do <xref:System.Windows.Controls.TextBox>).  
  
 Se você deseja a fonte a ser atualizado como você está digitando, defina o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da associação com <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. No exemplo a seguir, o `Text` propriedades do <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBlock> estão associados à mesma propriedade de origem. O <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade o <xref:System.Windows.Controls.TextBox> associação está definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 Como resultado, o <xref:System.Windows.Controls.TextBlock> mostra o mesmo texto (porque a origem for alterada) como o usuário insere o texto para o <xref:System.Windows.Controls.TextBox>, conforme ilustrado na captura de tela a seguir do exemplo:  
  
 ![Captura de tela do exemplo de associação de dados simples](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 Se você tiver uma caixa de diálogo ou um formulário de usuário editável e deseja adiar atualizações de origem até que o usuário terminar de editar os campos e clica em "Okey", você pode definir o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor de suas associações para <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, conforme mostrado no exemplo a seguir:  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 Quando você define o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, o valor de origem só muda quando o aplicativo chama o <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> método. O exemplo a seguir mostra como chamar <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> para `itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  Você pode usar a mesma técnica para as propriedades de outros controles, mas tenha em mente que a maioria das outras propriedades têm um padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>. Para obter mais informações, consulte o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> página de propriedades.  
  
> [!NOTE]
>  O <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade lida com as atualizações de origem e, portanto, só é relevante para <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> associações. Para <xref:System.Windows.Data.BindingMode.TwoWay> e <xref:System.Windows.Data.BindingMode.OneWayToSource> associações funcione, a objeto de origem precisa fornecer notificações de alteração de propriedade. Você pode consultar os exemplos citados neste tópico para obter mais informações. Além disso, você pode examinar [Implementar notificação de alteração de propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
