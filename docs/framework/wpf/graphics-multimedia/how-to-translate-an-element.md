---
title: Como converter um elemento
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: ba6bda09a4ee189cdd1a32eed8f65b32d1a9abe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187315"
---
# <a name="how-to-translate-an-element"></a>Como converter um elemento
Este exemplo mostra como traduzir (mover) <xref:System.Windows.Media.TranslateTransform>um elemento usando um .  
  
 A <xref:System.Windows.Media.TranslateTransform> classe é especialmente útil para mover elementos dentro de painéis que não suportam posicionamento absoluto. Por exemplo, aplicando <xref:System.Windows.Media.TranslateTransform> um <xref:System.Windows.UIElement.RenderTransform%2A> à propriedade de um elemento, <xref:System.Windows.Controls.StackPanel> você <xref:System.Windows.Controls.DockPanel>pode mover um elemento dentro de um ou .  
  
 Use <xref:System.Windows.Media.TranslateTransform.X%2A> a propriedade <xref:System.Windows.Media.TranslateTransform> do para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo x. Use <xref:System.Windows.Media.TranslateTransform.Y%2A> a propriedade para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo y. Por fim, <xref:System.Windows.Media.TranslateTransform> aplique <xref:System.Windows.UIElement.RenderTransform%2A> a propriedade do elemento.  
  
 O exemplo a <xref:System.Windows.Media.TranslateTransform> seguir usa um para mover um elemento 50 pixels para a direita e 50 pixels para baixo.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Confira também

- [Visão geral de transformações](transforms-overview.md)
