---
title: Como animar a opacidade de um elemento ou pincel
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 549d3eab0d6d75403e962eeb146be8d7995cc931
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421796"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Como animar a opacidade de um elemento ou pincel
Para tornar um elemento de framework esmaecer e sair do modo de exibição, você pode animar sua <xref:System.Windows.UIElement.Opacity%2A> propriedade, ou você pode animar a <xref:System.Windows.Media.Brush.Opacity%2A> propriedade do <xref:System.Windows.Media.Brush> (ou pincéis) usadas para pintar. Animar a opacidade do elemento facilita e seus filhos esmaecem e aparecem na exibição, mas animar o pincel usado para pintar o elemento permite a ser mais seletivo sobre qual parte do elemento desaparece. Por exemplo, você poderia animar a opacidade de um pincel usado para pintar a tela de fundo de um botão. Isso faria com que a tela de fundo do botão esmaecesse e aparecesse na exibição, deixando o texto completamente opaco.  
  
> [!NOTE]
>  Animando a <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.Brush> fornece benefícios de desempenho em comparação com animar o <xref:System.Windows.UIElement.Opacity%2A> propriedade de um elemento.  
  
 No exemplo a seguir, dois botões são animados de modo que desaparecem e saem do modo de exibição. A opacidade do primeiro <xref:System.Windows.Controls.Button> é animado de `1.0` à `0.0` sobre um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos. O segundo botão também é animado, mas a opacidade do SolidColorBrush usado para pintar seu <xref:System.Windows.Controls.Control.Background%2A> é animado em vez da opacidade do botão inteiro. Quando o exemplo é executado, o primeiro botão esmaece e desaparece completamente da exibição, enquanto apenas a tela de fundo do segundo botão esmaece e desaparece da exibição. Seu texto e borda permanecem totalmente opacos.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 O código foi omitido neste exemplo. O exemplo completo também mostra como animar a opacidade de um <xref:System.Windows.Media.Color> dentro de um <xref:System.Windows.Media.LinearGradientBrush>.  Para ver o exemplo completo, consulte [Animando a opacidade de um exemplo de elemento](https://go.microsoft.com/fwlink/?LinkID=159968).
