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
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties. Links to additional references are listed at the end of the overview.  
  
 The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:  
  
- Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).  
  
- Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider. Typically, it will be the topmost and leftmost row or column.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.  
  
- Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Required Members for IGridItemProvider  
 The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Required members|Member type|Anotações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|propriedade|Nenhum|  
  
 This control pattern has no associated methods or events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 This control pattern has no associated exceptions.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle Grid de automação de interface do usuário](implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
