---
title: 'Implementando o padrão de controle ExpandCollapse de interface de usuário '
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: f593fb09e8c1056c28d351bfdf0218a0161fd9e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403800"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementando o padrão de controle ExpandCollapse de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listadas no final da visão geral.  
  
 O <xref:System.Windows.Automation.ExpandCollapsePattern> padrão de controle é usado para oferecer suporte aos controles que visualmente expandem para exibir mais conteúdo e recolher para ocultar o conteúdo. Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Convenções e diretrizes de implementação  
 Ao implementar o padrão de controle ExpandCollapse, observe as seguintes diretrizes e convenções:  
  
-   Controles agregados — criados com objetos filho que fornecem a interface do usuário com a funcionalidade de expandir/recolher — devem oferecer suporte a <xref:System.Windows.Automation.ExpandCollapsePattern> padrão de controle, ao passo que seus elementos filho não. Por exemplo, um controle de caixa de combinação é criado com uma combinação de caixa de listagem, um botão e controles de edição, mas é apenas a caixa de combinação pai que deve oferecer suporte a <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Uma exceção é o controle de menu, que é uma agregação de objetos individuais MenuItem. Os objetos MenuItem podem dar suporte a <xref:System.Windows.Automation.ExpandCollapsePattern> padrão de controle, mas o pai não é possível de controle de Menu. Uma exceção similar se aplica a controles de árvore e o Item de árvore.  
  
-   Quando o <xref:System.Windows.Automation.ExpandCollapseState> de um controle é definido como <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, qualquer <xref:System.Windows.Automation.ExpandCollapsePattern> funcionalidade está inativa no momento para o controle e a única informação que pode ser obtida usando esse padrão de controle é o <xref:System.Windows.Automation.ExpandCollapseState>. Se qualquer objeto filho for adicionado posteriormente, o <xref:System.Windows.Automation.ExpandCollapseState> alterações e <xref:System.Windows.Automation.ExpandCollapsePattern> funcionalidade está ativada.  
  
-   <xref:System.Windows.Automation.ExpandCollapseState> refere-se a visibilidade dos objetos de filho imediatos. ele não faz referência a visibilidade de todos os objetos descendentes.  
  
-   Expanda e funcionalidade recolher é específica do controle. A seguir estão exemplos desse comportamento.  
  
    -   O Menu de pessoal do Office pode ser um MenuItem de três estados (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> e <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) onde o controle especifica o estado a adotar quando um <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> é chamado.  
  
    -   Chamando <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> em um TreeItem pode exibir todos os descendentes ou somente os filhos imediatos.  
  
    -   Se chamar <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> em um controle mantém o estado de seus descendentes, um evento de alteração de visibilidade deve ser enviado, não um evento de alteração de estado se o controle pai não mantém o estado de seus descendentes quando recolhido, o controle pode destruir todos os descendentes que não são mais visíveis e geram um evento destruído. ou pode alterar o <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> para cada descendente e acionar uma visibilidade do evento de alteração.  
  
-   Para garantir a navegação, é desejável para um objeto no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore (com o estado de visibilidade apropriada), independentemente de seus pais <xref:System.Windows.Automation.ExpandCollapseState>. Se os descendentes são geradas sob demanda, eles só podem aparecer no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore depois de ser exibidos pela primeira vez ou somente enquanto eles estão visíveis.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Membros necessários para IExpandCollapseProvider  
 As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Propriedade|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Método|Nenhum|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|evento|Esse controle não tem eventos associados; Use esse delegado genérico.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|O <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> é chamado quando o <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Navegar em elementos de automação de interface do usuário com o TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
