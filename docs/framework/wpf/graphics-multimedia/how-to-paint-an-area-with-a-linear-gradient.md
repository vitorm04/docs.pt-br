---
title: 'Como: Pintar uma área com um gradiente linear'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367239"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Como: Pintar uma área com um gradiente linear
Este exemplo mostra como usar o <xref:System.Windows.Media.LinearGradientBrush> classe pintar uma área com um gradiente linear. No exemplo a seguir, o <xref:System.Windows.Shapes.Shape.Fill%2A> de um <xref:System.Windows.Shapes.Rectangle> é pintado com um gradiente linear diagonal que faz a transição de amarelo para vermelho para azul para verde limão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 A ilustração a seguir mostra o gradiente criado pelo exemplo anterior.  
  
 ![Gradiente linear diagonal](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Para criar um gradiente linear horizontal, altere o <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> da <xref:System.Windows.Media.LinearGradientBrush> para (0, 0.5) e (1, 0,5). No exemplo a seguir, um <xref:System.Windows.Shapes.Rectangle> é pintado com um gradiente linear horizontal.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 A ilustração a seguir mostra o gradiente criado pelo exemplo anterior.  
  
 ![Um gradiente linear horizontal](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Para criar um gradiente linear vertical, altere o <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> e <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> da <xref:System.Windows.Media.LinearGradientBrush> para (0.5,0) e (0.5,1). No exemplo a seguir, um <xref:System.Windows.Shapes.Rectangle> é pintado com um gradiente linear vertical.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 A ilustração a seguir mostra o gradiente criado pelo exemplo anterior.  
  
 ![Gradiente linear vertical](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  Os exemplos neste tópico usam o sistema de coordenadas padrão para definir pontos de início e pontos de extremidade. O sistema de coordenadas padrão é relativo a uma caixa delimitadora: 0 indica 0% da caixa delimitadora e 1 indica 100 por cento da caixa delimitadora. Você pode alterar esse sistema de coordenadas definindo a <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriedade para o valor <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Um sistema de coordenadas absoluto não é relativo a uma caixa delimitadora. Os valores são interpretados diretamente no espaço local.  
  
 Para obter exemplos adicionais, veja [Exemplo de pincéis](https://go.microsoft.com/fwlink/?LinkID=159973). Para obter mais informações sobre gradientes e outros tipos de pincéis, veja [Visão geral de pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md).
