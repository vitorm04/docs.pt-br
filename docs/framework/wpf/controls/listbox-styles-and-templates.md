---
title: Estilos e modelos ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: 552df5df6bdf8d9cdd8241c3e68cae671a24c6a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577757"
---
# <a name="listbox-styles-and-templates"></a>Estilos e modelos ListBox
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ListBox> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listbox-parts"></a>Partes de ListBox  
 O <xref:System.Windows.Controls.ListBox> controle não tem nenhuma parte nomeada.  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ListBox>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item em de <xref:System.Windows.Controls.ListBox>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem no controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve dar a <xref:System.Windows.Controls.ItemsPresenter> o nome, `ItemsPresenter`.  
  
## <a name="listbox-states"></a>Estados de ListBox  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ListBox> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle é válido.|  
|InvalidFocused|ValidationStates|O controle não é válido e tem o foco.|  
|InvalidUnfocused|ValidationStates|O controle não é válido e não tem o foco.|  
  
## <a name="listboxitem-parts"></a>Partes de ListBoxItem  
 O <xref:System.Windows.Controls.ListBoxItem> controle não tem nenhuma parte nomeada.  
  
## <a name="listboxitem-states"></a>Estados de ListBoxItem  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ListBox> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|  
|Disabled|CommonStates|O item está desabilitado.|  
|Focalizado|FocusStates|O item tem o foco.|  
|Sem foco|FocusStates|O item não tem o foco.|  
|Não selecionado|SelectionStates|O item não está selecionado.|  
|Selecionado|SelectionStates|O item é currentlyplate selecionado.|  
|SelectedUnfocused|SelectionStates|O item está selecionado, mas não tem o foco.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.|  
  
## <a name="listbox-controltemplate-example"></a>Exemplo de ControlTemplate de ListBox  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.ListBoxItem> controles.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 O exemplo anterior usa um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [Personalização do controle](../../../../docs/framework/wpf/controls/control-customization.md)
- [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
