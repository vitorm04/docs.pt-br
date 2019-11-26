---
title: Implementando o padrão de controle Scroll de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: d146ba67f4fe3f5fda6196231f96f428f702086a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447164"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementando o padrão de controle Scroll de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IScrollProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O padrão de controle <xref:System.Windows.Automation.ScrollPattern> é usado para dar suporte a um controle que atua como um contêiner rolável para uma coleção de objetos filho. O controle não é necessário para usar barras de rolagem para dar suporte à funcionalidade de rolagem, embora normalmente faça isso.  
  
 ![Controle de rolagem sem barras de rolagem.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Exemplo de um controle de rolagem que não usa barras de rolagem  
  
 Para obter exemplos de controles que implementam esse controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de rolagem, observe as seguintes diretrizes e convenções:  
  
- O filho desse controle deve implementar <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
- As barras de rolagem de um controle de contêiner não dão suporte ao padrão de controle de <xref:System.Windows.Automation.ScrollPattern>. Em vez disso, eles devem oferecer suporte ao padrão de controle de <xref:System.Windows.Automation.RangeValuePattern>.  
  
- Quando a rolagem é medida em percentuais, todos os valores ou quantidades relacionados à formatura de rolagem devem ser normalizados para um intervalo de 0 a 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> e <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> são independentes do <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
- Se <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> = `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> deverá ser definido como 100% e <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> deverá ser definido como <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Da mesma forma, se <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> = `false` <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> deverá ser definido como 100 por cento e <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> deve ser definido como <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Isso permite que um cliente de automação da interface do usuário use esses valores de propriedade dentro do método <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> ao mesmo tempo em que evita uma [condição de corrida](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) se uma direção na qual o cliente não está interessado em rolar é ativada.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> é específico da localidade. A definição de HorizontalScrollPercent = 100,0 deve definir o local de rolagem do controle como o equivalente de sua posição mais à direita para idiomas como o inglês que são lidos da esquerda para a direita. Como alternativa, para idiomas como o árabe que são lidos da direita para a esquerda, a definição de HorizontalScrollPercent = 100,0 deve definir o local de rolagem para a posição mais à esquerda.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Membros necessários para IScrollProvider  
 As propriedades e os métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
|Membro necessário|Tipo de membro|{1&gt;Observações&lt;1}|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> gera essa exceção se um controle dá suporte a valores de <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> exclusivamente para rolagem horizontal ou vertical, mas um valor de <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> é passado.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> gera essa exceção quando um valor que não pode ser convertido em um Double é passado.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> gera essa exceção quando um valor maior que 100 ou menor que 0 é passado (exceto-1, que é equivalente a <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Ambos <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> e <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> gerar essa exceção quando for feita uma tentativa de rolar em uma direção sem suporte.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
