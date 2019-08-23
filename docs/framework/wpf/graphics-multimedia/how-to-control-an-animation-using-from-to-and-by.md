---
title: 'Como: Controlar uma animação usando From, To e By'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 812217a2905671567271687b974a435dd85cea47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930081"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Como: Controlar uma animação usando From, To e By
Um "de/para/por" ou "animação básica" cria uma transição entre dois valores de destino (consulte [visão geral da animação](animation-overview.md) para obter uma introdução a diferentes tipos de animações). Para definir os valores de destino de uma animação básica, use <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>suas <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>Propriedades, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> e.  A tabela a seguir resume como as <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>propriedades <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> podem ser usadas juntas ou separadamente para determinar os valores de destino de uma animação.  
  
|Propriedades especificadas|Comportamento resultante|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|A animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor base da propriedade que está sendo animada ou para o valor de saída de uma animação anterior, dependendo de como a animação anterior é configurada.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor especificado <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> pela propriedade.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor especificado pela soma <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> das propriedades e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor base da propriedade animada ou do valor de saída de uma animação anterior para o valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor base da propriedade sendo animada ou do valor de saída de uma animação anterior para a soma desse valor e o valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade.|  
  
> [!NOTE]
> Não defina a <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Propriedade e a <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Propriedade na mesma animação.  
  
 Para usar outros métodos de interpolação ou animar entre mais de dois valores de destino, use uma animação de quadro chave. Consulte [visão geral das animações de quadro chave](key-frame-animations-overview.md) para obter mais informações.  
  
 Para obter informações sobre como aplicar várias animações a uma única propriedade, consulte [visão geral das animações de quadro chave](key-frame-animations-overview.md).  
  
 O exemplo a seguir mostra os diferentes efeitos de <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>configuração <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> Propriedades em animações.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da animação](animation-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Amostra de valores de destino de animação De, Para e Por](https://go.microsoft.com/fwlink/?LinkID=159988)
