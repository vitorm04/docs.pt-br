---
title: Implementando o padrão de controle ExpandCollapse de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 232bceba8286c2566a7df03b9001a5c43b348b20
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043455"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementando o padrão de controle ExpandCollapse de interface de usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.

Este tópico apresenta as diretrizes e convenções para <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>implementar o, incluindo informações sobre propriedades, métodos e eventos. Links para referências adicionais são listados no final da visão geral.

O <xref:System.Windows.Automation.ExpandCollapsePattern> padrão de controle é usado para dar suporte a controles que expandem visualmente para exibir mais conteúdo e recolher para ocultar o conteúdo. Para obter exemplos de controles que implementam esse padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação

Ao implementar o padrão de controle ExpandCollapse, observe as seguintes diretrizes e convenções:

- Controles de agregação — criados com objetos filho que fornecem a interface do usuário com funcionalidade de expandir/ <xref:System.Windows.Automation.ExpandCollapsePattern> recolher — devem oferecer suporte ao padrão de controle, enquanto seus elementos filho não. Por exemplo, um controle de caixa de combinação é criado com uma combinação de controles de caixa de listagem, botões e edição, mas é apenas a caixa de combinação pai que <xref:System.Windows.Automation.ExpandCollapsePattern>deve dar suporte ao.

  > [!NOTE]
  > Uma exceção é o controle de menu, que é uma agregação de objetos individuais MenuItem. Os objetos MenuItem podem dar suporte <xref:System.Windows.Automation.ExpandCollapsePattern> ao padrão de controle, mas o controle menu pai não pode. Uma exceção semelhante se aplica aos controles de item de árvore e árvore.

- Quando o <xref:System.Windows.Automation.ExpandCollapseState> de um controle é definido como <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, qualquer <xref:System.Windows.Automation.ExpandCollapsePattern> funcionalidade está inativa no momento para o controle e as únicas informações que podem ser obtidas usando esse padrão de <xref:System.Windows.Automation.ExpandCollapseState>controle é o. Se qualquer objeto filho for adicionado posteriormente, as <xref:System.Windows.Automation.ExpandCollapseState> alterações e <xref:System.Windows.Automation.ExpandCollapsePattern> a funcionalidade serão ativadas.

- <xref:System.Windows.Automation.ExpandCollapseState>refere-se apenas à visibilidade de objetos filho imediatos; Ele não se refere à visibilidade de todos os objetos descendentes.

- A funcionalidade de expandir e recolher é específica ao controle. Veja a seguir exemplos desse comportamento.

  - O menu pessoal do Office pode ser um MenuItem de três Estados<xref:System.Windows.Automation.ExpandCollapseState.Expanded>( <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> e <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) em que o controle Especifica o estado a ser adotado <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> quando um <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou é chamado.

  - Chamar <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> em um TreeItem pode exibir todos os descendentes ou apenas filhos imediatos.

  - Se chamar <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> em um controle mantiver o estado de seus descendentes, um evento de alteração de visibilidade deverá ser enviado, não um evento de alteração de estado se o controle pai não mantiver o estado de seus descendentes quando recolhido, o controle poderá destruir todos os descendentes que não estão mais visíveis e gerar um evento destruído; ou pode alterar o <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> para cada descendente e gerar um evento de alteração de visibilidade.

- Para garantir a navegação, é desejável que um objeto esteja na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore (com o estado de visibilidade apropriado), independentemente de seus pais. <xref:System.Windows.Automation.ExpandCollapseState> Se os descendentes forem gerados sob demanda, eles só poderão aparecer na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore depois de serem exibidos pela primeira vez ou somente enquanto estiverem visíveis.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>Membros necessários para IExpandCollapseProvider

As propriedades e os métodos a seguir são necessários <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>para implementar o.

|Membros necessários|Tipo de membro|Observações|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Propriedade|Nenhum|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Método|Nenhum|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Método|Nenhum|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|evento|Este controle não tem eventos associados; Use este delegado genérico.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Exceções

Os provedores devem lançar as seguintes exceções.

|Tipo de exceção|Condição|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> Ou é<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> chamado quando o <xref:System.Windows.Automation.ExpandCollapseState> . =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>|

## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Navegar em elementos de automação de interface do usuário com o TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
