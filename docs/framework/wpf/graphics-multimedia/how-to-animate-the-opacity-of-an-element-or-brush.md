---
title: 'Como: Animar a opacidade de um elemento ou pincel'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: f07138a0b68fff050133d477074571c60cd8651e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363365"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Como: Animar a opacidade de um elemento ou pincel
Para tornar um elemento de framework esmaecer e sair do modo de exibição, você pode animar sua <xref:System.Windows.UIElement.Opacity%2A> propriedade, ou você pode animar a <xref:System.Windows.Media.Brush.Opacity%2A> propriedade do <xref:System.Windows.Media.Brush> (ou pincéis) usadas para pintar. Animar a opacidade do elemento facilita e seus filhos esmaecem e aparecem na exibição, mas animar o pincel usado para pintar o elemento permite a ser mais seletivo sobre qual parte do elemento desaparece. Por exemplo, você poderia animar a opacidade de um pincel usado para pintar a tela de fundo de um botão. Isso faria com que a tela de fundo do botão esmaecesse e aparecesse na exibição, deixando o texto completamente opaco.  
  
> [!NOTE]
>  Animando a <xref:System.Windows.Media.Brush.Opacity%2A> de um <xref:System.Windows.Media.Brush> fornece benefícios de desempenho em comparação com animar o <xref:System.Windows.UIElement.Opacity%2A> propriedade de um elemento.  
  
 No exemplo a seguir, dois botões são animados de modo que desaparecem e saem do modo de exibição. A opacidade do primeiro <xref:System.Windows.Controls.Button> é animado de `1.0` à `0.0` sobre um <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos. O segundo botão também é animado, mas a opacidade do SolidColorBrush usado para pintar seu <xref:System.Windows.Controls.Control.Background%2A> é animado em vez da opacidade do botão inteiro. Quando o exemplo é executado, o primeiro botão esmaece e desaparece completamente da exibição, enquanto apenas a tela de fundo do segundo botão esmaece e desaparece da exibição. Seu texto e borda permanecem totalmente opacos.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 O código foi omitido neste exemplo. O exemplo completo também mostra como animar a opacidade de um <xref:System.Windows.Media.Color> dentro de um <xref:System.Windows.Media.LinearGradientBrush>.  Para ver o exemplo completo, consulte [Animando a opacidade de um exemplo de elemento](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation).
