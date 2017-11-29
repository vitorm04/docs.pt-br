---
title: Como converter um elemento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 222aebe0ffe3d2bb1d84002a2ad94b0b92ede15b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-translate-an-element"></a>Como converter um elemento
Este exemplo mostra como transladar (mover) um elemento usando um <xref:System.Windows.Media.TranslateTransform>.  
  
 O <xref:System.Windows.Media.TranslateTransform> classe é especialmente útil para mover elementos dentro de painéis que dão suporte ao posicionamento absoluto. Por exemplo, aplicando um <xref:System.Windows.Media.TranslateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um elemento, você pode mover um elemento dentro de um <xref:System.Windows.Controls.StackPanel> ou <xref:System.Windows.Controls.DockPanel>.  
  
 Use o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade o <xref:System.Windows.Media.TranslateTransform> para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo x. Use o <xref:System.Windows.Media.TranslateTransform.Y%2A> propriedade para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo y. Finalmente, aplique o <xref:System.Windows.Media.TranslateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.TranslateTransform> para mover o elemento 50 pixels para as direita e 50 pixels para baixo.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
