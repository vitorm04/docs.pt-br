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
ms.openlocfilehash: 981a487b9935a86595a9caca03b4371326924642
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458228"
---
# <a name="togglebutton-styles-and-templates"></a>Estilos e modelos ToggleButton

Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.ToggleButton>. Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).

## <a name="togglebutton-parts"></a>Partes de ToggleButton

O controle de <xref:System.Windows.Controls.Primitives.ToggleButton> não tem nenhuma parte nomeada.

## <a name="togglebutton-states"></a>Estados de ToggleButton

A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.ToggleButton>.

|Nome do VisualState|Nome do VisualStateGroup|Descrição|
|-|-|-|
|Normal|CommonStates|O estado padrão.|
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|
|Pressionado|CommonStates|O controle é pressionado.|
|Disabled|CommonStates|O controle está desabilitado.|
|Focalizado|FocusStates|O controle tem foco.|
|Sem foco|FocusStates|O controle não tem foco.|
|Selecionado|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.|
|Não Selecionado|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.|
|Indeterminado|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> é `true` e <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `null`.|
|Válido|ValidationStates|O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.|
|InvalidFocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.|
|InvalidUnfocused|ValidationStates|A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.|

> [!NOTE]
> Se o estado visual indeterminado não existir no seu modelo de controle, o estado visual desmarcado será usado como o estado visual padrão.

## <a name="togglebutton-controltemplate-example"></a>Exemplo de ControlTemplate de ToggleButton

O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.ToggleButton>.

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

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
