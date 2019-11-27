---
title: Implementando o padrão de controle Invoke de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: 30ae83aa4b73f36afce1251387598ef9b61816d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435166"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementando o padrão de controle Invoke de automação de interface de usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).

Este tópico apresenta as diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IInvokeProvider>, incluindo informações sobre eventos e propriedades. Links para referências adicionais são listados no final do tópico.

O padrão de controle de <xref:System.Windows.Automation.InvokePattern> é usado para dar suporte a controles que não mantêm o estado quando ativado, mas, em vez disso, inicia ou executa uma ação única e não ambígua. Os controles que mantêm o estado, como caixas de seleção e botões de opção, devem implementar <xref:System.Windows.Automation.Provider.IToggleProvider> e <xref:System.Windows.Automation.Provider.ISelectionItemProvider> respectivamente. Para obter exemplos de controles que implementam o padrão de controle Invoke, consulte [mapeamento de padrão de controle para clientes de automação da interface do usuário](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Diretrizes e convenções de implementação

Ao implementar o padrão de controle Invoke, observe as seguintes diretrizes e convenções:

- Os controles implementam <xref:System.Windows.Automation.Provider.IInvokeProvider> se o mesmo comportamento não é exposto por meio de outro provedor de padrão de controle. Por exemplo, se o método <xref:System.Windows.Automation.InvokePattern.Invoke%2A> em um controle executar a mesma ação que o <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou o método <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>, o controle não deverá implementar <xref:System.Windows.Automation.Provider.IInvokeProvider>.

- Invocar um controle geralmente é executado clicando ou clicando duas vezes ou pressionando ENTER, um atalho de teclado predefinido ou alguma combinação alternativa de pressionamentos de teclas.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> é gerado em um controle que foi ativado (como uma resposta a um controle que realiza sua ação associada). Se possível, o evento deve ser gerado depois que o controle tiver concluído a ação e retornado sem bloqueio. O evento chamado deve ser gerado antes de atender à solicitação Invoke nos seguintes cenários:

  - Não é possível ou prático aguardar até que a ação seja concluída.

  - A ação requer interação do usuário.

  - A ação é demorada e fará com que o cliente de chamada seja bloqueado por um período significativo.

- Se invocar o controle tiver efeitos colaterais significativos, esses efeitos colaterais devem ser expostos por meio da propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>. Por exemplo, embora <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> não esteja associado à seleção, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> pode fazer com que outro controle se torne selecionado.

- Os efeitos de focalizar (ou passar pelo mouse) geralmente não constituem um evento chamado. No entanto, os controles que executam uma ação (em oposição a causar um efeito visual) com base no estado de foco devem dar suporte ao padrão de controle de <xref:System.Windows.Automation.InvokePattern>.

> [!NOTE]
> Essa implementação é considerada um problema de acessibilidade se o controle puder ser invocado somente como resultado de um efeito colateral relacionado ao mouse.

- Invocar um controle é diferente de selecionar um item. No entanto, dependendo do controle, a invocação pode fazer com que o item se torne selecionado como um efeito colateral. Por exemplo, invocar um item de lista de documentos do Microsoft Word na pasta meus documentos seleciona o item e abre o documento.

- Um elemento pode desaparecer da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] imediatamente após ser invocado. A solicitação de informações do elemento fornecido pelo retorno de chamada do evento pode falhar como resultado. A solução prévia de informações em cache é a alternativa recomendada.

- Os controles podem implementar vários padrões de controle. Por exemplo, o controle cor de preenchimento na barra de ferramentas do Microsoft Excel implementa o <xref:System.Windows.Automation.InvokePattern> e os padrões de controle de <xref:System.Windows.Automation.ExpandCollapsePattern>. <xref:System.Windows.Automation.ExpandCollapsePattern> expõe o menu e o <xref:System.Windows.Automation.InvokePattern> preenche a seleção ativa com a cor escolhida.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>Membros necessários para IInvokeProvider

As propriedades e os métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IInvokeProvider>.

|Membros necessários|Tipo de membro|{1&gt;Observações&lt;1}|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|{1&gt;método&lt;1}|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> é uma chamada assíncrona e deve retornar imediatamente sem bloqueio.<br /><br /> Esse comportamento é particularmente crítico para controles que, direta ou indiretamente, iniciam uma caixa de diálogo modal quando invocada. Qualquer cliente de automação de interface do usuário que atraia o evento permanecerá bloqueado até que a caixa de diálogo modal seja fechada.|

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
