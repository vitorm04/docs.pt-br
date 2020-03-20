---
title: Implementando o padrão de controle Scroll de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll control pattern
- control patterns, Scroll
- Scroll control pattern
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
ms.openlocfilehash: 0420adaefb91f0c9f0d34d5bdf5863373a0b652b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180158"
---
# <a name="implementing-the-ui-automation-scroll-control-pattern"></a>Implementando o padrão de controle Scroll de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IScrollProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.  
  
 O <xref:System.Windows.Automation.ScrollPattern> padrão de controle é usado para apoiar um controle que age como um recipiente rolável para uma coleção de objetos infantis. O controle não é necessário para usar barras de rolagem para suportar a funcionalidade de rolagem, embora normalmente o faça.  
  
 ![Controle de rolagem sem rolagem.](./media/uia-scrollpattern-without-scrollbars.PNG "UIA_ScrollPattern_Without_Scrollbars")  
Exemplo de um controle de rolagem que não usa barras de rolagem  
  
 Para exemplos de controles que implementam esse controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário.](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao implementar o padrão de controle Scroll, observe as seguintes diretrizes e convenções:  
  
- O filho desse controle deve implementar <xref:System.Windows.Automation.Provider.IScrollItemProvider>.  
  
- As barras de rolagem de <xref:System.Windows.Automation.ScrollPattern> um controle de contêiner não suportam o padrão de controle. Eles devem <xref:System.Windows.Automation.RangeValuePattern> apoiar o padrão de controle em vez disso.  
  
- Quando a rolagem é medida em percentuais, todos os valores ou valores relacionados à graduação de rolagem devem ser normalizados para uma faixa de 0 a 100.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>e <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> são independentes do <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>.  
  
- <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>  =  `false` Se, <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> em seguida, deve ser <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> definido para <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>100% e deve ser definido como . Da mesma <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>  =  `false` forma, se então <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> deve ser <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> definido para <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>100 por cento e deve ser definido como . Isso permite que um cliente de Automação <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> de UI use esses valores de propriedade dentro do método, evitando uma [condição de corrida](https://support.microsoft.com/default.aspx?scid=kb;en-us;317723) se uma direção que o cliente não está interessado em rolar for ativada.  
  
- <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>é específico local. A configuração HorizontalScrollPercent = 100.0 deve definir o local de rolagem do controle para o equivalente à sua posição mais à direita para idiomas como o inglês que lê da esquerda para a direita. Alternativamente, para idiomas como o árabe que lêem da direita para a esquerda, a configuração HorizontalScrollPercent = 100.0 deve definir o local do pergaminho para a posição mais à esquerda.  
  
<a name="Required_Members_for_IScrollProvider"></a>
## <a name="required-members-for-iscrollprovider"></a>Membros obrigatórios para IScrollProvider  
 As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.IScrollProvider>são necessários para a implementação.  
  
|Membro obrigatório|Tipo de membro|Observações|  
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
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>lança essa exceção se <xref:System.Windows.Automation.ScrollAmount.SmallIncrement> um controle suportar valores exclusivamente <xref:System.Windows.Automation.ScrollAmount.LargeIncrement> para rolagem horizontal ou vertical, mas um valor é passado.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>lança essa exceção quando um valor que não pode ser convertido em um duplo é passado.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>lança essa exceção quando um valor maior que 100 ou menos de <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>0 é passado (exceto -1 que é equivalente a ).|  
|<xref:System.InvalidOperationException>|Ambos <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> e jogue esta exceção quando uma tentativa é feita para rolar em uma direção sem suporte.|  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
