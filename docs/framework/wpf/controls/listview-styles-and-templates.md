---
title: Estilos e modelos ListView
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ListView
- states [WPF], ListView
- ControlTemplate [WPF], ListView
- styles [WPF], ListView
- ListView [WPF], styles and templates
- templates [WPF], ListView
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
ms.openlocfilehash: 74ff02ec65cbb308a702bc72274a83c52fe6a79a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="listview-styles-and-templates"></a>Estilos e modelos ListView
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ListView> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listview-parts"></a>Partes de ListView  
 O <xref:System.Windows.Controls.ListView> controle não tem as partes nomeadas.  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ListView>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item de <xref:System.Windows.Controls.ListView>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve fornecer o <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.  
  
## <a name="listview-states"></a>Estados de ListView  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ListView> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="listviewitem-parts"></a>Partes de ListViewItem  
 O <xref:System.Windows.Controls.ListViewItem> controle não tem as partes nomeadas.  
  
## <a name="listviewitem-states"></a>Estados de ListViewItem  
 A tabela a seguir lista os estados para o <xref:System.Windows.Controls.ListViewItem> controle.  
  
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
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="listview-controltemplate-examples"></a>Exemplos de ControlTemplate de ListView  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ListView> controle e seus tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 O <xref:System.Windows.Controls.ControlTemplate> exemplos usam um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Estilos e modelos de controle](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Personalização do controle](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
