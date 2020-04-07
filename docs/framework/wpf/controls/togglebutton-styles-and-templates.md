---
title: Estilos e modelos ToggleButton
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805916"
---
# <a name="togglebutton-styles-and-templates"></a>Estilos e modelos ToggleButton

Este tópico descreve os estilos e <xref:System.Windows.Controls.Primitives.ToggleButton> modelos para o controle. Você pode modificar <xref:System.Windows.Controls.ControlTemplate> o padrão para dar ao controle uma aparência única. Para obter mais informações, consulte [Criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).

## <a name="togglebutton-parts"></a>Alternar peças de botão

O <xref:System.Windows.Controls.Primitives.ToggleButton> controle não tem nenhuma parte nomeada.

## <a name="togglebutton-states"></a>Estados de ToggleButton

A tabela a seguir lista <xref:System.Windows.Controls.Primitives.ToggleButton> os estados visuais para o controle.

|Nome do VisualState|Nome do VisualStateGroup|Descrição|
|-|-|-|
|Normal|CommonStates|O estado padrão.|
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|
|Pressionado|CommonStates|O controle é pressionado.|
|Desabilitado|CommonStates|O controle está desabilitado.|
|Focalizado|FocusStates|O controle tem foco.|
|Sem foco|FocusStates|O controle não tem foco.|
|Verificado|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.|
|Desmarcado|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.|
|Indeterminado|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> é `true` e <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `null`.|
|Válido|ValidationStates|O controle <xref:System.Windows.Controls.Validation> usa a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe e `false`a propriedade anexada é .|
|InvalidFocused|ValidationStates|A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` e o controle tem foco.|
|InvalidUnfocused|ValidationStates|A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` e o controle não tem foco.|

> [!NOTE]
> Se o estado visual indeterminado não existir no seu modelo de controle, o estado visual desmarcado será usado como estado visual padrão.

## <a name="togglebutton-controltemplate-example"></a>Exemplo de modelo de controle de botão de alternar

O exemplo a seguir <xref:System.Windows.Controls.ControlTemplate> mostra <xref:System.Windows.Controls.Primitives.ToggleButton> como definir um para o controle.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

O exemplo anterior usa um ou mais dos seguintes recursos.

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](control-styles-and-templates.md)
- [Personalização do controle](control-customization.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Crie um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
