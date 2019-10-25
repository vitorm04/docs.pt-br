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
# <a name="how-to-create-a-custom-panel-element"></a>Como criar um elemento de painel personalizado
## <a name="example"></a>Exemplo  
 Este exemplo mostra como substituir o comportamento de layout padrão do elemento <xref:System.Windows.Controls.Panel> e criar elementos de layout personalizados que são derivados de <xref:System.Windows.Controls.Panel>.  
  
 O exemplo define um elemento de <xref:System.Windows.Controls.Panel> personalizado simples chamado `PlotPanel`, que posiciona elementos filho de acordo com duas coordenadas x e y embutidas em código. Neste exemplo, `x` e `y` são definidos como `50`; Portanto, todos os elementos filho são posicionados nesse local nos eixos x e y.  
  
 Para implementar comportamentos de <xref:System.Windows.Controls.Panel> personalizados, o exemplo usa os métodos <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>. Cada método retorna os dados de <xref:System.Windows.Size> que são necessários para posicionar e renderizar elementos filho.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Panel>
- [Visão geral de painéis](panels-overview.md)
