---
title: Como implementar notificação de alteração da propriedade
description: Habilite suas propriedades para notificar automaticamente uma fonte de associação quando o valor da propriedade for alterado em Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620775"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="a7505-103">Como implementar notificação de alteração da propriedade</span><span class="sxs-lookup"><span data-stu-id="a7505-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="a7505-104">Para oferecer suporte <xref:System.Windows.Data.BindingMode.OneWay> ou <xref:System.Windows.Data.BindingMode.TwoWay> Associação para permitir que suas propriedades de destino de associação reflitam automaticamente as alterações dinâmicas da fonte de associação (por exemplo, para que o painel de visualização seja atualizado automaticamente quando o usuário editar um formulário), sua classe precisa fornecer as notificações de propriedade alteradas adequadas.</span><span class="sxs-lookup"><span data-stu-id="a7505-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="a7505-105">Este exemplo mostra como criar uma classe que implementa <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="a7505-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7505-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7505-106">Example</span></span>  
 <span data-ttu-id="a7505-107">Para implementar <xref:System.ComponentModel.INotifyPropertyChanged> , você precisa declarar o <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> evento e criar o `OnPropertyChanged` método.</span><span class="sxs-lookup"><span data-stu-id="a7505-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="a7505-108">Em seguida, para cada propriedade para a qual você deseja alterar notificações, chame `OnPropertyChanged` sempre que a propriedade for atualizada.</span><span class="sxs-lookup"><span data-stu-id="a7505-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="a7505-109">Para ver um exemplo de como a `Person` classe pode ser usada para dar suporte à <xref:System.Windows.Data.BindingMode.TwoWay> associação, consulte [controlar quando o texto da caixa de Text atualiza a origem](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="a7505-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7505-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7505-110">See also</span></span>

- [<span data-ttu-id="a7505-111">Visão geral das origens da associação</span><span class="sxs-lookup"><span data-stu-id="a7505-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="a7505-112">Visão geral da ligação de dados</span><span class="sxs-lookup"><span data-stu-id="a7505-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a7505-113">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="a7505-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
