---
title: Estilos e modelos ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: 8f29039185e7171d799543fb1d43e2fa460a97e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123065"
---
# <a name="combobox-styles-and-templates"></a>Estilos e modelos ComboBox
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ComboBox> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="combobox-parts"></a>Partes de ComboBox  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ComboBox> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|Contém o texto do <xref:System.Windows.Controls.ComboBox>.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|A lista suspensa que contém os itens na caixa de combinação.|  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ComboBox>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item em de <xref:System.Windows.Controls.ComboBox>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem no controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve dar a <xref:System.Windows.Controls.ItemsPresenter> o nome, `ItemsPresenter`.  
  
## <a name="combobox-states"></a>Estados de ComboBox  
 A tabela a seguir lista os estados para o <xref:System.Windows.Controls.ComboBox> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O controle está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está sobre o <xref:System.Windows.Controls.ComboBox> controle.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|FocusedDropDown|FocusStates|Na lista suspensa para o <xref:System.Windows.Controls.ComboBox> tem o foco.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.|  
|Editável|EditStates|A propriedade <xref:System.Windows.Controls.ComboBox.IsEditable%2A> é `true`.|  
|Não editável|EditStates|A propriedade <xref:System.Windows.Controls.ComboBox.IsEditable%2A> é `false`.|  
  
## <a name="comboboxitem-parts"></a>Partes de ComboBoxItem  
 O <xref:System.Windows.Controls.ComboBoxItem> controle não tem nenhuma parte nomeada.  
  
## <a name="comboboxitem-states"></a>Estados de ComboBoxItem  
 A tabela a seguir lista os estados para o <xref:System.Windows.Controls.ComboBoxItem> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O controle está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está sobre o <xref:System.Windows.Controls.ComboBox> controle.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|Selecionado|SelectionStates|O item está selecionado atualmente.|  
|Não selecionado|SelectionStates|O item não está selecionado.|  
|SelectedUnfocused|SelectionStates|O item está selecionado, mas não tem o foco.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.|  
  
## <a name="combobox-controltemplate-example"></a>Exemplo de ControlTemplate de ComboBox  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ComboBox> controle e tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
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
