---
title: Como associar as propriedades de dois controles
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e79b1f9f00e8c76f94bf4386a284607f526624a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="065d1-102">Como associar as propriedades de dois controles</span><span class="sxs-lookup"><span data-stu-id="065d1-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="065d1-103">Este exemplo mostra como associar a propriedade de um controle instanciado a de outro usando o <xref:System.Windows.Data.Binding.ElementName%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="065d1-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="065d1-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="065d1-104">Example</span></span>  
 <span data-ttu-id="065d1-105">O exemplo a seguir mostra como associar o <xref:System.Windows.Controls.Panel.Background%2A> propriedade de um <xref:System.Windows.Controls.Canvas> para o <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> propriedade de um <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="065d1-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="065d1-106">Quando este exemplo é processado, ele é semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="065d1-106">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="065d1-107">![Uma tela com um plano de fundo verde](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="065d1-107">![A canvas with a green background](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="065d1-108">**Observação** a propriedade de destino de vinculação (neste exemplo, o <xref:System.Windows.Controls.Panel.Background%2A> propriedade) deve ser uma propriedade de dependência.</span><span class="sxs-lookup"><span data-stu-id="065d1-108">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="065d1-109">Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="065d1-109">For more information, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065d1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="065d1-110">See Also</span></span>  
 [<span data-ttu-id="065d1-111">Especificar a origem da associação</span><span class="sxs-lookup"><span data-stu-id="065d1-111">Specify the Binding Source</span></span>](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [<span data-ttu-id="065d1-112">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="065d1-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
