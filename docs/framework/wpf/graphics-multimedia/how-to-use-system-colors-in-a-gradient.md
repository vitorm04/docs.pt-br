---
title: 'Como: Usar cores do sistema em um gradiente'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229434"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Como: Usar cores do sistema em um gradiente
Para usar uma cor do sistema em um gradiente, você deve usar o  *\<SystemColor >* cor e  *\<SystemColor >* ColorKey a propriedades estáticas do <xref:System.Windows.SystemColors> classe para obter uma referência para a cor, onde  *\<SystemColor >* é o nome da cor do sistema desejado. Use o  *\<SystemColor >* ColorKey propriedades quando você deseja criar uma referência dinâmica que se atualiza automaticamente com as alterações de tema do sistema. Caso contrário, use o  *\<SystemColor >* propriedades de cor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa recursos de cor do sistema dinâmico para criar um gradiente.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 O exemplo a seguir usa recursos de cor do sistema estático para criar um gradiente.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.SystemColors>
- [Pintar uma área com um pincel de sistema](how-to-paint-an-area-with-a-system-brush.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
