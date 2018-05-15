---
title: Como criar um elemento de painel personalizado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 2d1581ef1d0130a6952becf36d668e6a198e1ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="5d043-102">Como criar um elemento de painel personalizado</span><span class="sxs-lookup"><span data-stu-id="5d043-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="5d043-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d043-103">Example</span></span>  
 <span data-ttu-id="5d043-104">Este exemplo mostra como substituir o comportamento de layout padrão de <xref:System.Windows.Controls.Panel> elemento e criar elementos de layout personalizados que são derivados de <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="5d043-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="5d043-105">O exemplo define um personalizado simple <xref:System.Windows.Controls.Panel> elemento chamado `PlotPanel`, que posiciona elementos filho acordo com dois embutido coordenadas x e y-.</span><span class="sxs-lookup"><span data-stu-id="5d043-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="5d043-106">Neste exemplo, `x` e `y` são definidos como `50`; portanto, todos os elementos filho são posicionados naquele local em x e y eixos.</span><span class="sxs-lookup"><span data-stu-id="5d043-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="5d043-107">Para implementar personalizado <xref:System.Windows.Controls.Panel> comportamentos, o exemplo usa o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="5d043-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="5d043-108">Cada método retorna o <xref:System.Windows.Size> dados que são necessários para posicionar e renderizar elementos filho.</span><span class="sxs-lookup"><span data-stu-id="5d043-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5d043-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d043-109">See Also</span></span>  
 <xref:System.Windows.Controls.Panel>  
 [<span data-ttu-id="5d043-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="5d043-110">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="5d043-111">Criar um exemplo de painel de disposição de conteúdo personalizado</span><span class="sxs-lookup"><span data-stu-id="5d043-111">Create a Custom Content-Wrapping Panel Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159979)
