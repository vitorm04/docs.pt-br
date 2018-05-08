---
title: Como aplicar animações ao texto
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-animations-to-text"></a>Como aplicar animações ao texto
As animações podem alterar a exibição e a aparência do texto em seu aplicativo. Os exemplos a seguir usam diferentes tipos de animação para afetar a exibição do texto em uma <xref:System.Windows.Controls.TextBlock> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a largura do bloco de texto. O valor da largura muda da largura do bloco de texto para 0 em um período de 10 segundos, depois inverte os valores de largura e continua. Este tipo de animação cria um efeito de revelação.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para animar a opacidade do bloco de texto. O valor de opacidade muda de 1,0 para 0 em um período de 5 segundos, depois reverte os valores de opacidade e continua.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 O diagrama a seguir mostra o efeito do <xref:System.Windows.Controls.TextBlock> controle alterando sua opacidade de `1.00` para `0.00` durante o intervalo de 5 segundos definido pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Texto alterando a opacidade de 1,00 para 0,00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Opacidade do texto mudando de 1,00 para 0,00  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.Animation.ColorAnimation> para animar a cor de primeiro plano do bloco de texto. O valor da cor de primeiro plano muda de uma cor para uma segunda cor em um período de 5 segundos, depois reverte os valores de cor e continua.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimation> para girar o bloco de texto. O bloco de texto faz uma rotação completa em um período de 20 segundos e depois continua repetindo a rotação.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
