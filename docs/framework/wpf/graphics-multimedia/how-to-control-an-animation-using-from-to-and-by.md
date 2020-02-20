---
title: Como controlar uma animação usando de, para e por
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: b06df97dc57c58a01f30be2d70bfeebf104521ad
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451779"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Como controlar uma animação usando de, para e por
Um "de/para/por" ou "animação básica" cria uma transição entre dois valores de destino (consulte [visão geral da animação](animation-overview.md) para obter uma introdução a diferentes tipos de animações). Para definir os valores de destino de uma animação básica, use suas propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  A tabela a seguir resume como as propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> podem ser usadas juntas ou separadamente para determinar os valores de destino de uma animação.  
  
|Propriedades especificadas|Comportamento resultante|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|A animação progride do valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> para o valor base da propriedade sendo animada ou para um valor de saída da animação anterior, dependendo de como a animação anterior é configurada.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> para o valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> para o valor especificado pela soma das propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor base da propriedade animada ou do valor de saída de uma animação anterior para o valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor base da propriedade sendo animada ou do valor de saída de uma animação anterior à soma desse valor e ao valor especificado pela propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
  
> [!NOTE]
> Não defina a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> e a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> na mesma animação.  
  
 Para usar outros métodos de interpolação ou animar entre mais de dois valores de destino, use uma animação de quadro chave. Consulte [visão geral das animações de quadro chave](key-frame-animations-overview.md) para obter mais informações.  
  
 Para obter informações sobre como aplicar várias animações a uma única propriedade, consulte [visão geral das animações de quadro chave](key-frame-animations-overview.md).  
  
 O exemplo a seguir mostra os diferentes efeitos da definição das propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>e <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> em animações.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Amostra de valores de destino de animação De, Para e Por](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
