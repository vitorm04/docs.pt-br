---
title: Como animar em um estilo
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: e0741a869ab81875aaa25340de851ef939e11a6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558807"
---
# <a name="how-to-animate-in-a-style"></a>Como animar em um estilo
Este exemplo mostra como animar propriedades em um estilo. Ao animar em um estilo, somente o elemento de estrutura para o qual o estilo está definido pode ser alvo diretamente. Para direcionar um objeto freezable, é preciso fazer a "marcação" de uma propriedade do elemento.  
  
 No exemplo a seguir, diversas animações são definidas em um estilo e aplicadas a um <xref:System.Windows.Controls.Button>. Quando o usuário move o mouse sobre o botão, ele passa de opaco a parcialmente translúcido e repete o processo. Quando o usuário move o mouse para fora do botão, este fica completamente opaco. Quando o botão é clicado, sua cor da tela de fundo muda de laranja para branco e volta a cor original. Porque o <xref:System.Windows.Media.SolidColorBrush> usado para pintar o botão não pode ser direcionado diretamente, ele é acessado por "dotting down" com o botão <xref:System.Windows.Controls.Control.Background%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Observe que ao animar dentro de um estilo, é possível segmentar objetos que não existem. Por exemplo, suponha que seu estilo utilize um <xref:System.Windows.Media.SolidColorBrush> definir a propriedade de plano de fundo de um botão, mas em algum momento o estilo é substituído e o plano de fundo do botão é definido com um <xref:System.Windows.Media.LinearGradientBrush>.  Tentar animar a <xref:System.Windows.Media.SolidColorBrush> não lançará uma exceção; a animação simplesmente falhará silenciosamente.  
  
 Para mais informações sobre sintaxe de segmentação de storyboard, consulte [Visão Geral de Storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Para mais informações sobre animação, consulte [Visão Geral de Animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Para mais informações sobre estilos, consulte [Estilos e Modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).
