---
title: Como usar cores do sistema em um gradiente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Como usar cores do sistema em um gradiente
Para usar uma cor do sistema em um gradiente, você deve usar o  *\<SystemColor >*cor e  *\<SystemColor >*ColorKey a propriedades estáticas do <xref:System.Windows.SystemColors> classe para obter um referência para a cor, onde  *\<SystemColor >* é o nome da cor do sistema desejada. Use o  *\<SystemColor >*ColorKey propriedades quando você deseja criar uma referência dinâmica que se atualiza automaticamente com as alterações de tema do sistema. Caso contrário, use o  *\<SystemColor >*propriedades de cores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa recursos de cores de sistema dinâmico para criar um gradiente.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 O exemplo a seguir usa recursos de cores do sistema estático para criar um gradiente.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.SystemColors>  
 [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
