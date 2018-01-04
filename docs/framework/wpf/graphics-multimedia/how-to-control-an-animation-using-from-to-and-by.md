---
title: "Como controlar uma animação usando de, para e por"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17f87c8bcf09022aa389df779e29f5e5affabc20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Como controlar uma animação usando de, para e por
Um "de/para/por" ou "animação básica" cria uma transição entre dois valores de destino (consulte [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) para obter uma introdução aos diferentes tipos de animações). Para definir os valores de destino de uma animação básica, use seu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades.  A tabela a seguir resume como o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades podem ser usadas em conjunto ou separadamente para determinar o alvo de uma animação valores.  
  
|Propriedades especificadas|Comportamento resultante|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|A animação progride do valor especificado o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor base da propriedade que está sendo animada ou para uma animação anterior valor de saída, dependendo de como a animação anterior é configurada.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> o valor especificado pela propriedade de <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor especificado o <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedade para o valor especificado pela soma do <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> e <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedades.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|A animação progride do valor base da propriedade animada ou uma animação anterior valor de saída para o valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|A animação progride do valor base da propriedade que está sendo animada ou uma animação anterior valor de saída para a soma do valor e o valor especificado pelo <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade.|  
  
> [!NOTE]
>  Não defina o <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriedade e o <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriedade na mesma animação.  
  
 Para usar outros métodos de interpolação ou animar entre mais de dois valores de destino, use uma animação de quadro chave. Consulte [visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md) para obter mais informações.  
  
 Para obter informações sobre como aplicar várias animações a uma única propriedade, consulte [visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 O exemplo a seguir mostra os efeitos diferentes de configuração <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, e <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriedades em animações.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Amostra de valores de destino de animação De, Para e Por](http://go.microsoft.com/fwlink/?LinkID=159988)
