---
title: Como usar cores do sistema em um gradiente
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Como usar cores do sistema em um gradiente
Para usar uma cor do sistema em um gradiente, você deve usar o  *\<SystemColor >* cor e  *\<SystemColor >* ColorKey a propriedades estáticas do <xref:System.Windows.SystemColors> classe para obter um referência para a cor, onde  *\<SystemColor >* é o nome da cor do sistema desejada. Use o  *\<SystemColor >* ColorKey propriedades quando você deseja criar uma referência dinâmica que se atualiza automaticamente com as alterações de tema do sistema. Caso contrário, use o  *\<SystemColor >* propriedades de cores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa recursos de cores de sistema dinâmico para criar um gradiente.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 O exemplo a seguir usa recursos de cores do sistema estático para criar um gradiente.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.SystemColors>  
 [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Visão geral da pintura com cores sólidas e gradientes](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
