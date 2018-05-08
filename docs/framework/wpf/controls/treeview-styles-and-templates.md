---
title: Estilos e modelos TreeView
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 3a73127e409a96d5282272bd7a0e55a13a83a849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="treeview-styles-and-templates"></a>Estilos e modelos TreeView
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.TreeView> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Partes de TreeView  
 O <xref:System.Windows.Controls.TreeView> controle não tem as partes nomeadas.  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.TreeView>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item de <xref:System.Windows.Controls.TreeView>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve fornecer o <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.  
  
## <a name="treeview-states"></a>Estados de TreeView  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.TreeView> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="treeviewitem-parts"></a>Partes TreeViewItem  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.TreeViewItem> controle.  
  
|Parte|Tipo|Descrição|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Um elemento visual que contém esse cabeçalho de conteúdo do <xref:System.Windows.Controls.TreeView> controle.|  
  
## <a name="treeviewitem-states"></a>Estados TreeViewItem  
 A tabela a seguir lista os estados visuais para <xref:System.Windows.Controls.TreeViewItem> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o <xref:System.Windows.Controls.TreeViewItem>.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.TreeViewItem> está desabilitado.|  
|Focalizado|FocusStates|O <xref:System.Windows.Controls.TreeViewItem> tem foco.|  
|Sem foco|FocusStates|O <xref:System.Windows.Controls.TreeViewItem> não tem foco.|  
|Expandido|ExpansionStates|O <xref:System.Windows.Controls.TreeViewItem> controle é expandido.|  
|Recolhido|ExpansionStates|O <xref:System.Windows.Controls.TreeViewItem> está recolhido.|  
|HasItems|HasItemsStates|O <xref:System.Windows.Controls.TreeViewItem> tem itens.|  
|NoItems|HasItemsStates|O <xref:System.Windows.Controls.TreeViewItem> não tem itens.|  
|Selecionado|SelectionStates|O <xref:System.Windows.Controls.TreeViewItem> está selecionado.|  
|SelectedInactive|SelectionStates|O <xref:System.Windows.Controls.TreeViewItem> é selecionado, mas não está ativo.|  
|Não selecionado|SelectionStates|O <xref:System.Windows.Controls.TreeViewItem> não está selecionado.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="treeview-controltemplate-example"></a>Exemplo de ControlTemplate de TreeView  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.TreeView> controle e seus tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
