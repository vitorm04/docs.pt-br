---
title: Estilos e modelos RepeatButton
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 8585e98536fd908daa11f21da395cab44924d612
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283421"
---
# <a name="repeatbutton-styles-and-templates"></a>Estilos e modelos RepeatButton

Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.RepeatButton>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="repeatbutton-parts"></a>Partes de RepeatButton

O controle de <xref:System.Windows.Controls.Primitives.RepeatButton> não tem nenhuma parte nomeada.

## <a name="repeatbutton-states"></a>Estados de RepeatButton

A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.RepeatButton>.

|Nome do VisualState|Nome do VisualStateGroup|Descrição|
|-|-|-|
|Normal|CommonStates|O estado padrão.|
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|
|Pressionado|CommonStates|O controle é pressionado.|
|Disabled|CommonStates|O controle está desabilitado.|
|Focalizado|FocusStates|O controle tem foco.|
|Sem foco|FocusStates|O controle não tem foco.|
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|

## <a name="repeatbutton-controltemplate-example"></a>Exemplo de ControlTemplate de RepeatButton

O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.RepeatButton>.

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

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
