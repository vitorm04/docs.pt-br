---
title: 'Como: Definir o tamanho de bloco um TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 80b5dfc668464df829db593668bea8a9a4ec09e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839664"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Como: Definir o tamanho de bloco um TileBrush

Este exemplo mostra como definir o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>. Por padrão, um <xref:System.Windows.Media.TileBrush> produz um único bloco que preenche completamente a área que você está pintando. Você pode substituir esse comportamento, definindo a <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades.

O <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especifica o tamanho de bloco para um <xref:System.Windows.Media.TileBrush>. Por padrão, o valor da <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade é relativo ao tamanho da área que está sendo pintada. Para tornar o <xref:System.Windows.Media.TileBrush.Viewport%2A> propriedade especificar um tamanho de bloco absoluto, defina a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedade para <xref:System.Windows.Media.BrushMappingMode.Absolute>.

## <a name="example"></a>Exemplo

O exemplo a seguir usa uma <xref:System.Windows.Media.ImageBrush>, um tipo de <xref:System.Windows.Media.TileBrush>, para desenhar um retângulo com blocos. O exemplo define cada bloco para 50% por 50 por cento da área de saída (o retângulo). Como resultado, o retângulo é pintado com quatro projeções da imagem.

A ilustração a seguir mostra a saída que esse exemplo produz:

![Um retângulo com quatro números errados demonstrando lado a lado com um pincel de imagem.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

O exemplo a seguir cria uma <xref:System.Windows.Media.ImageBrush>, define sua <xref:System.Windows.Media.TileBrush.Viewport%2A> para `0,0,25,25` e sua <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> para <xref:System.Windows.Media.BrushMappingMode.Absolute>e o utiliza para pintar outro retângulo. Como resultado, o pincel produz blocos com uma largura de 25 pixels e uma altura de 25 pixels.

A ilustração a seguir mostra a saída que esse exemplo produz:

![Um retângulo com números errados de oito quarenta e demonstrar um TileBrush lado a lado com um visor.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

Os exemplos anteriores fazem parte de um exemplo maior. Para o exemplo completo, consulte [exemplo de ImageBrush](https://go.microsoft.com/fwlink/?LinkID=160005).

Embora este exemplo usa o <xref:System.Windows.Media.ImageBrush> classe, o <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> propriedades se comportam de forma idêntica para os outros <xref:System.Windows.Media.TileBrush> objetos, ou seja, para <xref:System.Windows.Media.DrawingBrush> e <xref:System.Windows.Media.VisualBrush>. Para obter mais informações sobre <xref:System.Windows.Media.ImageBrush> e o outro <xref:System.Windows.Media.TileBrush> objetos, consulte [pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.TileBrush>
- [Pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md)
- [Criar padrões de bloco diferentes com um TileBrush](how-to-create-different-tile-patterns-with-a-tilebrush.md)
