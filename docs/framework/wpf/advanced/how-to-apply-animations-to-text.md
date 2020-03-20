---
title: Como aplicar animações ao texto
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174622"
---
# <a name="how-to-apply-animations-to-text"></a>Como aplicar animações ao texto
As animações podem alterar a exibição e a aparência do texto em seu aplicativo. Os exemplos a seguir usam diferentes tipos de animações para afetar a exibição de texto em um <xref:System.Windows.Controls.TextBlock> controle.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation> seguir usa um para animar a largura do bloco de texto. O valor da largura muda da largura do bloco de texto para 0 em um período de 10 segundos, depois inverte os valores de largura e continua. Este tipo de animação cria um efeito de revelação.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation> seguir usa um para animar a opacidade do bloco de texto. O valor de opacidade muda de 1,0 para 0 em um período de 5 segundos, depois reverte os valores de opacidade e continua.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 O diagrama a seguir <xref:System.Windows.Controls.TextBlock> mostra o efeito `1.00` do `0.00` controle mudando sua opacidade de para durante o intervalo de 5 segundos definido pelo <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Mudança de texto opacidade de 1,00 para 0,00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 O exemplo a <xref:System.Windows.Media.Animation.ColorAnimation> seguir usa um para animar a cor do primeiro plano do bloco de texto. O valor da cor de primeiro plano muda de uma cor para uma segunda cor em um período de 5 segundos, depois reverte os valores de cor e continua.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimation> seguir usa um para girar o bloco de texto. O bloco de texto faz uma rotação completa em um período de 20 segundos e depois continua repetindo a rotação.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](../graphics-multimedia/animation-overview.md)
