---
title: Como animar em um estilo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a>Como animar em um estilo
Este exemplo mostra como animar propriedades em um estilo. Ao animar em um estilo, somente o elemento de estrutura para o qual o estilo está definido pode ser alvo diretamente. Para direcionar um objeto freezable, é preciso fazer a "marcação" de uma propriedade do elemento.  
  
 No exemplo a seguir, diversas animações são definidas em um estilo e aplicadas a um <xref:System.Windows.Controls.Button>. Quando o usuário move o mouse sobre o botão, ele passa de opaco a parcialmente translúcido e repete o processo. Quando o usuário move o mouse para fora do botão, este fica completamente opaco. Quando o botão é clicado, sua cor da tela de fundo muda de laranja para branco e volta a cor original. Porque o <xref:System.Windows.Media.SolidColorBrush> usado para pintar o botão não pode ser direcionado diretamente, ele é acessado por "dotting down" com o botão <xref:System.Windows.Controls.Control.Background%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Observe que ao animar dentro de um estilo, é possível segmentar objetos que não existem. Por exemplo, suponha que seu estilo utilize um <xref:System.Windows.Media.SolidColorBrush> definir a propriedade de plano de fundo de um botão, mas em algum momento o estilo é substituído e o plano de fundo do botão é definido com um <xref:System.Windows.Media.LinearGradientBrush>.  Tentar animar a <xref:System.Windows.Media.SolidColorBrush> não lançará uma exceção; a animação simplesmente falhará silenciosamente.  
  
 Para mais informações sobre sintaxe de segmentação de storyboard, consulte [Visão Geral de Storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Para mais informações sobre animação, consulte [Visão Geral de Animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Para mais informações sobre estilos, consulte [Estilos e Modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md).
