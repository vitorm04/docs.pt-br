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
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799139"
---
# <a name="how-to-create-a-custom-panel-element"></a><span data-ttu-id="57718-102">Como criar um elemento de painel personalizado</span><span class="sxs-lookup"><span data-stu-id="57718-102">How to: Create a Custom Panel Element</span></span>
## <a name="example"></a><span data-ttu-id="57718-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57718-103">Example</span></span>  
 <span data-ttu-id="57718-104">Este exemplo mostra como substituir o comportamento de layout padrão do elemento <xref:System.Windows.Controls.Panel> e criar elementos de layout personalizados que são derivados de <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="57718-104">This example shows how to override the default layout behavior of the <xref:System.Windows.Controls.Panel> element and create custom layout elements that are derived from <xref:System.Windows.Controls.Panel>.</span></span>  
  
 <span data-ttu-id="57718-105">O exemplo define um elemento de <xref:System.Windows.Controls.Panel> personalizado simples chamado `PlotPanel`, que posiciona elementos filho de acordo com duas coordenadas x e y embutidas em código.</span><span class="sxs-lookup"><span data-stu-id="57718-105">The example defines a simple custom <xref:System.Windows.Controls.Panel> element called `PlotPanel`, which positions child elements according to two hard-coded x- and y-coordinates.</span></span> <span data-ttu-id="57718-106">Neste exemplo, `x` e `y` são definidos como `50`; Portanto, todos os elementos filho são posicionados nesse local nos eixos x e y.</span><span class="sxs-lookup"><span data-stu-id="57718-106">In this example, `x` and `y` are both set to `50`; therefore, all child elements are positioned at that location on the x and y axes.</span></span>  
  
 <span data-ttu-id="57718-107">Para implementar comportamentos de <xref:System.Windows.Controls.Panel> personalizados, o exemplo usa os métodos <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.</span><span class="sxs-lookup"><span data-stu-id="57718-107">To implement custom <xref:System.Windows.Controls.Panel> behaviors, the example uses the <xref:System.Windows.FrameworkElement.MeasureOverride%2A> and <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> methods.</span></span> <span data-ttu-id="57718-108">Cada método retorna os dados de <xref:System.Windows.Size> que são necessários para posicionar e renderizar elementos filho.</span><span class="sxs-lookup"><span data-stu-id="57718-108">Each method returns the <xref:System.Windows.Size> data that is necessary to position and render child elements.</span></span>  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="57718-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57718-109">See also</span></span>

- <xref:System.Windows.Controls.Panel>
- [<span data-ttu-id="57718-110">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="57718-110">Panels Overview</span></span>](panels-overview.md)
