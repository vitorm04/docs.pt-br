---
title: Estilos e modelos de elevador
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 780ddc07c79aab111c17f9e7e551cfde85c68f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="thumb-syles-and-templates"></a>Estilos e modelos de elevador
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.Thumb> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="thumb-parts"></a>Partes de miniatura  
 O <xref:System.Windows.Controls.Primitives.Thumb> controle não tem as partes nomeadas.  
  
## <a name="thumb-states"></a>Estados de miniatura  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.Thumb> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|-|-|-|  
|Normal|CommonStates|O estado padrão.|  
|MouseOver|CommonStates|O ponteiro do mouse é posicionado sobre o controle.|  
|Pressionado|CommonStates|O controle é pressionado.|  
|Disabled|CommonStates|O controle está desabilitado.|  
|Focalizado|FocusStates|O controle tem foco.|  
|Sem foco|FocusStates|O controle não tem foco.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="thumb-controltemplate-example"></a>Exemplo de ControlTemplate Thumb  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.Thumb> controle.  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
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
