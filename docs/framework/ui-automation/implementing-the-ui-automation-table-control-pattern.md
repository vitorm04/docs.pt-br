---
title: Implementando o padrão de controle de tabela de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 8e929f181255f6738261533fa3261187ebe3c6ff
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447098"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementando o padrão de controle de tabela de automação de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events. Links to additional references are listed at the end of the overview.  
  
 The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements. The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column. This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Table control pattern, note the following guidelines and conventions:  
  
- Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
- A column or row header can be contained within a table object or be a separate header object that is associated with a table object.  
  
- Column and row headers may include both a primary header as well as any supporting headers.  
  
> [!NOTE]
> This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column. This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.  
  
- See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.  
  
 ![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Example of a Table with Complex Column Headers  
  
 ![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Example of a Table with Ambiguous RowOrColumnMajor Property  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Required Members for ITableProvider  
 The following properties and methods are required for the ITableProvider interface.  
  
|Required members|Member type|Anotações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Método|Nenhum|  
  
 This control pattern has no associated events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 This control pattern has no associated exceptions.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle TableItem de automação de interface do usuário](implementing-the-ui-automation-tableitem-control-pattern.md)
- [Implementando o padrão de controle Grid de automação de interface do usuário](implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
