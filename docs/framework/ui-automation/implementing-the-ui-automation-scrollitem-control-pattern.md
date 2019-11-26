---
title: Implementando o padrão de controle ScrollItem de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 1e33a64e66bc084e8cc5f75ece2ac2a4d7ea85aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447132"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implementando o padrão de controle ScrollItem de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IScrollItemProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final do tópico.  
  
 O padrão de controle <xref:System.Windows.Automation.ScrollItemPattern> é usado para dar suporte a controles filho individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IScrollProvider>. Esse padrão de controle atua como um canal de comunicação entre um controle filho e seu contêiner para garantir que o contêiner possa alterar o conteúdo visível no momento (ou região) dentro de seu visor para exibir o controle filho. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar o padrão de controle de item de rolagem, observe as seguintes diretrizes e convenções:  
  
- Os itens contidos em um controle de janela ou Canvas não são necessários para implementar a interface IScrollItemProvider. No entanto, como alternativa, eles devem expor um local válido para o <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Isso permitirá que um aplicativo cliente de automação da interface do usuário use os métodos de padrão de controle de <xref:System.Windows.Automation.ScrollPattern> no contêiner para exibir o item filho.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Membros necessários para IScrollItemProvider  
 O método a seguir é necessário para implementar a interface IScrollProvider.  
  
|Membros necessários|Tipo de membro|{1&gt;Observações&lt;1}|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Método|Nenhum|  
  
 Este padrão de controle não tem propriedades ou eventos associados.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Os provedores devem lançar as seguintes exceções.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Se um item não puder ser rolado para a exibição:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
