---
title: Visão geral sobre eventos de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1c479bc423ba17e527926bbf9c7dae6ffd8845d1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400307"
---
# <a name="ui-automation-events-overview"></a>Visão geral sobre eventos de automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] notificação de eventos é um recurso importante para tecnologias auxiliares, como leitores de tela e lentes. Esses eventos acompanhar clientes de automação de interface do usuário que são gerados por provedores de automação de interface do usuário quando algo acontece no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] e use as informações para notificar os usuários finais.  
  
 Eficiência é aprimorada permitindo que aplicativos de provedor gerar eventos seletivamente, dependendo se todos os clientes estão inscritos para esses eventos, ou não, se nenhum cliente está ouvindo os eventos.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Tipos de eventos  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos se enquadram nas categorias a seguir.  
  
|evento|Descrição|  
|-----------|-----------------|  
|Alteração de propriedade|Gerado quando uma propriedade em um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mudanças de padrão de controle ou elemento. Por exemplo, se um cliente precisa monitorar o controle de caixa de seleção de um aplicativo, ele pode registrar para escutar um evento de alteração de propriedade no <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> propriedade. Quando o controle de caixa de seleção está marcado ou desmarcado, o provedor gera o evento e o cliente possa agir conforme necessário.|  
|Elemento de ação|Gerado quando uma alteração na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] resultados do usuário final ou de atividade de programação; por exemplo, quando um botão é clicado ou invocado por meio de <xref:System.Windows.Automation.InvokePattern>.|  
|Alteração de estrutura|Gerado quando a estrutura do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] alterações de árvore. A estrutura é alterada quando novos [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens se tornam visíveis, ocultos ou removidos na área de trabalho.|  
|Alteração da área de trabalho global|Gerado quando ocorrem as ações de interesse global para o cliente, como quando o foco muda de um elemento para outro, ou quando fecha uma janela.|  
  
 Alguns eventos não significam necessariamente que o estado da interface do usuário foi alterado. Por exemplo, se o usuário pressiona TAB para um campo de entrada de texto e, em seguida, clica em um botão para atualizar o campo, um `TextChangedEvent` é gerado, mesmo se o usuário não tiver alterado realmente o texto. Ao processar um evento, pode ser necessário para um aplicativo cliente verificar se, na verdade, nada foi alterado antes de tomar.  
  
 Os seguintes eventos podem ser gerados, mesmo quando o estado da interface do usuário não foi alterado.  
  
-   `AutomationPropertyChangedEvent` (dependendo da propriedade que foi alterada)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>Identificadores de eventos de automação de interface do usuário  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] eventos são identificados pela <xref:System.Windows.Automation.AutomationEvent> objetos. O <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> propriedade contém um valor que identifica exclusivamente o tipo de evento.  
  
 Os valores possíveis para <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> são fornecidos na tabela a seguir, junto com o tipo usado para argumentos de evento. Observe que os identificadores usados por clientes e provedores são nomeados identicamente campos de classes diferentes.  
  
|Identificador de cliente|Identificador do provedor|Tipo de argumentos de evento|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>Argumentos de evento de automação de interface do usuário  
 As seguintes classes encapsulam os argumentos do evento.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Contém informações sobre o carregamento assíncrono do conteúdo, incluindo a porcentagem de carregamento concluído.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Contém informações sobre um evento simples que exige nenhum dado extra.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Contém informações sobre uma alteração de foco de entrada de um elemento para outro. Eventos desse tipo são gerados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistema, não por meio de provedores.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Contém informações sobre uma alteração no valor de uma propriedade de um padrão de controle ou elemento.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Contém informações sobre uma alteração no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Contém informações sobre o fechamento de uma janela.|  
  
 Todas as classes de argumento de evento contém um <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> membro. Esse identificador é encapsulado em um <xref:System.Windows.Automation.AutomationEvent>.  
  
 O <xref:System.Windows.Automation.AutomationEvent> objetos usados para identificar os eventos são obtidos por provedores de campos na <xref:System.Windows.Automation.AutomationElementIdentifiers> e classes de padrão de identificador de controle, como <xref:System.Windows.Automation.DockPatternIdentifiers>. Os campos equivalentes são obtidos por aplicativos cliente dos campos em <xref:System.Windows.Automation.AutomationElement> e classes de padrão de controle, como <xref:System.Windows.Automation.DockPattern>.  
  
 Para obter uma lista de identificadores de evento, consulte [eventos de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [Assinar eventos de automação de interface do usuário](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
