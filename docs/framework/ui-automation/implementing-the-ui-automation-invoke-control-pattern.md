---
title: Implementando o padrão de controle Invoke de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: e9815e4c2c0740f213632681200e48c8e4786657
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043390"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementando o padrão de controle Invoke de automação de interface de usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.

Este tópico apresenta diretrizes e convenções para implementação <xref:System.Windows.Automation.Provider.IInvokeProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.

O <xref:System.Windows.Automation.InvokePattern> padrão de controle é usado para dar suporte a controles que não mantêm o estado quando ativado, mas, em vez disso, inicia ou executa uma ação única e não ambígua. Os controles que mantêm o estado, como caixas de seleção e botões de opção, devem <xref:System.Windows.Automation.Provider.IToggleProvider> implementar <xref:System.Windows.Automation.Provider.ISelectionItemProvider> e, respectivamente. Para obter exemplos de controles que implementam o padrão de controle Invoke, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação

Ao implementar o padrão de controle Invoke, observe as seguintes diretrizes e convenções:

- Os controles <xref:System.Windows.Automation.Provider.IInvokeProvider> implementam se o mesmo comportamento não é exposto por meio de outro provedor de padrão de controle. Por exemplo, se o <xref:System.Windows.Automation.InvokePattern.Invoke%2A> método em um controle executar a mesma ação que o <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> método <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> ou, o controle não deverá ser <xref:System.Windows.Automation.Provider.IInvokeProvider>implementado.

- Invocar um controle geralmente é executado clicando ou clicando duas vezes ou pressionando ENTER, um atalho de teclado predefinido ou alguma combinação alternativa de pressionamentos de teclas.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>é gerado em um controle que foi ativado (como uma resposta a um controle que realiza sua ação associada). Se possível, o evento deve ser gerado depois que o controle tiver concluído a ação e retornado sem bloqueio. O evento chamado deve ser gerado antes de atender à solicitação Invoke nos seguintes cenários:

  - Não é possível ou prático aguardar até que a ação seja concluída.

  - A ação requer interação do usuário.

  - A ação é demorada e fará com que o cliente de chamada seja bloqueado por um período significativo.

- Se invocar o controle tiver efeitos colaterais significativos, esses efeitos colaterais devem ser expostos por meio <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> da propriedade. Por exemplo, embora <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> não esteja associado à seleção, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> o pode fazer com que outro controle se torne selecionado.

- Os efeitos de focalizar (ou passar pelo mouse) geralmente não constituem um evento chamado. No entanto, os controles que executam uma ação (em oposição a causar um efeito visual) com base no estado <xref:System.Windows.Automation.InvokePattern> de foco devem dar suporte ao padrão de controle.

> [!NOTE]
> Essa implementação é considerada um problema de acessibilidade se o controle puder ser invocado somente como resultado de um efeito colateral relacionado ao mouse.

- Invocar um controle é diferente de selecionar um item. No entanto, dependendo do controle, a invocação pode fazer com que o item se torne selecionado como um efeito colateral. Por exemplo, invocar um [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] item de lista de documentos na pasta meus documentos seleciona o item e abre o documento.

- Um elemento pode desaparecer da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore imediatamente após ser invocado. A solicitação de informações do elemento fornecido pelo retorno de chamada do evento pode falhar como resultado. A solução prévia de informações em cache é a alternativa recomendada.

- Os controles podem implementar vários padrões de controle. Por exemplo, o controle cor de preenchimento na [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] barra de ferramentas implementa <xref:System.Windows.Automation.InvokePattern> o e <xref:System.Windows.Automation.ExpandCollapsePattern> os padrões de controle. <xref:System.Windows.Automation.ExpandCollapsePattern>expõe o menu e <xref:System.Windows.Automation.InvokePattern> preenche a seleção ativa com a cor escolhida.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>Membros necessários para IInvokeProvider

As propriedades e os métodos a seguir são necessários <xref:System.Windows.Automation.Provider.IInvokeProvider>para implementar o.

|Membros necessários|Tipo de membro|Observações|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|method|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>é uma chamada assíncrona e deve retornar imediatamente sem bloqueio.<br /><br /> Esse comportamento é particularmente crítico para controles que, direta ou indiretamente, iniciam uma caixa de diálogo modal quando invocada. Qualquer cliente de automação de interface do usuário que atraia o evento permanecerá bloqueado até que a caixa de diálogo modal seja fechada.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Exceções

Os provedores devem lançar as seguintes exceções.

|Tipo de exceção|Condição|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|Se o controle não está habilitado.|

## <a name="see-also"></a>Consulte também

- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Invocando um controle utilizando automação de interface do usuário](invoke-a-control-using-ui-automation.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
