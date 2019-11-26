---
title: Estilos e modelos ProgressBar
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283449"
---
# <a name="progressbar-styles-and-templates"></a>Estilos e modelos ProgressBar
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ProgressBar>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="progressbar-parts"></a>Partes de ProgressBar  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ProgressBar>.  
  
|Parte|Digite|Descrição|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|O objeto que indica o progresso.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|O objeto que define o caminho do indicador de progresso.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Um objeto que ornamenta a barra de progresso.|  
  
## <a name="progressbar-states"></a>Estados de ProgressBar  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ProgressBar>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Barra|CommonStates|<xref:System.Windows.Controls.ProgressBar> relata o progresso com base na propriedade <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.|  
|Indeterminado|CommonStates|<xref:System.Windows.Controls.ProgressBar> relata o progresso genérico com um padrão repetido.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="progressbar-controltemplate-example"></a>Exemplo de ControlTemplate de ProgressBar  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ProgressBar>.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 O exemplo anterior usa um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](control-styles-and-templates.md)
- [Personalização do controle](control-customization.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
