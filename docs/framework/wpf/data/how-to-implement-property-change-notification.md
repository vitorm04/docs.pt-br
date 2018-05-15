---
title: Como implementar notificação de alteração da propriedade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="70b5b-102">Como implementar notificação de alteração da propriedade</span><span class="sxs-lookup"><span data-stu-id="70b5b-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="70b5b-103">Para dar suporte a <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> para habilitar suas propriedades de destino de associação refletir automaticamente alterações dinâmicas da fonte de associação (por exemplo, para o painel de visualização atualizadas automaticamente quando o usuário edita um formulário), sua classe Você precisa fornecer as notificações de alteração de propriedade adequadas.</span><span class="sxs-lookup"><span data-stu-id="70b5b-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="70b5b-104">Este exemplo mostra como criar uma classe que implementa <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="70b5b-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b5b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70b5b-105">Example</span></span>  
 <span data-ttu-id="70b5b-106">Para implementar <xref:System.ComponentModel.INotifyPropertyChanged> é necessário declarar a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> eventos e crie o `OnPropertyChanged` método.</span><span class="sxs-lookup"><span data-stu-id="70b5b-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="70b5b-107">Em seguida, para cada propriedade que você deseja notificações de alterações, chame `OnPropertyChanged` sempre que a propriedade é atualizada.</span><span class="sxs-lookup"><span data-stu-id="70b5b-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="70b5b-108">Para ver um exemplo de como o `Person` classe pode ser usada para oferecer suporte a <xref:System.Windows.Data.BindingMode.TwoWay> de associação, consulte [controlar quando o texto da caixa de texto atualiza a fonte](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="70b5b-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b5b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70b5b-109">See Also</span></span>  
 [<span data-ttu-id="70b5b-110">Visão geral das origens da associação</span><span class="sxs-lookup"><span data-stu-id="70b5b-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="70b5b-111">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="70b5b-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="70b5b-112">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="70b5b-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
