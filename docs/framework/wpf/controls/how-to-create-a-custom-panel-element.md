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
ms.locfileid: "33552394"
---
# <a name="how-to-create-a-custom-panel-element"></a>Como criar um elemento de painel personalizado
## <a name="example"></a>Exemplo  
 Este exemplo mostra como substituir o comportamento de layout padrão de <xref:System.Windows.Controls.Panel> elemento e criar elementos de layout personalizados que são derivados de <xref:System.Windows.Controls.Panel>.  
  
 O exemplo define um personalizado simple <xref:System.Windows.Controls.Panel> elemento chamado `PlotPanel`, que posiciona elementos filho acordo com dois embutido coordenadas x e y-. Neste exemplo, `x` e `y` são definidos como `50`; portanto, todos os elementos filho são posicionados naquele local em x e y eixos.  
  
 Para implementar personalizado <xref:System.Windows.Controls.Panel> comportamentos, o exemplo usa o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos. Cada método retorna o <xref:System.Windows.Size> dados que são necessários para posicionar e renderizar elementos filho.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Panel>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Criar um exemplo de painel de disposição de conteúdo personalizado](http://go.microsoft.com/fwlink/?LinkID=159979)
