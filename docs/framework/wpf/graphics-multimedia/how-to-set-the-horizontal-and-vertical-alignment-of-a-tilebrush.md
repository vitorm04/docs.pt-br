---
title: Como definir o alinhamento horizontal e vertical de um TileBrush
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], alignment of
- vertical alignment of TileBrushes [WPF]
- aligning [WPF], TileBrushes
- horizontal alignment of Tilebrushes [WPF]
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
ms.openlocfilehash: 4352067f149a1af25cd0a04a12596693188445fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-horizontal-and-vertical-alignment-of-a-tilebrush"></a>Como definir o alinhamento horizontal e vertical de um TileBrush
Este exemplo mostra como controlar o alinhamento horizontal e vertical do conteúdo em um bloco. Para controlar o alinhamento horizontal e vertical de um <xref:System.Windows.Media.TileBrush>, use seu <xref:System.Windows.Media.TileBrush.AlignmentX%2A> e <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedades.  
  
 O <xref:System.Windows.Media.TileBrush.AlignmentX%2A> e <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedades de um <xref:System.Windows.Media.TileBrush> são usadas quando uma das seguintes condições for verdadeira:  
  
-   O <xref:System.Windows.Media.TileBrush.Stretch%2A> é de propriedade <xref:System.Windows.Media.Stretch.Uniform> ou <xref:System.Windows.Media.Stretch.UniformToFill> e <xref:System.Windows.Media.TileBrush.Viewbox%2A> e <xref:System.Windows.Media.TileBrush.Viewport%2A> têm taxas de proporção diferentes.  
  
-   O <xref:System.Windows.Media.TileBrush.Stretch%2A> é de propriedade <xref:System.Windows.Media.Stretch.None> e <xref:System.Windows.Media.TileBrush.Viewbox%2A> e <xref:System.Windows.Media.TileBrush.Viewport%2A> são de tamanhos diferentes.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir alinha o conteúdo de um <xref:System.Windows.Media.DrawingBrush>, que é um tipo de <xref:System.Windows.Media.TileBrush>, para o canto superior esquerdo do seu bloco. Para alinhar o conteúdo, o exemplo define o <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propriedade o <xref:System.Windows.Media.DrawingBrush> para <xref:System.Windows.Media.AlignmentX.Left> e o <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedade <xref:System.Windows.Media.AlignmentY.Top>. Este exemplo gerencia a seguinte saída.  
  
 ![Um TileBrush com superior&#45;à esquerda](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm_TileBrushAlignmentExampleTopLeft")  
TileBrush com conteúdo alinhado ao canto superior esquerdo  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## <a name="example"></a>Exemplo  
 O próximo exemplo alinha o conteúdo de um <xref:System.Windows.Media.DrawingBrush> para o canto inferior direito do seu tile, definindo a <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propriedade <xref:System.Windows.Media.AlignmentX.Right> e o <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedade <xref:System.Windows.Media.AlignmentY.Bottom>. O exemplo produz a saída a seguir.  
  
 ![Um TileBrush com inferior&#45;direita alinhamento](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm_TileBrushAlignmentExampleBottomRight")  
TileBrush com conteúdo alinhado ao canto inferior direito  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## <a name="example"></a>Exemplo  
 O próximo exemplo alinha o conteúdo de um <xref:System.Windows.Media.DrawingBrush> para o canto superior esquerdo do seu tile, definindo o <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propriedade <xref:System.Windows.Media.AlignmentX.Left> e <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedade <xref:System.Windows.Media.AlignmentY.Top>. Ele também define o <xref:System.Windows.Media.TileBrush.Viewport%2A> e <xref:System.Windows.Media.TileBrush.TileMode%2A> do <xref:System.Windows.Media.DrawingBrush> para produzir um padrão de bloco. O exemplo produz a saída a seguir.  
  
 ![Um lado TileBrush com superior&#45;à esquerda](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm_TileBrushAlignmentExampleTopLeftTiled")  
Padrão de blocos com conteúdo alinhado à parte superior esquerda no bloco base  
  
 A ilustração destaca um bloco da base para que você possa ver como seu conteúdo está alinhado. Observe que o <xref:System.Windows.Media.TileBrush.AlignmentX%2A> configuração não tem nenhum efeito porque o conteúdo do <xref:System.Windows.Media.DrawingBrush> preenche completamente o bloco base horizontalmente.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## <a name="example"></a>Exemplo  
 Exemplo alinha o conteúdo de um <xref:System.Windows.Media.DrawingBrush> para o canto inferior direito do seu tile base definindo o <xref:System.Windows.Media.TileBrush.AlignmentX%2A> propriedade <xref:System.Windows.Media.AlignmentX.Right> e o <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedade <xref:System.Windows.Media.AlignmentY.Bottom>. O exemplo produz a saída a seguir.  
  
 ![Um lado TileBrush com inferior&#45;direita alinhamento](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm_TileBrushAlignmentExampleBottomRightTiled")  
Padrão de blocos com conteúdo alinhado à parte inferior direita no bloco base  
  
 Novamente, o <xref:System.Windows.Media.TileBrush.AlignmentX%2A> configuração não tem nenhum efeito porque o conteúdo do <xref:System.Windows.Media.DrawingBrush> preenche completamente o bloco base horizontalmente.  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xaml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 Os exemplos usam <xref:System.Windows.Media.DrawingBrush> objetos para demonstrar como o <xref:System.Windows.Media.TileBrush.AlignmentX%2A> e <xref:System.Windows.Media.TileBrush.AlignmentY%2A> propriedades são usadas. Essas propriedades se comportam de forma idêntica para todos os cursores do lado a lado: <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.ImageBrush>, e <xref:System.Windows.Media.VisualBrush>. Para obter mais informações sobre pincéis de bloco, consulte [Pintura com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.DrawingBrush>  
 <xref:System.Windows.Media.ImageBrush>  
 <xref:System.Windows.Media.VisualBrush>  
 [Pintando com imagens, desenhos e visuais](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
