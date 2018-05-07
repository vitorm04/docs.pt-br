---
title: Padrões de Controle para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: d3ec88eb1054c4cc14f01320c85924c9ca346361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral apresenta padrões de controle para clientes de automação de interface do usuário. Inclui informações sobre como um cliente de automação de interface do usuário pode usar padrões de controle para acessar informações sobre o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Padrões de controle fornecem uma maneira de categorizar e expor a funcionalidade de um controle independente do tipo de controle ou a aparência do controle. Clientes de automação de interface do usuário podem examinar um <xref:System.Windows.Automation.AutomationElement> para determinar qual controle padrões são suportados em ter certeza de que o comportamento do controle.  
  
 Para obter uma lista completa dos padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Obtendo padrões de controle  
 Os clientes recuperam um padrão de controle de um <xref:System.Windows.Automation.AutomationElement> chamando <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 Os clientes podem usar o <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> um indivíduo ou método `IsPatternAvailable` propriedade (por exemplo, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) para determinar se um padrão ou o grupo de padrões é compatíveis com o <xref:System.Windows.Automation.AutomationElement>. No entanto, é mais eficiente para tentar obter o padrão de controle e de teste para um `null` referência que verifique as propriedades com suporte e recuperar o padrão de controle, pois isto resulta em menos chamadas entre processos.  
  
 O exemplo a seguir demonstra como obter um <xref:System.Windows.Automation.TextPattern> padrão de controle de um <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Recuperando propriedades em padrões de controle  
 Os clientes podem recuperar os valores de propriedade nos padrões de controle chamando <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> e convertendo o objeto retornado para um tipo apropriado. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Além de `GetPropertyValue` métodos, valores de propriedade podem ser recuperados por meio de [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] acessadores para acessar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades em um padrão.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Controles com padrões variáveis  
 Alguns tipos de controle suportam padrões diferentes dependendo da maneira na qual o controle está sendo usado ou seu estado. Exemplos de controles que podem ter padrões variáveis são modos de exibição de lista (miniaturas, lado a lado, ícones, lista, detalhes), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] gráficos (pizza, linha, barras, o valor da célula com uma fórmula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]da área (Normal, Layout da Web, estrutura de tópicos, Layout de impressão, impressão de documentos Visualização), e [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] capas.  
  
 Controles que implementam os tipos de controle personalizados podem ter qualquer conjunto de padrões de controle que são necessários para representar sua funcionalidade.  
  
## <a name="see-also"></a>Consulte também  
 [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) (Padrões de controle da Automação da Interface do Usuário)  
 [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md) (Padrão de texto da Automação da Interface do Usuário)  
 [Invocando um controle utilizando automação de interface do usuário](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Obter o estado de Alternância de uma caixa de seleção usando automação de interface do usuário](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Exemplo de texto de inserção de TextPattern](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Exemplo de seleção e pesquisa de TextPattern](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [Exemplo de Item de Menu ExpandCollapsePattern e InvokePattern](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
