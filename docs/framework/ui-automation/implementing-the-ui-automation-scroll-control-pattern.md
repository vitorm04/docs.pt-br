---
title: Implementando o padrão de controle Scroll de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 8efbe02098041b2037da94925e56244a28895e0b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677507"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementando o padrão de controle Scroll de automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IScrollProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.ScrollPattern> padrão de controle é usado para dar suporte a um controle que atua como um contêiner rolável para uma coleção de objetos filho. O controle não é necessário usar as barras de rolagem para dar suporte à funcionalidade de rolagem, embora ele normalmente faz.  
  
 ![Controle de rolagem sem barras de rolagem. ](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Exemplo de um controle de rolagem que não usa barras de rolagem  
  
 Para obter exemplos de controles que implementam esse controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar o padrão de controle Scroll, observe as seguintes diretrizes e convenções:  
  
-   O filho desse controle deve implementar <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
-   As barras de rolagem de um controle de contêiner não dão suporte a <xref:System.Windows.Automation.ScrollPattern> padrão de controle. Eles devem dar suporte a <xref:System.Windows.Automation.RangeValuePattern> em vez disso, o padrão de controle.  
  
-   Quando a rolagem é medida em porcentagens, todos os valores ou valores relacionados à graduação de rolagem deve ser normalizadas em um intervalo de 0 a 100.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> e <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> independem do <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
-   Se <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` , em seguida, <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> deve ser definido como 100% e <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> deve ser definido como <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Da mesma forma, se <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` , em seguida, <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> deve ser definido como 100 por cento e <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> deve ser definido como <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>. Isso permite que um cliente de automação de interface do usuário para usar esses valores de propriedade dentro de <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> método, evitando uma [condição de corrida](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) se uma direção o cliente não estiver interessado em rolagem torna-se ativado.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A> é específica da localidade. Configuração HorizontalScrollPercent = 100,0 deve definir o local de rolagem do controle para o equivalente da sua posição mais à direita para idiomas como inglês lidos da esquerda para a direita. Como alternativa, para idiomas como árabe lidos da direita para esquerda, a configuração HorizontalScrollPercent = 100,0 deve definir o local de rolagem para a posição mais à esquerda.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## <a name="required-members-for-iscrollprovider"></a>Membros necessários para IScrollProvider  
 As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IScrollProvider>.  
  
|Membro necessário|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|Método|Nenhum|  
  
 Esse padrão de controle não tem eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> gera esta exceção se um controle suporta <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> valores exclusivamente para rolagem horizontal ou vertical, mas um <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> valor é passado.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> gera esta exceção quando um valor que não pode ser convertido em um duplo é passado.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> gera esta exceção quando um valor maior que 100 ou menor que 0 é passado (exceto -1 que é equivalente a <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>).|  
|<xref:System.InvalidOperationException>|Ambos <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> e <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> geram esta exceção quando é feita uma tentativa de rolar em uma direção sem suporte.|  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
