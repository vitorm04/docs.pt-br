---
title: Estilos e modelos PasswordBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 4ba90182468466773644c7375059f0cc01675b33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283460"
---
# <a name="passwordbox-styles-and-templates"></a>Estilos e modelos PasswordBox

Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.PasswordBox>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="passwordbox-parts"></a>Partes PasswordBox

A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.PasswordBox>.

|Parte|Tipo|Descrição|
|-|-|-|
|PART_ContentHost|<xref:System.Windows.FrameworkElement>|Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>. O texto do <xref:System.Windows.Controls.PasswordBox> é exibido neste elemento.|

## <a name="passwordbox-states"></a>Estados PasswordBox

A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.PasswordBox>.

|Nome do VisualState|Nome do VisualStateGroup|Descrição|
|-|-|-|
|Normal|CommonStates|O estado padrão.|
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|
|Disabled|CommonStates|O controle está desabilitado.|
|Focalizado|FocusStates|O controle tem foco.|
|Sem foco|FocusStates|O controle não tem foco.|
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|

## <a name="passwordbox-controltemplate-example"></a>Exemplo de ControlTemplate PasswordBox

O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.PasswordBox>.

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

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
