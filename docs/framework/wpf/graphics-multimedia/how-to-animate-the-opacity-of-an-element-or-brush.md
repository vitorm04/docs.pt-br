---
title: Como animar a opacidade de um elemento ou pincel
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: a45bf0344c10e1214aa5218e25e9bd9a87d5ea60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559647"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Como animar a opacidade de um elemento ou pincel
Para um elemento de framework esmaecimento e sair do modo de exibição, é possível animar seu <xref:System.Windows.UIElement.Opacity%2A> pode animar a propriedade ou o <xref:System.Windows.Media.Brush.Opacity%2A> propriedade do <xref:System.Windows.Media.Brush> (ou pincéis) usado para pintar a ele. Animar a opacidade do elemento facilita e seus filhos esmaecem e aparecem na exibição, mas animar o pincel usado para pintar o elemento permite a ser mais seletivo sobre qual parte do elemento desaparece. Por exemplo, você poderia animar a opacidade de um pincel usado para pintar a tela de fundo de um botão. Isso faria com que a tela de fundo do botão esmaecesse e aparecesse na exibição, deixando o texto completamente opaco.  
  
> [!NOTE]
>  Animação de <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.Brush> fornece benefícios de desempenho sobre animação a <xref:System.Windows.UIElement.Opacity%2A> propriedade de um elemento.  
  
 No exemplo a seguir, dois botões são animados de modo que desaparecem e saem do modo de exibição. A opacidade do primeiro <xref:System.Windows.Controls.Button> é animado de `1.0` para `0.0` em um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos. O segundo botão também é animado, mas a opacidade de SolidColorBrush usado para pintar o <xref:System.Windows.Controls.Control.Background%2A> é animada em vez da opacidade do botão inteiro. Quando o exemplo é executado, o primeiro botão esmaece e desaparece completamente da exibição, enquanto apenas a tela de fundo do segundo botão esmaece e desaparece da exibição. Seu texto e borda permanecem totalmente opacos.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 O código foi omitido neste exemplo. O exemplo completo também mostra como animar a opacidade de um <xref:System.Windows.Media.Color> dentro de um <xref:System.Windows.Media.LinearGradientBrush>.  Para ver o exemplo completo, consulte [Animando a opacidade de um exemplo de elemento](http://go.microsoft.com/fwlink/?LinkID=159968).
