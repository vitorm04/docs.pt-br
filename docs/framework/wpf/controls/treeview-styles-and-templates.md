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
ms.openlocfilehash: f6dbe54324a5ad5e2f85719d819c035abfd644b1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460190"
---
# <a name="treeview-styles-and-templates"></a>Estilos e modelos TreeView
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.TreeView>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Partes de TreeView  
 O controle de <xref:System.Windows.Controls.TreeView> não tem nenhuma parte nomeada.  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.TreeView>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.TreeView>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.  
  
## <a name="treeview-states"></a>Estados de TreeView  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.TreeView>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="treeviewitem-parts"></a>Partes TreeViewItem  
 A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.TreeViewItem>.  
  
|Parte|Digite|Descrição|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Um elemento visual que contém o conteúdo do cabeçalho do controle de <xref:System.Windows.Controls.TreeView>.|  
  
## <a name="treeviewitem-states"></a>Estados TreeViewItem  
 A tabela a seguir lista os Estados visuais para <xref:System.Windows.Controls.TreeViewItem> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse está posicionado sobre o <xref:System.Windows.Controls.TreeViewItem>.|  
|Disabled|CommonStates|O <xref:System.Windows.Controls.TreeViewItem> está desabilitado.|  
|Focalizado|FocusStates|O <xref:System.Windows.Controls.TreeViewItem> tem foco.|  
|Sem foco|FocusStates|O <xref:System.Windows.Controls.TreeViewItem> não tem foco.|  
|Expandido|ExpansionStates|O controle <xref:System.Windows.Controls.TreeViewItem> é expandido.|  
|Recolhido|ExpansionStates|O controle <xref:System.Windows.Controls.TreeViewItem> está recolhido.|  
|HasItems|HasItemsStates|O <xref:System.Windows.Controls.TreeViewItem> tem itens.|  
|NoItems|HasItemsStates|O <xref:System.Windows.Controls.TreeViewItem> não tem itens.|  
|Selecionado|SelectionStates|O <xref:System.Windows.Controls.TreeViewItem> está selecionado.|  
|SelectedInactive|SelectionStates|A <xref:System.Windows.Controls.TreeViewItem> está selecionada, mas não ativa.|  
|Não selecionado|SelectionStates|O <xref:System.Windows.Controls.TreeViewItem> não está selecionado.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="treeview-controltemplate-example"></a>Exemplo de ControlTemplate de TreeView  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.TreeView> e seus tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
