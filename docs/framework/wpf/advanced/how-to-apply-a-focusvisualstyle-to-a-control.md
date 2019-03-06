---
title: 'Como: Aplicar um FocusVisualStyle a um controle'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: c4b379d3c57b6d0ae29952c23a35d7cc2cdf7f96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366589"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Como: Aplicar um FocusVisualStyle a um controle
Este exemplo mostra como criar um estilo visual de foco em recursos e aplicar o estilo a um controle, usando o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um estilo que cria a composição de controle adicional que só se aplica quando esse controle é voltado para o teclado no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Isso é feito definindo um estilo com uma <xref:System.Windows.Controls.ControlTemplate>, em seguida, fazendo referência a esse estilo como um recurso ao definir o <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> propriedade.  
  
 Um retângulo externo representando uma borda é colocado fora da área retangular. A menos que modificado caso contrário, o dimensionamento do estilo usa o <xref:System.Windows.FrameworkElement.ActualHeight%2A> e <xref:System.Windows.FrameworkElement.ActualWidth%2A> do controle retangular no qual o estilo visual de foco é aplicado. Este exemplo define valores negativos para o <xref:System.Windows.FrameworkElement.Margin%2A> para tornar a borda pareça estar ligeiramente fora do controle focalizado.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 Um <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> é aditivo a qualquer estilo de modelo de controle que vem a partir de um estilo explícito ou um estilo de tema; o estilo primário para um controle ainda pode ser criado usando um <xref:System.Windows.Controls.ControlTemplate> e configurando esse estilo para o <xref:System.Windows.FrameworkElement.Style%2A> propriedade.  
  
 Estilos visuais de foco devem ser usados consistentemente em um tema ou uma interface do usuário, em vez de usar um diferente para cada elemento focalizável. Para obter detalhes, consulte [Estilos para foco em controles e FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Estilo e modelagem](../controls/styling-and-templating.md)
- [Estilos para foco em controles e FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
