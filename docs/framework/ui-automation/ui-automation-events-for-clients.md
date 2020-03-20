---
title: Automação de Eventos de Interface de Usuário para Clientes.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: d7105e9211c35e7d6125c3017e8b4b829a25b128
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179903"
---
# <a name="ui-automation-events-for-clients"></a>Automação de Eventos de Interface de Usuário para Clientes.
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico descreve [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] como os eventos são usados pelos clientes da UI Automation.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]permite que os clientes se inscrevam em eventos de interesse. Essa capacidade melhora o desempenho eliminando a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] necessidade de pesquisa contínua de todos os elementos do sistema para ver se alguma informação, estrutura ou estado mudou.  
  
 A eficiência também é melhorada pela capacidade de ouvir eventos apenas dentro de um escopo definido. Por exemplo, um cliente pode ouvir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos de mudança de foco em todos os elementos da árvore, ou em apenas um elemento e seus descendentes.  
  
> [!NOTE]
> Não assuma que todos os [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] eventos possíveis são levantados por um provedor. Por exemplo, nem todas as alterações de propriedade fazem com que os eventos sejam levantados pelos provedores de proxy padrão para os controles Windows Forms e Win32.  
  
 Para uma visão [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais ampla dos eventos, consulte Visão Geral de Eventos de [Automação de UI](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>Assinando eventos  
 Os aplicativos clientes assinam eventos de um tipo específico registrando um manipulador de eventos, usando um dos seguintes métodos.  
  
|Método|Tipo de evento|Tipo de argumentos de evento|Tipo de delegado|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Mudança de foco|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Alteração da propriedade|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Alteração de estrutura|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Todos os outros eventos, identificados por um<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> ou <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Antes de chamar o método, você deve criar um método de delegado para lidar com o evento. Se preferir, você pode lidar com diferentes tipos de eventos em um único método, e passar este método em várias chamadas para um dos métodos na tabela. Por exemplo, <xref:System.Windows.Automation.AutomationEventHandler> um único pode ser configurado para <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>lidar com vários eventos de forma diferente de acordo com o .  
  
> [!NOTE]
> Para processar eventos fechados por janela, lance o tipo <xref:System.Windows.Automation.WindowClosedEventArgs>de argumento que é passado para o manipulador de eventos como . Como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o elemento para a janela não é `sender` mais válido, você não pode usar o parâmetro para recuperar informações; usar <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> em vez disso.  
  
> [!CAUTION]
> Se sua aplicação pode receber [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]eventos por conta própria, não use o segmento do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] seu aplicativo para se inscrever em eventos ou para cancelar a inscrição. Fazer isso pode levar a um comportamento imprevisível. Para obter mais informações, consulte [Problemas de threading de automação de ui](ui-automation-threading-issues.md).  
  
 No desligamento ou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] quando os eventos não são mais de interesse para o aplicativo, os clientes de Automação de Interface do Usuário devem ligar para um dos seguintes métodos.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Desregistra um manipulador de eventos <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>que foi registrado usando .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Desregistra um manipulador de eventos <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>que foi registrado usando .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Desregistra um manipulador de eventos <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>que foi registrado usando .|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Não registra todos os manipuladores de eventos registrados.|  
  
 Por exemplo, código, consulte [Assinar eventos de automação de ui](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Confira também

- [Assinar eventos de automação de interface do usuário](subscribe-to-ui-automation-events.md)
- [Visão geral sobre eventos de automação de interface do usuário](ui-automation-events-overview.md)
- [Visão geral das propriedades de automação da interface do usuário](ui-automation-properties-overview.md)
- [Amostra trackfocus](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
