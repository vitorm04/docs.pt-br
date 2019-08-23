---
title: 'Como: Animar a opacidade de um elemento ou pincel'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950506"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Como: Animar a opacidade de um elemento ou pincel
Para fazer com que um elemento de estrutura apareça e saia da exibição, você pode <xref:System.Windows.UIElement.Opacity%2A> animar sua propriedade ou pode <xref:System.Windows.Media.Brush.Opacity%2A> animar a <xref:System.Windows.Media.Brush> propriedade dos (ou pincéis) usados para pintar. Animar a opacidade do elemento facilita e seus filhos esmaecem e aparecem na exibição, mas animar o pincel usado para pintar o elemento permite a ser mais seletivo sobre qual parte do elemento desaparece. Por exemplo, você poderia animar a opacidade de um pincel usado para pintar a tela de fundo de um botão. Isso faria com que a tela de fundo do botão esmaecesse e aparecesse na exibição, deixando o texto completamente opaco.  
  
> [!NOTE]
> Animar <xref:System.Windows.Media.Brush.Opacity%2A> o de <xref:System.Windows.Media.Brush> a fornece benefícios de desempenho com <xref:System.Windows.UIElement.Opacity%2A> a animação da propriedade de um elemento.  
  
 No exemplo a seguir, dois botões são animados de modo que desaparecem e saem do modo de exibição. <xref:System.Windows.Controls.Button> A opacidade do primeiro é animada de `1.0` para `0.0` mais <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinco segundos. O segundo botão também é animado, mas a opacidade do SolidColorBrush usado para pintar seu <xref:System.Windows.Controls.Control.Background%2A> é animada em vez da opacidade do botão inteiro. Quando o exemplo é executado, o primeiro botão esmaece e desaparece completamente da exibição, enquanto apenas a tela de fundo do segundo botão esmaece e desaparece da exibição. Seu texto e borda permanecem totalmente opacos.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 O código foi omitido neste exemplo. O exemplo completo também mostra como animar a opacidade de um <xref:System.Windows.Media.Color> dentro de <xref:System.Windows.Media.LinearGradientBrush>um.  Para ver o exemplo completo, consulte [Animando a opacidade de um exemplo de elemento](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation).
