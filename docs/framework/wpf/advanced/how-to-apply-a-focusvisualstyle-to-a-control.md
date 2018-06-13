---
title: Como aplicar um FocusVisualStyle a um controle
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 34af5ca6f5ce6b3714d7d7e0d707841cdfc61349
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543726"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Como aplicar um FocusVisualStyle a um controle
Este exemplo mostra como criar um estilo visual de foco em recursos e aplicar o estilo a um controle, usando o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um estilo que cria a composição de controle adicional que só se aplica quando esse controle é voltado para o teclado no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Isso é feito definindo um estilo com um <xref:System.Windows.Controls.ControlTemplate>, em seguida, fazer referência a esse estilo como um recurso ao definir o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.  
  
 Um retângulo externo representando uma borda é colocado fora da área retangular. A menos que modificado de outra forma, o dimensionamento do estilo usa o <xref:System.Windows.FrameworkElement.ActualHeight%2A> e <xref:System.Windows.FrameworkElement.ActualWidth%2A> do controle retangular onde o estilo visual de foco é aplicado. Este exemplo define valores negativos para o <xref:System.Windows.FrameworkElement.Margin%2A> para tornar a borda pareça estar ligeiramente fora do controle focalizado.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 Um <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> é aditivo para qualquer estilo de modelo de controle que vem tanto de um estilo explícito ou um estilo de tema; o estilo primário para um controle pode ainda ser criado usando um <xref:System.Windows.Controls.ControlTemplate> e configurando esse estilo para o <xref:System.Windows.FrameworkElement.Style%2A> propriedade.  
  
 Estilos visuais de foco devem ser usados consistentemente em um tema ou uma interface do usuário, em vez de usar um diferente para cada elemento focalizável. Para obter detalhes, consulte [Estilos para foco em controles e FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Estilos para foco em controles e FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
