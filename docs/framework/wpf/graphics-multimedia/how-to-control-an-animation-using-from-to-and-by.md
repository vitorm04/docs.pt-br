---
title: 'Como: Controlar uma animação usando de, para e por'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 35973a2a3dea233468f91c6bd24851be088b84e0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373836"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Como: Controlar uma animação usando de, para e por
Um "de/para/por" ou "animação básica" cria uma transição entre dois valores de destino (consulte [visão geral da animação](animation-overview.md) para obter uma introdução aos diferentes tipos de animações). Para definir os valores de destino de uma animação básica, use suas <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades.  A tabela a seguir resume como o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades podem ser usadas juntas ou separadamente para determinar o alvo de uma animação valores.  
  
|Propriedades especificadas|Comportamento resultante|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|A animação progride do valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor base da propriedade sendo animada ou para uma animação anterior valor de saída, dependendo de como a animação anterior é configurada.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor especificado pela soma do <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor base da propriedade animada ou uma animação anterior valor de saída para o valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor base da propriedade sendo animada ou uma animação anterior valor de saída para a soma desse valor e o valor especificado pela <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade.|  
  
> [!NOTE]
>  Não defina ambas as <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade e o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade na mesma animação.  
  
 Para usar outros métodos de interpolação ou animar entre mais de dois valores de destino, use uma animação de quadro chave. Ver [visão geral de animações de quadro-chave](key-frame-animations-overview.md) para obter mais informações.  
  
 Para obter informações sobre como aplicar várias animações a uma única propriedade, consulte [visão geral de animações de quadro-chave](key-frame-animations-overview.md).  
  
 O exemplo a seguir mostra os diferentes efeitos da configuração <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedades em animações.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da animação](animation-overview.md)
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Amostra de valores de destino de animação De, Para e Por](https://go.microsoft.com/fwlink/?LinkID=159988)
