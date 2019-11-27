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
ms.openlocfilehash: cb7043a21020193a4b2a2569ec610f311834a698
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283750"
---
# <a name="listbox-styles-and-templates"></a>Estilos e modelos ListBox
Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ListBox>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="listbox-parts"></a>Partes da caixa de listagem  
 O controle de <xref:System.Windows.Controls.ListBox> não tem nenhuma parte nomeada.  
  
 Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.ListBox>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>. (O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.ListBox>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).  Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.  
  
## <a name="listbox-states"></a>Estados da caixa de listagem  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ListBox>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle é válido.|  
|InvalidFocused|ValidationStates|O controle não é válido e tem o foco.|  
|InvalidUnfocused|ValidationStates|O controle não é válido e não tem o foco.|  
  
## <a name="listboxitem-parts"></a>Partes de ListBoxItem  
 O controle de <xref:System.Windows.Controls.ListBoxItem> não tem nenhuma parte nomeada.  
  
## <a name="listboxitem-states"></a>Estados de ListBoxItem  
 A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ListBox>.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|  
|Desabilitado|CommonStates|O item está desabilitado.|  
|Focalizado|FocusStates|O item tem o foco.|  
|Sem foco|FocusStates|O item não tem foco.|  
|Não selecionado|SelectionStates|O item não está selecionado.|  
|Selecionado|SelectionStates|O item é currentlyplate selecionado.|  
|SelectedUnfocused|SelectionStates|O item está selecionado, mas não tem o foco.|  
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|  
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|  
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|  
  
## <a name="listbox-controltemplate-example"></a>Exemplo de ControlTemplate de ListBox  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para os controles <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
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
