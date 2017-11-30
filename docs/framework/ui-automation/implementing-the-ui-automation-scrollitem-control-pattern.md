---
title: "Implementando o padrão de controle ScrollItem de interface de usuário "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 92c3b4fad775dcd04299e18da126107d8fbb4471
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a>Implementando o padrão de controle ScrollItem de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar o <xref:System.Windows.Automation.Provider.IScrollItemProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.ScrollItemPattern> padrão de controle é usado para suportar controles filhos individuais de contêiners que implementam <xref:System.Windows.Automation.Provider.IScrollProvider>. Esse padrão de controle atua como um canal de comunicação entre um controle filho e seu recipiente para garantir que o recipiente pode mudar o conteúdo visível no momento (ou região) no seu viewport para exibir o controle filho. Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Convenções e diretrizes de implementação  
 Ao implementar o padrão de controle Item de rolagem, observe as seguintes diretrizes e convenções:  
  
-   Os itens contidos em um controle de janela ou tela não são necessários para implementar a interface IScrollItemProvider. Como alternativa, no entanto, eles devem expor um local válido para o <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>. Isso permitirá que um aplicativo de cliente de automação de interface do usuário para usar o <xref:System.Windows.Automation.ScrollPattern> controlar os métodos padrão no contêiner para exibir o item filho.  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a>Membros necessários para IScrollItemProvider  
 O método a seguir é necessário para implementar a interface IScrollProvider.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|-Método|Nenhum|  
  
 Esse padrão de controle não tem propriedades associadas ou eventos.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Se um item não pode ser rolado para a exibição:<br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
