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
ms.openlocfilehash: 579ce6fd7e4e7a1179fc686daeb95b9dea21ac90
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283729"
---
# <a name="listview-styles-and-templates"></a>Estilos e modelos ListView
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ListView>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="listview-parts"></a>Partes de ListView  
 O controle de <xref:System.Windows.Controls.ListView> não tem nenhuma parte nomeada.  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.ListView>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.ListView>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.  
  
## <a name="listview-states"></a>Estados de ListView  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ListView>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="listviewitem-parts"></a>Partes de ListViewItem  
 O controle de <xref:System.Windows.Controls.ListViewItem> não tem nenhuma parte nomeada.  
  
## <a name="listviewitem-states"></a>Estados de ListViewItem  
 A tabela a seguir lista os Estados do controle de <xref:System.Windows.Controls.ListViewItem>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|Disabled|CommonStates|O controle está desabilitado.|  
|MouseOver|CommonStates|O ponteiro do mouse está sobre o controle de <xref:System.Windows.Controls.ComboBox>.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|Selecionado|SelectionStates|O item está selecionado atualmente.|  
|Não selecionado|SelectionStates|O item não está selecionado.|  
|SelectedUnfocused|SelectionStates|O item está selecionado, mas não tem o foco.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="listview-controltemplate-examples"></a>Exemplos de ControlTemplate de ListView  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ListView> e seus tipos associados.  
  
 [!code-xaml[ControlTemplateExamples#ListView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 Os exemplos de <xref:System.Windows.Controls.ControlTemplate> usam um ou mais dos recursos a seguir.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](control-styles-and-templates.md)
- [Personalização do controle](control-customization.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
