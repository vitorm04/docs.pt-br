---
title: 'Como: Especificar a origem de uma transformação usando valores relativos'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 48b3b0df8dab8516873495a996074eae57ffe00f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082952"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>Como: Especificar a origem de uma transformação usando valores relativos
Este exemplo mostra como usar valores relativos para especificar a origem de um <xref:System.Windows.UIElement.RenderTransform%2A> que é aplicado a um <xref:System.Windows.FrameworkElement>.  
  
 Quando você girar, dimensionar ou distorcer um <xref:System.Windows.FrameworkElement> usando o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade, a configuração padrão se aplica a transformação ao canto superior esquerdo do elemento. Se você deseja girar, dimensionar ou distorcer no centro do elemento, compense definindo o centro da transformação para o centro do elemento. No entanto, essa solução requer que você saiba o tamanho do elemento. Uma maneira mais fácil de aplicar uma transformação para o Centro de um elemento é definir sua <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade para (0,5, 0,5), em vez de definir um valor central na própria transformação.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.RotateTransform> girar um <xref:System.Windows.Controls.Button> 45 graus no sentido horário. Porque o exemplo não especifica um centro, o botão gira sobre o ponto (0, 0), que é seu canto superior esquerdo. O <xref:System.Windows.Media.RotateTransform> é aplicada para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade.  
  
 A ilustração a seguir mostra o resultado da transformação do seguinte exemplo.  
  
 ![Um botão transformado com RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
Uma rotação de 45 graus no sentido horário usando a propriedade RenderTransform  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 O exemplo a seguir também usa um <xref:System.Windows.Media.RotateTransform> girar uma <xref:System.Windows.Controls.Button> 45 graus no sentido horário; no entanto, este exemplo define o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> do botão para (0,5, 0,5). Como resultado, a rotação é aplicada ao centro do botão em vez de seu canto superior esquerdo.  
  
 A ilustração a seguir mostra o resultado da transformação do seguinte exemplo.  
  
 ![Um botão transformado sobre seu centro](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
Uma rotação de 45 graus usando a propriedade RenderTransform com um RenderTransformOrigin de (0,5, 0,5)  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 Para obter mais informações sobre como transformar <xref:System.Windows.FrameworkElement> objetos, consulte a [visão geral de transformações](transforms-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Transform>
- [Visão geral de transformações](transforms-overview.md)
- [Tópicos de instruções](transformations-how-to-topics.md)
