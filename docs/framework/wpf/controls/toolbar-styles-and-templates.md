---
title: Estilos e modelos ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: a984311234386cb205d5db35f18a743ca535ff05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283663"
---
# <a name="toolbar-styles-and-templates"></a>Estilos e modelos ToolBar
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ToolBar>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="toolbar-parts"></a>Partes da barra de ferramentas  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ToolBar>.  
  
|Parte|Digite|Descrição|  
|-|-|-|  
|PART_ToolBarPanel|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|O objeto que contém os controles na <xref:System.Windows.Controls.ToolBar>.|  
|PART_ToolBarOverflowPanel|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|O objeto que contém os controles que estão na área de estouro do <xref:System.Windows.Controls.ToolBar>.|  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.ToolBar>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.ToolBar>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.  
  
## <a name="toolbar-states"></a>Estados da barra de ferramentas  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ToolBar>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="toolbar-controltemplate-example"></a>Exemplo de ControlTemplate da barra de ferramentas  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
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
