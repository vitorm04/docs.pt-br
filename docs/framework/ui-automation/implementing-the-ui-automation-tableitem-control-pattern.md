---
title: 'Implementando o padrão de controle TableItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: db94a1a4588c2f889da8adb1cb3e47e208ce1211
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528666"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementando o padrão de controle TableItem de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.ITableItemProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final da visão geral.  
  
 O <xref:System.Windows.Automation.TableItemPattern> padrão de controle é usado para dar suporte a controles filhos de contêineres que implementam <xref:System.Windows.Automation.Provider.ITableProvider>. Acesso à funcionalidade das células individuais é fornecido pela implementação simultânea necessária de <xref:System.Windows.Automation.Provider.IGridItemProvider>. Esse padrão de controle é análogo à <xref:System.Windows.Automation.Provider.IGridItemProvider> com a diferença que qualquer controle implementando <xref:System.Windows.Automation.Provider.ITableItemProvider> por meio de programação deve expor a relação entre a célula individual e suas informações de linha e coluna. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
  
-   Para a funcionalidade do item de grade relacionados, consulte [Implementando o padrão de controle GridItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>Membros necessários para ITableItemProvider  
  
|Membro necessário|Tipo de membro|Observações|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Método|Nenhum|  
  
 Esse padrão de controle não tem propriedades associadas ou eventos.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Esse padrão de controle não tem exceção associada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementando o padrão de controle Table de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [Implementando o padrão de controle GridItem de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
