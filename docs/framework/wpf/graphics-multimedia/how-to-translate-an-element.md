---
title: 'Como: Converter um elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 9c1b873a89820e85efb99789f483c4832fb23cf7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231182"
---
# <a name="how-to-translate-an-element"></a>Como: Converter um elemento
Este exemplo mostra como mover (translação) um elemento usando um <xref:System.Windows.Media.TranslateTransform>.  
  
 O <xref:System.Windows.Media.TranslateTransform> classe é especialmente útil para mover elementos dentro de painéis que não dão suporte ao posicionamento absoluto. Por exemplo, aplicando uma <xref:System.Windows.Media.TranslateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um elemento, você pode mover um elemento dentro de uma <xref:System.Windows.Controls.StackPanel> ou <xref:System.Windows.Controls.DockPanel>.  
  
 Use o <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade do <xref:System.Windows.Media.TranslateTransform> para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo x. Use o <xref:System.Windows.Media.TranslateTransform.Y%2A> propriedade para especificar a quantidade, em pixels, para mover o elemento ao longo do eixo y. Por fim, aplique a <xref:System.Windows.Media.TranslateTransform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade do elemento.  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.TranslateTransform> para mover o elemento 50 pixels para as direita e 50 pixels para baixo.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Para obter o exemplo completo, consulte [Amostras de Transformação 2D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de transformações](transforms-overview.md)
