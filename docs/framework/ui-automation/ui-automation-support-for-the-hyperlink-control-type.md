---
title: Suporte de automação de interface de usuário para o Tipo de Controle Hyperlink
ms.date: 03/30/2017
helpviewer_keywords:
- Hyperlink control type
- UI Automation, Hyperlink control type
- control types, Hyperlink
ms.assetid: 110cceea-5932-4955-a1a6-13afc51422b2
ms.openlocfilehash: ebcc2d143b9ed4b01b2b8044b8a52fe192750e42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179732"
---
# <a name="ui-automation-support-for-the-hyperlink-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Hyperlink
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle Hyperlink. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura das árvores, valores de propriedade e padrões de controle.  
  
 Os controles de hiperlink permitem que um usuário navegue dentro de uma página, de uma página para outra, e abra janelas.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle Hyperlink. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de hiperlink, sejam os Formulários Win32 ou Windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a visão [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a visão de conteúdo da árvore que diz respeito aos controles de hiperlinks e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte Visão geral da [árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Hyperlink|Hyperlink|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para o tipo de controle Hyperlink. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|Suportado se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis, e você realizar testes especializados de acerto, então anular e fornecer um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Veja as notas.|Se o controle puder receber foco no teclado, ele deve suportar esta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O nome do controle de hiperlink é o texto exibido na tela como sublinhado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|O ponto clicável do controle de hiperlink deve ser um ponto que inicia o hiperlink se clicado com um ponteiro do mouse.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Veja as notas.|Se houver um rótulo de texto estático, então esta propriedade deve expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Hyperlink|Este valor é o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mesmo para todos os quadros.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"hiperlink"|Cadeia localizada correspondente ao tipo de controle Hyperlink.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|O controle de hiperlink está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visualização de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O controle de hiperlink está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visão de controle da árvore.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Padrões e propriedades de controle de automação de ida e clara necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados por todos os controles de hiperlink. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Propriedade de padrão/padrão de controle|Suporte/Valor|Observações|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Sim|Todos os controles de hiperlink devem suportar o padrão Invocar.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Depende|Os controles de hiperlink devem suportar o padrão de controle Valor quando o link contiver informações utilizáveis e significativas para o usuário.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value>|Por exemplo, `"https://www...."`|Uma URL para um endereço internet ou intranet é um exemplo de um hiperlink que contém informações que são significativas para o usuário. Um link programático, no entanto, é significativo apenas para uma aplicação e não é recomendado para a propriedade Valor.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de hiperlink. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.Hyperlink>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
