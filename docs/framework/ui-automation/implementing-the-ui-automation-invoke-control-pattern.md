---
title: Implementando o padrão de controle Invoke de automação de interface de usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8ac28b481dc9e0749762a411502c8f9660cd0cd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementando o padrão de controle Invoke de automação de interface de usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IInvokeProvider>, incluindo informações sobre propriedades e eventos. Links para referências adicionais são listadas no final do tópico.  
  
 O <xref:System.Windows.Automation.InvokePattern> padrão de controle é usado para oferecer suporte aos controles que não mantém o estado quando ativado, mas em vez de iniciar ou executar uma ação única não ambígua. Controles que mantêm o estado, como caixas de seleção e botões de opção, em vez disso, devem implementar <xref:System.Windows.Automation.Provider.IToggleProvider> e <xref:System.Windows.Automation.Provider.ISelectionItemProvider> respectivamente. Para obter exemplos de controles que implementam o padrão de controle Invoke, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Convenções e diretrizes de implementação  
 Ao implementar o padrão de controle Invoke, observe as seguintes diretrizes e convenções:  
  
-   Implementam controles <xref:System.Windows.Automation.Provider.IInvokeProvider> se o mesmo comportamento não é exposto por meio de outro provedor de padrão de controle. Por exemplo, se o <xref:System.Windows.Automation.InvokePattern.Invoke%2A> método em um controle executa a mesma ação que o <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ou <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> método, o controle não deve implementar <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Invocar um controle é geralmente executado clicando duas vezes ou pressionando ENTER, um atalho de teclado predefinido ou alguma combinação alternativa de pressionamentos de teclas.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> é gerado em um controle que tiver sido ativado (como uma resposta a um controle levar a ação associada). Se possível, o evento deve ser gerado depois que o controle tiver concluído a ação e retornado sem bloqueio. O evento Invoked deve ser gerado antes de atender a solicitação Invoke nas seguintes situações:  
  
    -   Não é possível ou prático esperar até que a ação seja concluída.  
  
    -   A ação requer interação do usuário.  
  
    -   A ação é demorada e fará com que o cliente da chamada por uma quantidade significativa de tempo.  
  
-   Se invocar o controle tiver efeitos colaterais significativos, esses efeitos colaterais devem ser expostos por meio de <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> propriedade. Por exemplo, embora <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> não está associado a seleção, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> pode fazer com que outro controle fique selecionado.  
  
-   Passe o mouse (ou passar o mouse) efeitos geralmente não constituem um evento Invoked. No entanto, os controles que executar uma ação (em oposição a causar um efeito visual) com base no estado em foco devem oferecer suporte a <xref:System.Windows.Automation.InvokePattern> padrão de controle.  
  
> [!NOTE]
>  Essa implementação é considerada um problema de acessibilidade se o controle pode ser chamado somente como resultado de um efeito relacionados ao mouse.  
  
-   Invocar um controle é diferente de selecionar um item. No entanto, dependendo do controle, invocá-lo pode causar o item seja selecionado como um efeito colateral. Por exemplo, chamar um [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] item de lista do documento na pasta Meus documentos seleciona o item e abre o documento.  
  
-   Um elemento pode desaparecer do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore imediatamente após ser chamado. Solicitar informações do elemento fornecido pelo retorno de chamada do evento pode falhar como resultado. Pré-busca de informações armazenadas em cache é a solução recomendada.  
  
-   Os controles podem implementar vários padrões de controle. Por exemplo, o controle de cor de preenchimento no [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] barra de ferramentas implementa ambos o <xref:System.Windows.Automation.InvokePattern> e <xref:System.Windows.Automation.ExpandCollapsePattern> padrões de controle. <xref:System.Windows.Automation.ExpandCollapsePattern> expõe o menu e a <xref:System.Windows.Automation.InvokePattern> preenche a seleção ativa com a cor escolhida.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Membros necessários para IInvokeProvider  
 As propriedades e métodos a seguir são necessários para implementar <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Membros necessários|Tipo de membro|Observações|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|method|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> é uma chamada assíncrona e deve retornar imediatamente sem bloqueio.<br /><br /> Esse comportamento é particularmente importante para controles que, direta ou indiretamente, iniciam uma caixa de diálogo modal quando invocado. Qualquer cliente de automação de interface do usuário que atraiu o evento permanecerá bloqueado até que a caixa de diálogo modal está fechada.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Exceções  
 Provedores devem lançar as exceções a seguir.  
  
|Tipo de exceção|Condição|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Se o controle não está habilitado.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Invocando um controle utilizando automação de interface do usuário](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
