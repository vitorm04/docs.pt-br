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
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="a8035-102">Como controlar quando o texto de TextBox atualiza a origem</span><span class="sxs-lookup"><span data-stu-id="a8035-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="a8035-103">Este tópico descreve como usar o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade para controlar o intervalo das atualizações de fonte de associação.</span><span class="sxs-lookup"><span data-stu-id="a8035-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="a8035-104">O tópico usa o <xref:System.Windows.Controls.TextBox> controle como um exemplo.</span><span class="sxs-lookup"><span data-stu-id="a8035-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8035-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8035-105">Example</span></span>  
 <span data-ttu-id="a8035-106">O <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> propriedade tem um padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="a8035-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="a8035-107">Isso significa que se um aplicativo tem um <xref:System.Windows.Controls.TextBox> com uma associação de dados <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> propriedade, o texto que você digita no <xref:System.Windows.Controls.TextBox> não atualizar a fonte até que o <xref:System.Windows.Controls.TextBox> perde o foco (por exemplo, quando você clicar fora do <xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="a8035-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="a8035-108">Se você deseja a fonte a ser atualizado como você está digitando, defina o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> da associação com <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="a8035-108">If you want the source to get updated as you are typing, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="a8035-109">No exemplo a seguir, o `Text` propriedades do <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.TextBlock> estão associados à mesma propriedade de origem.</span><span class="sxs-lookup"><span data-stu-id="a8035-109">In the following example, the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="a8035-110">O <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade o <xref:System.Windows.Controls.TextBox> associação está definida como <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="a8035-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 <span data-ttu-id="a8035-111">Como resultado, o <xref:System.Windows.Controls.TextBlock> mostra o mesmo texto (porque a origem for alterada) como o usuário insere o texto para o <xref:System.Windows.Controls.TextBox>, conforme ilustrado na captura de tela a seguir do exemplo:</span><span class="sxs-lookup"><span data-stu-id="a8035-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="a8035-112">![Captura de tela do exemplo de associação de dados simples](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="a8035-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="a8035-113">Se você tiver uma caixa de diálogo ou um formulário de usuário editável e deseja adiar atualizações de origem até que o usuário terminar de editar os campos e clica em "Okey", você pode definir o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor de suas associações para <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8035-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a8035-114">Quando você define o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, o valor de origem só muda quando o aplicativo chama o <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a8035-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="a8035-115">O exemplo a seguir mostra como chamar <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> para `itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="a8035-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="a8035-116">Você pode usar a mesma técnica para as propriedades de outros controles, mas tenha em mente que a maioria das outras propriedades têm um padrão <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> valor <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="a8035-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="a8035-117">Para obter mais informações, consulte o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> página de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a8035-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8035-118">O <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> propriedade lida com as atualizações de origem e, portanto, só é relevante para <xref:System.Windows.Data.BindingMode.TwoWay> ou <xref:System.Windows.Data.BindingMode.OneWayToSource> associações.</span><span class="sxs-lookup"><span data-stu-id="a8035-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="a8035-119">Para <xref:System.Windows.Data.BindingMode.TwoWay> e <xref:System.Windows.Data.BindingMode.OneWayToSource> associações funcione, a objeto de origem precisa fornecer notificações de alteração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8035-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="a8035-120">Você pode consultar os exemplos citados neste tópico para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a8035-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="a8035-121">Além disso, você pode examinar [Implementar notificação de alteração de propriedade](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="a8035-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8035-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8035-122">See Also</span></span>  
 [<span data-ttu-id="a8035-123">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="a8035-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
