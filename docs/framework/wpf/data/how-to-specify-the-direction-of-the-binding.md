---
title: Como especificar a direção da associação
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459096"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="62d0c-102">Como especificar a direção da Associação</span><span class="sxs-lookup"><span data-stu-id="62d0c-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="62d0c-103">Este exemplo mostra como especificar se a associação atualiza apenas a propriedade de destino da associação (destino), a propriedade de origem da associação (origem) ou a propriedade de destino e a propriedade de origem.</span><span class="sxs-lookup"><span data-stu-id="62d0c-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62d0c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62d0c-104">Example</span></span>  
 <span data-ttu-id="62d0c-105">Use a propriedade <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> para especificar a direção da associação.</span><span class="sxs-lookup"><span data-stu-id="62d0c-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="62d0c-106">A seguir estão as opções disponíveis para atualizações de associação:</span><span class="sxs-lookup"><span data-stu-id="62d0c-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="62d0c-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> atualiza a propriedade de destino ou a propriedade sempre que a propriedade de destino ou a propriedade de origem for alterada.</span><span class="sxs-lookup"><span data-stu-id="62d0c-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="62d0c-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> atualiza a propriedade de destino somente quando a propriedade de origem é alterada.</span><span class="sxs-lookup"><span data-stu-id="62d0c-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="62d0c-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> atualiza a propriedade de destino somente quando o aplicativo é iniciado ou quando o <xref:System.Windows.FrameworkElement.DataContext%2A> passa por uma alteração.</span><span class="sxs-lookup"><span data-stu-id="62d0c-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="62d0c-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> atualiza a propriedade Source quando a propriedade de destino é alterada.</span><span class="sxs-lookup"><span data-stu-id="62d0c-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="62d0c-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> faz com que o valor de <xref:System.Windows.Data.Binding.Mode%2A> padrão da propriedade de destino seja usado.</span><span class="sxs-lookup"><span data-stu-id="62d0c-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="62d0c-112">Para obter mais informações, consulte a enumeração <xref:System.Windows.Data.BindingMode>.</span><span class="sxs-lookup"><span data-stu-id="62d0c-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="62d0c-113">O exemplo a seguir mostra como definir a propriedade <xref:System.Windows.Data.Binding.Mode%2A>.</span><span class="sxs-lookup"><span data-stu-id="62d0c-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="62d0c-114">Para detectar alterações de origem (aplicável a associações de <xref:System.Windows.Data.BindingMode.OneWay> e <xref:System.Windows.Data.BindingMode.TwoWay>), a origem deve implementar um mecanismo de notificação de alteração de propriedade adequado, como <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="62d0c-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="62d0c-115">Consulte [implementar notificação de alteração de propriedade](how-to-implement-property-change-notification.md) para obter um exemplo de uma implementação de <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="62d0c-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="62d0c-116">Para associações <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource>, você pode controlar o tempo das atualizações de origem definindo a propriedade <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="62d0c-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="62d0c-117">Consulte <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="62d0c-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d0c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62d0c-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="62d0c-119">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="62d0c-119">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="62d0c-120">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="62d0c-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
