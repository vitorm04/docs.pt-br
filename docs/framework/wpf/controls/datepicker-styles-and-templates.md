---
title: Modelos e estilos de DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbe8a3935da2d9aa928467b4c64da455f3b53c5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker-styles-and-templates"></a>Modelos e estilos de DatePicker
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.DatePicker> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
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
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="datepickertextbox-parts"></a>Partes de DatePickerTextBox  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Primitives.DatePickerTextBox> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|O elemento que contém o texto inicial de <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>. O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.|  
  
## <a name="datepickertextbox-states"></a>Estados de DatePickerTextBox  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.DatePickerTextBox> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.Primitives.DatePickerTextBox> está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|O usuário não pode alterar o texto de <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|Com marca-d'água|WatermarkStates|O controle exibe seu texto inicial.  O <xref:System.Windows.Controls.Primitives.DatePickerTextBox> está no estado quando o usuário não tiver inserido o texto ou selecionou uma data.|  
|Sem marca-d'água|WatermarkStates|O usuário tiver inserido o texto para o <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ou selecionou uma data no <xref:System.Windows.Controls.DatePicker>.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="datepicker-controltemplate-example"></a>Exemplo de ControlTemplate de DatePicker  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.DatePicker> controle.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
