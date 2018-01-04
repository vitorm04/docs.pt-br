---
title: Estilos e modelos ProgressBar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6809ce2f51af8a1baf535afa8fe80f4e5b5f53e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-styles-and-templates"></a>Estilos e modelos ProgressBar
Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ProgressBar> controle. Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva. Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="progressbar-parts"></a>Partes de barra de progresso  
 A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ProgressBar> controle.  
  
|Parte|Tipo|Descrição|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|O objeto que indica o progresso.|  
|PART_Track|<xref:System.Windows.FrameworkElement>|O objeto que define o caminho do indicador de progresso.|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|Um objeto que embellishes a barra de progresso.|  
  
## <a name="progressbar-states"></a>Estados de barra de progresso  
 A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ProgressBar> controle.  
  
|Nome do VisualState|Nome do VisualStateGroup|Descrição|  
|----------------------|---------------------------|-----------------|  
|Determinada|CommonStates|<xref:System.Windows.Controls.ProgressBar>relata o progresso com base no <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriedade.|  
|Indeterminado|CommonStates|<xref:System.Windows.Controls.ProgressBar>relata o progresso genérico com um padrão de repetição.|  
|Válido|ValidationStates|O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.|  
|InvalidFocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.|  
|InvalidUnfocused|ValidationStates|O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.|  
  
## <a name="progressbar-controltemplate-example"></a>Exemplo de ControlTemplate ProgressBar  
 O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ProgressBar> controle.  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
