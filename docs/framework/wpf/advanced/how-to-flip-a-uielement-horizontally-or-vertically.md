---
title: 'Como: Inverter um UIElement horizontal ou verticalmente'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 3dd9a8e2a94acf62973701094e8966c8ebff15c9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356345"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>Como: Inverter um UIElement horizontal ou verticalmente
Este exemplo mostra como usar um <xref:System.Windows.Media.ScaleTransform> inverter um <xref:System.Windows.UIElement> horizontal ou verticalmente. Neste exemplo, uma <xref:System.Windows.Controls.Button> controle (um tipo de <xref:System.Windows.UIElement>) é invertido aplicando um <xref:System.Windows.Media.ScaleTransform> ao seu <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 A ilustração a seguir mostra o botão a ser invertido.  
  
 ![Um botão sem transformação](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
O UIElement a ser invertido  
  
 O exemplo a seguir mostra o código que cria o botão.  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>Exemplo  
 Para inverter o botão horizontalmente, crie uma <xref:System.Windows.Media.ScaleTransform> e defina seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedade como -1. Aplicar a <xref:System.Windows.Media.ScaleTransform> do botão <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![Um botão invertido horizontalmente sobre &#40;0,0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
O botão após a aplicação de ScaleTransform  
  
## <a name="example"></a>Exemplo  
 Como você pode ver na ilustração anterior, o botão foi invertido, mas também foi movido. Isso ocorre porque o botão foi invertido no seu canto superior esquerdo. Para inverter o botão no lugar, você deseja aplicar o <xref:System.Windows.Media.ScaleTransform> ao seu centro, não a seu canto. Uma maneira fácil de aplicar a <xref:System.Windows.Media.ScaleTransform> aos botões center é definir o botão <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade como 0,5, 0,5.  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![Um botão invertido horizontalmente sobre seu centro](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
O botão com um RenderTransformOrigin de 0,5, 0,5  
  
## <a name="example"></a>Exemplo  
 Para Inverter verticalmente o botão, defina a <xref:System.Windows.Media.ScaleTransform> do objeto <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriedade em vez de seu <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> propriedade.  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![Um botão invertido verticalmente sobre seu centro](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
O botão invertido verticalmente  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de transformações](../graphics-multimedia/transforms-overview.md)
