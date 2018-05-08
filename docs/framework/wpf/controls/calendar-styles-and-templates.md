---
title: Estilos e modelos de calendário
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: a6f88d3371f4122a11c25a7cdf498f5822420498
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="calendar-styles-and-templates"></a>Estilos e modelos de calendário
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Calendar> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Partes de Calendário  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Calendar> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|O atualmente mês ou ano exibido no <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|O painel que contém o <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Estados de calendário  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Calendar> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="calendaritem-parts"></a>Partes de CalendarItem  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Primitives.CalendarItem> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|A raiz do controle.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|O botão que exibe a página anterior do calendário ao ser clicado.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|O botão que exibe a próxima página do calendário ao ser clicado.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|O botão que permite alternar entre os modos de mês, ano e década.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Hospeda o conteúdo no modo de mês.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Hospeda o conteúdo no modo de ano ou década.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|A sobreposição para o estado desabilitado.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|O <xref:System.Windows.DataTemplate> que descreve a estrutura de visual.|  
  
## <a name="calendaritem-states"></a>Estados de CalendarItem  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.CalendarItem> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Estado normal|CommonStates|O estado padrão.|  
|Estado desabilitado|CommonStates|O estado do calendário quando o <xref:System.Windows.UIElement.IsEnabled%2A> é de propriedade `false`.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="calendardaybutton-parts"></a>Partes de CalendarDayButton  
 O <xref:System.Windows.Controls.Primitives.CalendarDayButton> controle não tem as partes nomeadas.  
  
## <a name="calendardaybutton-states"></a>Estados de CalendarDayButton  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.CalendarDayButton> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Desabilitada|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarDayButton> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Pressionado|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarDayButton> é pressionado.|  
|Selecionado|SelectionStates|O botão está selecionado.|  
|Não selecionado|SelectionStates|O botão não está selecionado.|  
|CalendarButtonFocused|CalendarButtonFocusStates|O botão tem o foco.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|O botão não tem o foco.|  
|Focalizado|FocusStates|O botão tem o foco.|  
|Sem foco|FocusStates|O botão não tem o foco.|  
|Ativo|ActiveStates|O botão está ativo.|  
|Inativo|ActiveStates|O botão está inativo.|  
|RegularDay|DayStates|O botão não representam <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Hoje|DayStates|Representa o botão <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|O botão representa um dia que pode ser selecionado.|  
|BlackoutDay|BlackoutDayStates|O botão representa um dia que não pode ser selecionado.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="calendarbutton-parts"></a>Partes de CalendarButton  
 O <xref:System.Windows.Controls.Primitives.CalendarButton> controle não tem as partes nomeadas.  
  
## <a name="calendarbutton-states"></a>Estados de CalendarButton  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.CalendarButton> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Desabilitada|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarButton> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Pressionado|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarButton> é pressionado.|  
|Selecionado|SelectionStates|O botão está selecionado.|  
|Não selecionado|SelectionStates|O botão não está selecionado.|  
|CalendarButtonFocused|CalendarButtonFocusStates|O botão tem o foco.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|O botão não tem o foco.|  
|Focalizado|FocusStates|O botão tem o foco.|  
|Sem foco|FocusStates|O botão não tem o foco.|  
|Ativo|ActiveStates|O botão está ativo.|  
|Inativo|ActiveStates|O botão está inativo.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="calendar-controltemplate-example"></a>Exemplo de ControlTemplate de calendário  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Calendar> controle e tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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
