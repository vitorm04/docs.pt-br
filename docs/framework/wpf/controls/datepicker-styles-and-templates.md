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
ms.openlocfilehash: 323768b6221061d46446ab18f85555f5f7415e74
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460374"
---
# <a name="datepicker-styles-and-templates"></a>Estilos e modelos DatePicker
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.DatePicker>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Partes de DatePicker  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.DatePicker>.  
  
|Parte|Digite|Descrição|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|A raiz do controle.|  
|PART_Button|<xref:System.Windows.Controls.Button>|O botão que abre e fecha o <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|Caixa de texto que permite inserir uma data.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|O popup do controle de <xref:System.Windows.Controls.DatePicker>.|  
  
## <a name="datepicker-states"></a>Estados de DatePicker  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.DatePicker>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.DatePicker> está desabilitado.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="datepickertextbox-parts"></a>Partes de DatePickerTextBox  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Parte|Digite|Descrição|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|O elemento que contém o texto inicial no <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>. O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.|  
  
## <a name="datepickertextbox-states"></a>Estados de DatePickerTextBox  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.Primitives.DatePickerTextBox> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está posicionado sobre o <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|O usuário não pode alterar o texto na <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|Com marca-d'água|WatermarkStates|O controle exibe seu texto inicial.  O <xref:System.Windows.Controls.Primitives.DatePickerTextBox> está no estado em que o usuário não inseriu o texto ou selecionou uma data.|  
|Sem marca-d'água|WatermarkStates|O usuário inseriu o texto na <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ou selecionou uma data na <xref:System.Windows.Controls.DatePicker>.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle tem foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle não tem foco.|  
  
## <a name="datepicker-controltemplate-example"></a>Exemplo de ControlTemplate de DatePicker  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.DatePicker>.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 O exemplo anterior usa um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](control-styles-and-templates.md)
- [Personalização do controle](control-customization.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md)
