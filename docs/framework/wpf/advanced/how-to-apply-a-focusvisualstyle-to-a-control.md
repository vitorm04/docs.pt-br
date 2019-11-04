---
title: Como aplicar um FocusVisualStyle a um controle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459811"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Como aplicar um FocusVisualStyle a um controle
Este exemplo mostra como criar um estilo visual de foco em recursos e aplicar o estilo a um controle, usando a propriedade <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um estilo que cria a composição de controle adicional que só se aplica quando esse controle é voltado para o teclado no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Isso é feito definindo um estilo com um <xref:System.Windows.Controls.ControlTemplate>e, em seguida, referenciando esse estilo como um recurso ao definir a propriedade <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Um retângulo externo representando uma borda é colocado fora da área retangular. A menos que seja modificado de outra forma, o dimensionamento do estilo usa o <xref:System.Windows.FrameworkElement.ActualHeight%2A> e <xref:System.Windows.FrameworkElement.ActualWidth%2A> do controle retangular em que o estilo visual de foco é aplicado. Este exemplo define valores negativos para o <xref:System.Windows.FrameworkElement.Margin%2A> para que a borda pareça um pouco fora do controle focalizado.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 Um <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> é aditivo para qualquer estilo de modelo de controle que venha de um estilo explícito ou um estilo de tema; o estilo principal para um controle ainda pode ser criado usando um <xref:System.Windows.Controls.ControlTemplate> e definindo esse estilo para a propriedade <xref:System.Windows.FrameworkElement.Style%2A>.  
  
 Estilos visuais de foco devem ser usados consistentemente em um tema ou uma interface do usuário, em vez de usar um diferente para cada elemento focalizável. Para obter detalhes, consulte [Estilos para foco em controles e FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Estilos para foco em controles e FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
