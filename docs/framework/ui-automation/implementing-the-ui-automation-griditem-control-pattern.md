---
title: Implementando o padrão de controle GridItem de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435258"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementando o padrão de controle GridItem de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluindo informações sobre propriedades. Links para referências adicionais são listados no final da visão geral.  
  
 O padrão de controle <xref:System.Windows.Automation.GridItemPattern> é usado para dar suporte a controles filho individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IGridProvider>. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação  
 Ao implementar <xref:System.Windows.Automation.Provider.IGridProvider>, observe as seguintes diretrizes e convenções:  
  
- As coordenadas de grade são baseadas em zero com a célula superior esquerda com coordenadas (0, 0).  
  
- As células mescladas relatarão suas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> Propriedades com base em sua célula de âncora subjacente, conforme definido pelo provedor de automação de interface do usuário. Normalmente, será a linha ou coluna mais alta e mais à esquerda.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider> não fornece manipulação ativa da grade, como mesclagem ou divisão de células.  
  
- Controles que implementam <xref:System.Windows.Automation.Provider.IGridItemProvider> normalmente podem ser percorridos (ou seja, um cliente de automação da interface do usuário pode mover para controles adjacentes) usando o teclado.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Membros necessários para IGridItemProvider  
 As propriedades e os métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Membros necessários|Tipo de membro|{1&gt;Observações&lt;1}|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Propriedade|Nenhum|  
  
 Este padrão de controle não tem nenhum método ou evento associado.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem nenhuma exceção associada.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle Grid de automação de interface do usuário](implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
