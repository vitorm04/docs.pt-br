---
title: Estilos e modelos ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671976"
---
# <a name="scrollbar-styles-and-templates"></a>Estilos e modelos ScrollBar
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.ScrollBar> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="scrollbar-parts"></a>Partes da barra de rolagem  
 A tabela a seguir lista as partes nomeadas <xref:System.Windows.Controls.Primitives.ScrollBar> para o controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Primitives.ScrollBar>.|  
  
## <a name="scrollbar-states"></a>Estados da barra de rolagem  
 A tabela a seguir lista os Estados visuais para <xref:System.Windows.Controls.Primitives.ScrollBar> o controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|  
|Disabled|CommonStates|O controle está desabilitado.|  
|Válido|ValidationStates|O controle usa a <xref:System.Windows.Controls.Validation> classe e a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada `false`é.|  
|InvalidFocused|ValidationStates|A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada `true` é e o controle tem foco.|  
|InvalidUnfocused|ValidationStates|A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada `true` é e o controle não tem foco.|  
  
## <a name="scrollbar-controltemplate-example"></a>Exemplo de ControlTemplate de ScrollBar  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.ScrollBar> controle.  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 O exemplo anterior usa um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](control-styles-and-templates.md)
- [Personalização do controle](control-customization.md)
- [Estilo e modelagem](styling-and-templating.md)
- [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
