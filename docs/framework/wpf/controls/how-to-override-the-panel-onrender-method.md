---
title: "Como substituir o método OnRender do painel"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 774c612b09d5cb0ffdf36024a7e6a543f407cf67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-the-panel-onrender-method"></a>Como substituir o método OnRender do painel
Este exemplo mostra como substituir o <xref:System.Windows.Controls.Panel.OnRender%2A> método <xref:System.Windows.Controls.Panel> para adicionar efeitos gráficos personalizados a um elemento de layout.  
  
## <a name="example"></a>Exemplo  
 Use o <xref:System.Windows.Controls.Panel.OnRender%2A> método para adicionar efeitos gráficos a um elemento de painel renderizado. Por exemplo, você pode usar esse método para adicionar efeitos de plano de fundo ou borda personalizada. Um <xref:System.Windows.Media.DrawingContext> objeto é passado como um argumento, que fornece métodos para desenhar formas, texto, imagens ou vídeos. Como resultado, esse método é útil para a personalização de um objeto de painel.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Panel>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Exemplo de painel Radial personalizado](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
