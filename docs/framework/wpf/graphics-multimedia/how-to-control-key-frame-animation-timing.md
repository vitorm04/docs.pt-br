---
title: Como controlar o tempo de animação do quadro-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: d65bf6f7643adf1d98d468853ae8017a4a6554ac
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892672"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Como controlar o tempo de animação do quadro-chave
Este exemplo mostra como controlar o intervalo de quadros chave em uma animação de quadro chave. Assim como outras animações, animações de quadro-chave têm uma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade. Além de especificar a duração de uma animação, é necessário especificar qual parte da duração é atribuída a cada um de seus quadros chave. Para alocar o tempo, você deve especificar um <xref:System.Windows.Media.Animation.KeyTime> para cada quadro chave na animação.  
  
 O <xref:System.Windows.Media.Animation.KeyTime> para cada quadro chave especifica quando um quadro chave termina (ele não especifica o período de tempo que um quadro chave). Você pode especificar uma <xref:System.Windows.Media.Animation.KeyTime> como um <xref:System.TimeSpan> valor, como uma porcentagem ou como o <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> ou <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> valor especial.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> para animar um retângulo pela tela. Tempos-chave os quadros chave são definidos com <xref:System.TimeSpan> valores.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.  
  
 ![Valores de chave são alcançados em 3, 4 e 10 segundos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 O exemplo a seguir mostra uma animação que é idêntica, exceto que os tempos da chave os quadros chave são especificados com valores de percentual.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.  
  
 ![Valores de chave são alcançados em 3, 4 e 10 segundos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 O próximo exemplo usa <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> tempo valores de chave.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.  
  
 ![Valores de chave são alcançados em 3,3, 6,6 e 9,9 segundos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 O exemplo final usa <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> tempo valores de chave.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.  
  
 ![Valores de chave são alcançados em 0, 5 e 10 segundos](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 Para simplificar, as versões de código neste exemplo usam animações locais, não storyboards, porque uma única animação está sendo aplicada a uma única propriedade, mas os exemplos podem ser modificados para utilizar storyboards. Para ver um exemplo que mostra como declarar um storyboard no código, consulte [Animar uma propriedade usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012). Para obter mais informações sobre animações de quadro chave, consulte a [Visão geral de animações de quadro chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
