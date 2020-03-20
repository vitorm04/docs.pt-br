---
title: Estilos e modelos GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187474"
---
# <a name="groupbox-styles-and-templates"></a>Estilos e modelos GroupBox
<a name="introduction"></a>Este tópico descreve os estilos e <xref:System.Windows.Controls.GroupBox> modelos para o controle. Você pode modificar <xref:System.Windows.Controls.ControlTemplate> o padrão para dar ao controle uma aparência única. Para obter mais informações, consulte [Criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>Peças de caixa de grupo  
 O <xref:System.Windows.Controls.GroupBox> controle não tem nenhuma parte nomeada.  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>Estados groupbox  
 A tabela a seguir lista <xref:System.Windows.Controls.GroupBox> os estados visuais para o controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Válido|ValidationStates|O controle <xref:System.Windows.Controls.Validation> usa a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe e `false`a propriedade anexada é .|  
|InvalidFocused|ValidationStates|A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada tem `true` o controle tem foco.|  
|InvalidUnfocused|ValidationStates|A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem foco.|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>Exemplo de modelo de controle de caixa de grupo  
 O exemplo a seguir <xref:System.Windows.Controls.ControlTemplate> mostra <xref:System.Windows.Controls.GroupBox> como definir um para o controle.  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 O <xref:System.Windows.Controls.ControlTemplate> uso de um ou mais dos seguintes recursos.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Estilos e modelos de controle](control-styles-and-templates.md)
- [Personalização do controle](control-customization.md)
- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Crie um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
