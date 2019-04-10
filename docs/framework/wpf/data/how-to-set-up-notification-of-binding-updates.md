---
title: 'Como: Configurar notificação das atualizações de associação'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213956"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="3957e-102">Como: Configurar notificação das atualizações de associação</span><span class="sxs-lookup"><span data-stu-id="3957e-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="3957e-103">Este exemplo mostra como configurar para ser notificado quando o destino de associação (destino) ou a origem da associação (origem) de uma associação foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="3957e-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3957e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3957e-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="3957e-105">gera um evento de atualização de dados sempre que a origem da associação ou o destino foi atualizado.</span><span class="sxs-lookup"><span data-stu-id="3957e-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="3957e-106">Internamente este evento é usado para informar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que ele deve atualizar, porque os dados associados foram alterados.</span><span class="sxs-lookup"><span data-stu-id="3957e-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="3957e-107">Observe que, para esses eventos funcionem e também para a associação unidirecional ou bidirecional funcione corretamente, você precisa implementar a classe de dados usando o <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="3957e-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="3957e-108">Para obter mais informações, consulte [Implementar notificação de alteração da propriedade](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="3957e-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="3957e-109">Defina as <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> ou <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> propriedade (ou ambos) para `true` na associação.</span><span class="sxs-lookup"><span data-stu-id="3957e-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="3957e-110">O manipulador fornecido para ouvir este evento deve ser anexado diretamente ao elemento do qual se espera informações de mudanças ou ao contexto geral de dados, se é preciso estar ciente de qualquer mudança no contexto.</span><span class="sxs-lookup"><span data-stu-id="3957e-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="3957e-111">Aqui temos um exemplo que mostra como configurar a notificação quando uma propriedade de destino foi atualizada.</span><span class="sxs-lookup"><span data-stu-id="3957e-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="3957e-112">Agora é possível atribuir um manipulador baseado no delegado EventHandler\<T>, *OnTargetUpdated* neste exemplo, para manipular o evento:</span><span class="sxs-lookup"><span data-stu-id="3957e-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="3957e-113">Os parâmetros do evento podem ser usados para determinar detalhes sobre a propriedade que mudou (como o tipo ou o elemento específico se o mesmo manipulador estiver conectado a mais de um elemento), o que poderá ser útil se houver várias propriedades associadas em um único elemento.</span><span class="sxs-lookup"><span data-stu-id="3957e-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3957e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3957e-114">See also</span></span>

- [<span data-ttu-id="3957e-115">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="3957e-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3957e-116">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="3957e-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
