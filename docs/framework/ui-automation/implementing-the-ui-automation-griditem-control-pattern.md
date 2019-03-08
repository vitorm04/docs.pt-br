---
title: 'Implementando o padrão de controle GridItem de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: ff3f52d37a7d45b92981969983652f48f5071959
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675765"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementando o padrão de controle GridItem de interface de usuário 
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>, incluindo informações sobre as propriedades. Links para referências adicionais são listadas no final da visão geral.  
  
 O <xref:System.Windows.Automation.GridItemPattern> padrão de controle é usado para dar suporte a controles filhos individuais de contêineres que implementam <xref:System.Windows.Automation.Provider.IGridProvider>. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>As convenções e diretrizes de implementação  
 Ao implementar <xref:System.Windows.Automation.Provider.IGridProvider>, observe as seguintes diretrizes e convenções:  
  
-   Coordenadas de grade são baseadas em zero com a célula superior esquerda tendo as coordenadas (0, 0).  
  
-   As células mescladas relatará suas <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> e <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> propriedades com base em suas células âncoras subjacentes, conforme definido pelo provedor de automação de interface do usuário. Normalmente, ele será a mais à esquerda e superior de linha ou coluna.  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> não fornece para manipulação ativa da grade como mesclar ou dividir células.  
  
-   Controles que implementam <xref:System.Windows.Automation.Provider.IGridItemProvider> normalmente pode ser percorrido (isto é, um cliente de automação de interface do usuário pode mover para os controles adjacentes) usando o teclado.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Membros necessários para IGridItemProvider  
 As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Propriedade|Nenhum|  
  
 Esse padrão de controle não tem métodos associados ou eventos.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Esse padrão de controle não tem exceção associada.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementando o padrão de controle Grid de automação de interface do usuário](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
