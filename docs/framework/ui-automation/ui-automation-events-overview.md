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
ms.openlocfilehash: 495e7d29c814164f4235d18569477b856cb09045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179889"
---
# <a name="ui-automation-events-overview"></a>Visão geral sobre eventos de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]a notificação de eventos é um recurso-chave para tecnologias assistivas, como leitores de tela e lupas de tela. Esses clientes de Automação de Interface do Usuário rastreiam eventos [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] que são levantados por provedores de automação de interface do usuário quando algo acontece no e usam as informações para notificar os usuários finais.  
  
 A eficiência é melhorada ao permitir que os aplicativos do provedor levantem eventos seletivamente, dependendo se algum cliente está inscrito nesses eventos, ou não, se nenhum cliente está ouvindo qualquer evento.  
  
<a name="Types_of_Events"></a>
## <a name="types-of-events"></a>Tipos de eventos  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]eventos se enquadram nas seguintes categorias.  
  
|Evento|Descrição|  
|-----------|-----------------|  
|Alteração da propriedade|Elevado quando uma propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em um elemento ou padrão de controle muda. Por exemplo, se um cliente precisar monitorar o controle da caixa de seleção <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> de um aplicativo, ele pode se registrar para ouvir um evento de alteração de propriedade na propriedade. Quando o controle da caixa de seleção é verificado ou desmarcado, o provedor levanta o evento e o cliente pode agir conforme necessário.|  
|Ação de elemento|Elevado quando uma alteração [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] nos resultados de atividade suitiva ou programática do usuário final; por exemplo, quando um botão é <xref:System.Windows.Automation.InvokePattern>clicado ou invocado através de .|  
|Alteração de estrutura|Levantado quando a estrutura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore muda. A estrutura muda [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] quando novos itens se tornam visíveis, ocultos ou removidos na área de trabalho.|  
|Mudança global de desktop|Levantada quando ocorrem ações de interesse global para o cliente, como quando o foco muda de um elemento para outro, ou quando uma janela fecha.|  
  
 Alguns eventos não indicam necessariamente que o estado da interface do usuário mudou. Por exemplo, se o usuário fizer as guias em um campo de `TextChangedEvent` entrada de texto e clicar em um botão para atualizar o campo, um será levantado mesmo que o usuário não tenha realmente alterado o texto. Ao processar um evento, pode ser necessário que o aplicativo cliente verifique se algo realmente mudou antes de executar uma ação.  
  
 Os seguintes eventos podem ser levantados mesmo quando o estado da UI não mudou.  
  
- `AutomationPropertyChangedEvent`(dependendo da propriedade que mudou)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>
## <a name="ui-automation-event-identifiers"></a>Identificadores de eventos de automação de ida e usuário  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]eventos são <xref:System.Windows.Automation.AutomationEvent> identificados por objetos. A <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> propriedade contém um valor que identifica exclusivamente o tipo de evento.  
  
 Os valores <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> possíveis são dados na tabela a seguir, juntamente com o tipo utilizado para argumentos de eventos. Observe que os identificadores usados por clientes e provedores são campos de nome idêntico de diferentes classes.  
  
|Identificador do cliente|Identificador do provedor|Tipo de argumentos de evento|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>
## <a name="ui-automation-event-arguments"></a>Argumentos de eventos de automação de ui  
 As classes a seguir encapsulam argumentos de eventos.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Contém informações sobre o carregamento assíncrono de conteúdo, incluindo a porcentagem de carregamento concluído.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Contém informações sobre um evento simples que não requer dados extras.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Contém informações sobre uma mudança no foco de entrada de um elemento para outro. Eventos desse tipo são levantados pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistema, não por provedores.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Contém informações sobre uma alteração no valor de uma propriedade de um elemento ou padrão de controle.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Contém informações sobre uma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mudança na árvore.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Contém informações sobre o fechamento de uma janela.|  
  
 Todas as aulas de <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> argumento de evento contêm um membro. Este identificador é encapsulado em um <xref:System.Windows.Automation.AutomationEvent>.  
  
 Os <xref:System.Windows.Automation.AutomationEvent> objetos utilizados para identificar eventos <xref:System.Windows.Automation.AutomationElementIdentifiers> são obtidos por provedores de campos em e classes identificadoras de padrões de controle, tais como <xref:System.Windows.Automation.DockPatternIdentifiers>. Os campos equivalentes são obtidos por <xref:System.Windows.Automation.AutomationElement> aplicativos cliente saem de campos e classes de padrão de controle, tais como <xref:System.Windows.Automation.DockPattern>.  
  
 Para obter uma lista de identificadores de eventos, consulte Eventos de Automação de [Interface do Usuário para Clientes](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Confira também

- [Automação de Eventos de Interface de Usuário para Clientes.](ui-automation-events-for-clients.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](server-side-ui-automation-provider-implementation.md)
- [Assinar eventos de automação de interface do usuário](subscribe-to-ui-automation-events.md)
