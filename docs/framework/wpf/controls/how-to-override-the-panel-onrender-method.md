---
title: 'Como: Substituir o método OnRender do painel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
ms.openlocfilehash: bb2ccffd9eda46eff2c7ee098a5261fc8f128cab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702867"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Como: Substituir o método OnRender do painel
Este exemplo mostra como substituir a <xref:System.Windows.Controls.Panel.OnRender%2A> método de <xref:System.Windows.Controls.Panel> para adicionar efeitos gráficos personalizados a um elemento de layout.  
  
## <a name="example"></a>Exemplo  
 Use o <xref:System.Windows.Controls.Panel.OnRender%2A> método para adicionar efeitos gráficos a um elemento de painel renderizado. Por exemplo, você pode usar esse método para adicionar efeitos de plano de fundo ou borda personalizada. Um <xref:System.Windows.Media.DrawingContext> objeto é passado como um argumento, que fornece métodos para desenhar formas, texto, imagens ou vídeos. Como resultado, esse método é útil para a personalização de um objeto de painel.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Controls.Panel>
- [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
- [Exemplo de painel Radial personalizado](https://go.microsoft.com/fwlink/?LinkID=159982)
- [Tópicos de instruções](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
