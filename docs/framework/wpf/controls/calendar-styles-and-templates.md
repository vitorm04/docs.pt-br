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
ms.openlocfilehash: 64cb62a3459a3eeea6aa5e91b433a58a88ab08ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283553"
---
# <a name="calendar-styles-and-templates"></a>Estilos e modelos de calendário
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Calendar>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="calendar-parts"></a>Partes de Calendário  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Calendar>.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|O mês ou ano exibido no momento no <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|O painel que contém o <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>Estados de calendário  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Calendar>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="calendaritem-parts"></a>Partes de CalendarItem  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|A raiz do controle.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|O botão que exibe a página anterior do calendário ao ser clicado.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|O botão que exibe a próxima página do calendário ao ser clicado.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|O botão que permite alternar entre os modos de mês, ano e década.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Hospeda o conteúdo no modo de mês.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Hospeda o conteúdo no modo de ano ou década.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|A sobreposição para o estado desabilitado.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|O <xref:System.Windows.DataTemplate> que descreve a estrutura visual.|  
  
## <a name="calendaritem-states"></a>Estados de CalendarItem  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Estado normal|CommonStates|O estado padrão.|  
|Estado desabilitado|CommonStates|O estado do calendário quando a propriedade <xref:System.Windows.UIElement.IsEnabled%2A> é `false`.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="calendardaybutton-parts"></a>Partes de CalendarDayButton  
 O controle de <xref:System.Windows.Controls.Primitives.CalendarDayButton> não tem nenhuma parte nomeada.  
  
## <a name="calendardaybutton-states"></a>Estados de CalendarDayButton  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.CalendarDayButton>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Desabilitado|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarDayButton> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está posicionado sobre o <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Pressionado|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarDayButton> é pressionado.|  
|Selecionado|SelectionStates|O botão está selecionado.|  
|Não selecionado|SelectionStates|O botão não está selecionado.|  
|CalendarButtonFocused|CalendarButtonFocusStates|O botão tem o foco.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|O botão não tem o foco.|  
|Focalizado|FocusStates|O botão tem o foco.|  
|Sem foco|FocusStates|O botão não tem o foco.|  
|Ativo|ActiveStates|O botão está ativo.|  
|Inactive|ActiveStates|O botão está inativo.|  
|RegularDay|DayStates|O botão não representa <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Hoje|DayStates|O botão representa <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|O botão representa um dia que pode ser selecionado.|  
|BlackoutDay|BlackoutDayStates|O botão representa um dia que não pode ser selecionado.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="calendarbutton-parts"></a>Partes de CalendarButton  
 O controle de <xref:System.Windows.Controls.Primitives.CalendarButton> não tem nenhuma parte nomeada.  
  
## <a name="calendarbutton-states"></a>Estados de CalendarButton  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.CalendarButton>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Desabilitado|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarButton> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está posicionado sobre o <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Pressionado|CommonStates|O <xref:System.Windows.Controls.Primitives.CalendarButton> é pressionado.|  
|Selecionado|SelectionStates|O botão está selecionado.|  
|Não selecionado|SelectionStates|O botão não está selecionado.|  
|CalendarButtonFocused|CalendarButtonFocusStates|O botão tem o foco.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|O botão não tem o foco.|  
|Focalizado|FocusStates|O botão tem o foco.|  
|Sem foco|FocusStates|O botão não tem o foco.|  
|Ativo|ActiveStates|O botão está ativo.|  
|Inactive|ActiveStates|O botão está inativo.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="calendar-controltemplate-example"></a>Exemplo de ControlTemplate de calendário  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Calendar> e os tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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
