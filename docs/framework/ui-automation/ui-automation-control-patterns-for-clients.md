---
title: Padrões de Controle para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 2f6fccf828552fbd4102c16bde7ffbaf394b69ac
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400682"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Esta visão geral apresenta padrões de controle para clientes de automação da interface do usuário. Ele inclui informações sobre como um cliente de automação de interface do usuário pode usar padrões de controle [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]para acessar informações sobre o.  
  
 Os padrões de controle fornecem uma maneira de categorizar e expor a funcionalidade de um controle independentemente do tipo de controle ou da aparência do controle. Os clientes de automação da interface <xref:System.Windows.Automation.AutomationElement> do usuário podem examinar um para determinar quais padrões de controle têm suporte e estar garantidos do comportamento do controle.  
  
 Para obter uma lista completa de padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Obtendo padrões de controle  
 Os clientes recuperam um padrão de <xref:System.Windows.Automation.AutomationElement> controle de um <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> chamando <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>o ou o.  
  
 Os clientes podem usar <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> o método ou uma `IsPatternAvailable` propriedade individual (por exemplo <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>,) para determinar se um padrão <xref:System.Windows.Automation.AutomationElement>ou grupo de padrões tem suporte no. No entanto, é mais eficiente tentar obter o padrão de controle e testar uma `null` referência do que verificar as propriedades com suporte e recuperar o padrão de controle, pois isso resulta em menos chamadas de processo cruzado.  
  
 O exemplo a seguir demonstra como obter um <xref:System.Windows.Automation.TextPattern> padrão de controle de <xref:System.Windows.Automation.AutomationElement>um.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Recuperando propriedades em padrões de controle  
 Os clientes podem recuperar os valores de propriedade nos padrões de controle <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> chamando <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ou e convertendo o objeto retornado para um tipo apropriado. Para obter mais informações [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sobre propriedades, consulte [Propriedades de automação da interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Além dos `GetPropertyValue` métodos, os valores de propriedade podem ser recuperados por meio dos acessadores Common Language Runtime (CLR) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para acessar as propriedades em um padrão.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Controles com padrões de variáveis  
 Alguns tipos de controle dão suporte a padrões diferentes, dependendo do Estado ou da maneira como o controle está sendo usado. Exemplos de controles que podem ter padrões de variáveis são exibições de lista (miniaturas, blocos, ícones, lista, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] detalhes), gráficos (pizza, linha, barra, valor de célula com [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]uma fórmula), área do documento (normal, layout da Web, estrutura de tópicos, layout de impressão, impressão Visualização) e [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] capas.  
  
 Controles que implementam tipos de controle personalizados podem ter qualquer conjunto de padrões de controle que são necessários para representar sua funcionalidade.  
  
## <a name="see-also"></a>Consulte também

- [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) (Padrões de controle da Automação da Interface do Usuário)
- [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md) (Padrão de texto da Automação da Interface do Usuário)
- [Invocando um controle utilizando automação de interface do usuário](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)
- [Obter o estado de Alternância de uma caixa de seleção usando automação de interface do usuário](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Amostra de texto de inserção de TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Exemplo de pesquisa e seleção de TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Exemplo de InvokePattern, ExpandCollapsePattern e TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
