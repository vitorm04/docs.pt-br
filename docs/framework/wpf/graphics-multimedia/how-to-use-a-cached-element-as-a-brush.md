---
title: 'Como: Usar um elemento armazenado em cache como um pincel'
ms.date: 03/30/2017
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
ms.openlocfilehash: 78df242c7f00b69e36ea4ab6751f51509d9e2220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229362"
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Como: Usar um elemento armazenado em cache como um pincel
Use o <xref:System.Windows.Media.BitmapCacheBrush> classe reutilizar um elemento armazenado em cache com eficiência. Para armazenar em cache um elemento, criar uma nova instância dos <xref:System.Windows.Media.BitmapCache> de classe e atribuí-lo para o elemento <xref:System.Windows.UIElement.CacheMode%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como reutilizar um elemento armazenado em cache. O elemento armazenado em cache é um <xref:System.Windows.Controls.Image> controle que exibe uma imagem grande. O <xref:System.Windows.Controls.Image> controle é armazenada em cache como um bitmap usando o <xref:System.Windows.Media.BitmapCache> classe e o cache é reutilizado, atribuindo-o para um <xref:System.Windows.Media.BitmapCacheBrush>. O pincel é atribuído ao plano de fundo de vinte e cinco botões para mostrar a reutilização eficiente.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Como: Melhorar o desempenho de renderização armazenando em cache um elemento](how-to-improve-rendering-performance-by-caching-an-element.md)
