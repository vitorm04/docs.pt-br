---
title: Implementando o padrão de controle TableItem de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: f35b491c31e8725eac0025dfd6815079d0ea9b79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180073"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementando o padrão de controle TableItem de interface de usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz diretrizes e <xref:System.Windows.Automation.Provider.ITableItemProvider>convenções para a implementação, incluindo informações sobre eventos e propriedades. Os links para referências adicionais são listados no final da visão geral.  
  
 O <xref:System.Windows.Automation.TableItemPattern> padrão de controle é usado para apoiar <xref:System.Windows.Automation.Provider.ITableProvider>o controle infantil de recipientes que implementam . O acesso à funcionalidade celular individual é fornecido <xref:System.Windows.Automation.Provider.IGridItemProvider>pela implementação simultânea necessária de . Esse padrão de controle <xref:System.Windows.Automation.Provider.IGridItemProvider> é análogo à <xref:System.Windows.Automation.Provider.ITableItemProvider> distinção de que qualquer implementação de controle deve expor programáticamente a relação entre a célula individual e suas informações de linha e coluna. Para exemplos de controles que implementam esse padrão de controle, consulte Mapping de padrão de [controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e Convenções de Implementação  
  
- Para obter a funcionalidade de item de grade relacionado, consulte [Implementando o padrão](implementing-the-ui-automation-griditem-control-pattern.md)de controle de grade de automação de ui .  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a>Membros obrigatórios para ITableItemProvider  
  
|Membro obrigatório|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Método|Nenhum|  
  
 Este padrão de controle não tem propriedades ou eventos associados.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Exceções  
 Este padrão de controle não tem exceções associadas.  
  
## <a name="see-also"></a>Confira também

- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Padrões de controle de suporte em um provedor de automação da interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle de tabela de automação de interface de usuário](implementing-the-ui-automation-table-control-pattern.md)
- [Implementando o padrão de controle GridItem de interface de usuário ](implementing-the-ui-automation-griditem-control-pattern.md)
- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
