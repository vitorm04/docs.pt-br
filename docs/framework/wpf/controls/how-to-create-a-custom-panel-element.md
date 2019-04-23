---
title: 'Como: Criar um elemento de painel personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: d4fc9d76ada9f27bd52619280b323691af9382c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139562"
---
# <a name="how-to-create-a-custom-panel-element"></a>Como: Criar um elemento de painel personalizado
## <a name="example"></a>Exemplo  
 Este exemplo mostra como substituir o comportamento de layout de padrão para o <xref:System.Windows.Controls.Panel> elemento e criar elementos de layout personalizados que são derivados de <xref:System.Windows.Controls.Panel>.  
  
 O exemplo define um personalizado simple <xref:System.Windows.Controls.Panel> elemento chamado `PlotPanel`, que posiciona elementos filho acordo com dois embutidos coordenadas x e y-. Neste exemplo, `x` e `y` são definidos como `50`; portanto, todos os elementos filho são posicionados nesse local nos x e y eixos.  
  
 Para implementar personalizado <xref:System.Windows.Controls.Panel> comportamentos, o exemplo usa o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos. Cada método retorna o <xref:System.Windows.Size> dados que são necessários para posicionar e renderizar elementos filho.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Panel>
- [Visão geral de painéis](panels-overview.md)
- [Criar uma amostra de painel de encapsulamento com conteúdo personalizado](https://go.microsoft.com/fwlink/?LinkID=159979)
