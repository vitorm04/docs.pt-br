---
title: 'Implementando o padrão de controle GridItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180195"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementando o padrão de controle GridItem de interface de usuário 
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.IGridItemProvider>convenções para a implementação, incluindo informações sobre propriedades. Os links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.GridItemPattern> padrão de controle é usado para apoiar <xref:System.Windows.Automation.Provider.IGridProvider>controles individuais de crianças de recipientes que implementam . Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
 Ao <xref:System.Windows.Automation.Provider.IGridProvider>implementar, observe as seguintes diretrizes e convenções:  
  
- As coordenadas da grade são baseadas em zero com a célula superior esquerda tendo coordenadas (0,0).  
  
- As células mescladas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> reportarão suas propriedades com base em sua célula âncora subjacente, conforme definido pelo provedor de Automação de UI. Normalmente, será a linha ou coluna mais alta e mais à esquerda.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>não prevê manipulação ativa da grade, como a fusão ou divisão de células.  
  
- Os controles <xref:System.Windows.Automation.Provider.IGridItemProvider> que implementam podem ser normalmente atravessados (ou seja, um cliente de Automação de IU pode se mover para controles adjacentes) usando o teclado.  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>Membros obrigatórios para IGridItemProvider  
 As seguintes propriedades e métodos <xref:System.Windows.Automation.Provider.IGridItemProvider>são necessários para a implementação.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Propriedade|Nenhum|  
  
 Este padrão de controle não tem métodos ou eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem exceções associadas.  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o Padrão de Controle Grid de Automação de Interface de Usuário](implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
