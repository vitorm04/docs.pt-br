---
title: 'Como: Especificar a direção da associação'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 6e617b2fdb6150aa8d5d6960f7aab58198c8b240
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550143"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="9eb6a-102">Como: Especificar a direção da associação</span><span class="sxs-lookup"><span data-stu-id="9eb6a-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="9eb6a-103">Este exemplo mostra como especificar se a associação atualiza apenas a propriedade de destino da associação (destino), a propriedade de origem da associação (origem) ou a propriedade de destino e a propriedade de origem.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eb6a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eb6a-104">Example</span></span>  
 <span data-ttu-id="9eb6a-105">Você usa o <xref:System.Windows.Data.Binding.Mode%2A> propriedade para especificar a direção da associação.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="9eb6a-106">A lista de enumeração a seguir mostra as opções disponíveis para atualizações de associação:</span><span class="sxs-lookup"><span data-stu-id="9eb6a-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="9eb6a-107"><xref:System.Windows.Data.BindingMode.TwoWay> Atualiza a propriedade de destino ou a propriedade sempre que a propriedade de destino ou a propriedade de origem é alterado.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="9eb6a-108"><xref:System.Windows.Data.BindingMode.OneWay> Atualiza a propriedade de destino somente quando a propriedade de origem é alterada.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="9eb6a-109"><xref:System.Windows.Data.BindingMode.OneTime> Atualiza a propriedade de destino somente quando o aplicativo é iniciado ou quando o <xref:System.Windows.FrameworkElement.DataContext%2A> sofrer uma alteração.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="9eb6a-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> Atualiza a propriedade de origem quando a propriedade de destino é alterado.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="9eb6a-111"><xref:System.Windows.Data.BindingMode.Default> faz com que o padrão <xref:System.Windows.Data.Binding.Mode%2A> valor da propriedade de destino a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="9eb6a-112">Para obter mais informações, consulte a enumeração <xref:System.Windows.Data.BindingMode>.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="9eb6a-113">O exemplo a seguir mostra como definir o <xref:System.Windows.Data.Binding.Mode%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="9eb6a-114">Para detectar alterações na origem (aplicáveis ao <xref:System.Windows.Data.BindingMode.OneWay> e <xref:System.Windows.Data.BindingMode.TwoWay> associações), a origem deve implementar um mecanismo de notificação de alteração de propriedade adequado, como <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="9eb6a-115">Ver [implementar notificação de alteração de propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) para obter um exemplo de um <xref:System.ComponentModel.INotifyPropertyChanged> implementação.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-115">See [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="9eb6a-116">Para <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> associações, você pode controlar o intervalo das atualizações na origem definindo o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="9eb6a-117">Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9eb6a-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb6a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eb6a-118">See also</span></span>
- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="9eb6a-119">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="9eb6a-119">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9eb6a-120">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="9eb6a-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
