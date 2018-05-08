---
title: Estilos e modelos ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 2182390b47508833b8535864f2d670c194d66088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="scrollviewer-styles-and-templates"></a>Estilos e modelos ScrollViewer
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ScrollViewer> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="scrollviewer-parts"></a>Partes de ScrollViewer  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ScrollViewer> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_ScrollContentPresenter|<xref:System.Windows.Controls.ScrollContentPresenter>|O espaço reservado para o conteúdo a <xref:System.Windows.Controls.ScrollViewer>.|  
|PART_HorizontalScrollBar|<xref:System.Windows.Controls.Primitives.ScrollBar>|O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo horizontalmente.|  
|PART_VerticalScrollBar|<xref:System.Windows.Controls.Primitives.ScrollBar>|O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo verticalmente.|  
  
## <a name="scrollviewer-states"></a>Estados de ScrollViewer  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ScrollViewer> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="scrollviewer-controltemplate-example"></a>Exemplo de ControlTemplate de ScrollViewer  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ScrollViewer> controle.  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 O exemplo anterior usa um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Estilos e modelos de controle](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Personalização do controle](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
