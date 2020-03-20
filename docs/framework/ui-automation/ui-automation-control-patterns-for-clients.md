---
title: Padrões de Controle para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 1ee0df5b133f08ec3cf6ba617c80c480e207ddf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179953"
---
# <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral introduz padrões de controle para clientes de Automação de Interface do Usuário. Ele inclui informações sobre como um cliente de Automação de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]UI pode usar padrões de controle para acessar informações sobre o .  
  
 Os padrões de controle permitem categorizar e expor a funcionalidade de um controle independente do tipo ou da aparência do controle. Os clientes de <xref:System.Windows.Automation.AutomationElement> Automação de Interface do Usuário podem examinar um para determinar quais padrões de controle são suportados e ter certeza do comportamento do controle.  
  
 Para obter uma lista completa de padrões de controle, consulte Visão geral dos padrões de controle de automação de [ui](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a>Obtendo padrões de controle  
 Os clientes recuperam <xref:System.Windows.Automation.AutomationElement> um <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> padrão <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>de controle de um chamando ou .  
  
 Os clientes <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> podem usar `IsPatternAvailable` o método <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>ou uma propriedade individual (por exemplo) para <xref:System.Windows.Automation.AutomationElement>determinar se um padrão ou grupo de padrões é suportado no . No entanto, é mais eficiente tentar obter o `null` padrão de controle e testar uma referência do que verificar as propriedades suportadas e recuperar o padrão de controle, uma vez que resulta em menos chamadas de processo cruzado.  
  
 O exemplo a seguir <xref:System.Windows.Automation.TextPattern> demonstra como <xref:System.Windows.Automation.AutomationElement>obter um padrão de controle a partir de um .  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a>Recuperando propriedades em padrões de controle  
 Os clientes podem recuperar os valores <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> da propriedade nos padrões de controle ligando para um ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> para o outro e lançando o objeto devolvido a um tipo apropriado. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
 Além dos `GetPropertyValue` métodos, os valores de propriedade podem ser recuperados através dos acessórios [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de tempo de execução de linguagem comum (CLR) para acessar as propriedades em um padrão.  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a>Controles com padrões variáveis  
 Alguns tipos de controle suportam padrões diferentes dependendo do seu estado ou da maneira como o controle está sendo usado. Exemplos de controles que podem ter padrões variáveis são visualizações de listas (miniaturas, telhas, ícones, lista, detalhes), Gráficos microsoft excel (Pie, Linha, Barra, Valor celular com uma fórmula), área de documentos do Microsoft Word (Normal, Layout da Web, Contorno, Layout de Impressão, Imprimir Visualização) e skins do Microsoft Windows Media Player.  
  
 Controles que implementam tipos de controle personalizados podem ter qualquer conjunto de padrões de controle necessários para representar sua funcionalidade.  
  
## <a name="see-also"></a>Confira também

- [Padrões de controle de automação da interface do usuário](ui-automation-control-patterns.md)
- [Padrão de texto de automação da interface do usuário](ui-automation-text-pattern.md)
- [Invocando um Controle Utilizando Automação de IU](invoke-a-control-using-ui-automation.md)
- [Obter o estado Toggle de uma caixa de seleção usando automação de interface do usuário](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [Mapeamento de Padrão de Controles para Clientes de Automação de IU](control-pattern-mapping-for-ui-automation-clients.md)
- [Amostra de texto de inserção de textpattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [Amostra de pesquisa e seleção de textpattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [InvocarPadrão, ExpandOPadrão e Amostra de Alterneo Padrão](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
