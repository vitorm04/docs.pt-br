---
title: Estilos e modelos DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 5c8e199dd7123e1490c8a836a62ffea158797eb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912243"
---
# <a name="datepicker-styles-and-templates"></a>Estilos e modelos DatePicker
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.DatePicker> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Partes de DatePicker  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.DatePicker> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|A raiz do controle.|  
|PART_Button|<xref:System.Windows.Controls.Button>|O botão que abre e fecha o <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Caixa de texto que permite inserir uma data.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|O pop-up para o <xref:System.Windows.Controls.DatePicker> controle.|  
  
## <a name="datepicker-states"></a>Estados de DatePicker  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.DatePicker> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.DatePicker> está desabilitado.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.|  
  
## <a name="datepickertextbox-parts"></a>Partes de DatePickerTextBox  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Primitives.DatePickerTextBox> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|O elemento que contém o texto inicial no <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>. O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.|  
  
## <a name="datepickertextbox-states"></a>Estados de DatePickerTextBox  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.DatePickerTextBox> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.Primitives.DatePickerTextBox> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está posicionado sobre o <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|O usuário não pode alterar o texto a <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|Com marca-d'água|WatermarkStates|O controle exibe seu texto inicial.  O <xref:System.Windows.Controls.Primitives.DatePickerTextBox> está no estado quando o usuário não tiver inserido texto ou selecionou uma data.|  
|Sem marca-d'água|WatermarkStates|O usuário insere o texto para o <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ou selecionou uma data no <xref:System.Windows.Controls.DatePicker>.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.|  
  
## <a name="datepicker-controltemplate-example"></a>Exemplo de ControlTemplate de DatePicker  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.DatePicker> controle.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
