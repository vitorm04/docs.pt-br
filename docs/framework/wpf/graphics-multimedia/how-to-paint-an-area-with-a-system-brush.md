---
title: 'Como: Pintar uma área com um pincel de sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: 26511c577bf06b016dfc69cedc7fce2bafb35f32
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645375"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Como: Pintar uma área com um pincel de sistema
O <xref:System.Windows.SystemColors> classe fornece acesso a pincéis do sistema e cores, como <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, e <xref:System.Windows.SystemColors.DesktopBrush%2A>. Um pincel de sistema é um <xref:System.Windows.Media.SolidColorBrush> objeto que pinta uma área com a cor especificada do sistema. Um pincel do sistema sempre produz um preenchimento sólido; ele não pode ser usado para criar um gradiente.  
  
 Você pode usar pincéis do sistema como um recurso dinâmico ou estático. Use um recurso dinâmico se desejar que o pincel seja atualizado automaticamente se o usuário alterar o pincel do sistema enquanto o aplicativo está em execução; caso contrário, use um recurso estático. A classe SystemColors contém uma variedade de propriedades estáticas que seguem uma convenção de nomenclatura estrita:  
  
- *\<SystemColor>* Pincel  
  
     Obtém uma referência estática a uma <xref:System.Windows.Media.SolidColorBrush> da cor especificada do sistema.  
  
- *\<SystemColor>* BrushKey  
  
     Obtém uma referência dinâmica a um <xref:System.Windows.Media.SolidColorBrush> da cor especificada do sistema.  
  
- *\<SystemColor>* Cor  
  
     Obtém uma referência estática a uma <xref:System.Windows.Media.Color> estrutura de cor especificada do sistema.  
  
- *\<SystemColor>* ColorKey  
  
     Obtém uma referência dinâmica para o <xref:System.Windows.Media.Color> estrutura de cor especificada do sistema.  
  
 Uma cor do sistema é um <xref:System.Windows.Media.Color> estrutura que pode ser usada para configurar um pincel. Por exemplo, você pode criar um gradiente usando cores do sistema definindo a <xref:System.Windows.Media.GradientStop.Color%2A> propriedades de um <xref:System.Windows.Media.LinearGradientBrush> paradas de gradiente do objeto com as cores do sistema. Por exemplo, consulte [usar cores do sistema em um gradiente](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma referência de pincel de sistema dinâmico para definir a tela de fundo de um botão.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 O exemplo a seguir usa uma referência de pincel de sistema estático para definir a tela de fundo de um botão.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Para obter um exemplo que mostra como usar uma cor do sistema em um gradiente, consulte [usar cores do sistema em um gradiente](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Consulte também

- [Usar cores do sistema em um gradiente](how-to-use-system-colors-in-a-gradient.md)
- [Visão geral da pintura com cores sólidas e gradientes](painting-with-solid-colors-and-gradients-overview.md)
