---
title: 'Como: Usar cores do sistema em um gradiente'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 3148a5901ccf64194717e26664ab8b9cbd57db2a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365952"
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
