---
title: 'Como: Associar as propriedades de dois controles'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: f3355969d0f12f0f3ed9b49bdb7efa6913c5e4c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372094"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="c9ec8-102">Como: Associar as propriedades de dois controles</span><span class="sxs-lookup"><span data-stu-id="c9ec8-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="c9ec8-103">Este exemplo mostra como associar a propriedade de um controle instanciado a de outro usando o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c9ec8-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ec8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9ec8-104">Example</span></span>  
 <span data-ttu-id="c9ec8-105">O exemplo a seguir mostra como associar o <xref:System.Windows.Controls.Panel.Background%2A> propriedade de um <xref:System.Windows.Controls.Canvas> para o <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="c9ec8-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="c9ec8-106">propriedade de um <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="c9ec8-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="c9ec8-107">Quando este exemplo é renderizado, ele é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c9ec8-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="c9ec8-108">![Uma tela com um plano de fundo verde](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="c9ec8-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="c9ec8-109">**Observação** a propriedade de destino de associação (neste exemplo, o <xref:System.Windows.Controls.Panel.Background%2A> propriedade) deve ser uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="c9ec8-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="c9ec8-110">Para obter mais informações, consulte [Visão geral de vinculação de dados](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9ec8-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ec8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9ec8-111">See also</span></span>
- [<span data-ttu-id="c9ec8-112">Especificar a origem da associação</span><span class="sxs-lookup"><span data-stu-id="c9ec8-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="c9ec8-113">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="c9ec8-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
