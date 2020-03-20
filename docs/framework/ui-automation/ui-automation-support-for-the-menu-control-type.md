---
title: Suporte de Automação de Interface de Usuário para o Tipo de Controle Menu
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: 3e3177f682ad75f4673870a72aee6d86c7b5ab60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179679"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>Suporte de Automação de Interface de Usuário para o Tipo de Controle Menu
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle menu. Descreve a estrutura da [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] árvore do controle e fornece as propriedades e padrões de controle para cenários de controle específicos.  
  
 Um controle de menu permite a organização hierárquica de elementos associados a comandos e manipuladores de eventos. Em um aplicativo típico do Microsoft Windows, uma barra de menu contém vários botões de menu (como **Arquivo,** **Edição**e **Janela),** e cada botão do menu exibe um menu. Um menu contém uma coleção de itens do menu (como **Novo**, **Abrir**e **Fechar),** que podem ser expandidos para exibir itens adicionais do menu ou para executar uma ação específica quando clicado.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle menu. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de lista, se , Win32 ou Formulários windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a exibição de conteúdo da árvore que diz respeito aos controles do menu e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte [Visão geral da árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Menu<br /><br /> - MenuItem (1 ou muitos)|Não aplicável (a menos que o controle do menu seja um menu de contexto que seja pai de um objeto que não seja um item do menu)<br /><br /> - MenuItem (1 ou muitos)|  
  
 Os controles do menu sempre aparecem na exibição de controle e na visualização de conteúdo da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. Os tipos de controle de menu devem aparecer sob o controle a que suas informações estão se referindo. Os clientes de `MenuOpenedEvent` Automação de Interface do Usuário devem ouvir para garantir que obtenham consistentemente informações transmitidas pelos controles de menu. Controles de menu de contexto são um caso especial. Eles aparecem como crianças da Área de Trabalho.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para o tipo de controle Menu. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Sem suporte|O controle do menu não requer que uma propriedade Name seja definida.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Nenhum rótulo é antecipado com um controle típico do menu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menu|Este valor é o mesmo para todas as estruturas de IA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Falso|O controle do menu não está [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visualização de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O controle do menu está sempre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] incluído na visão de controle da árvore.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 Não há padrões de controle necessários para o tipo de controle menu.  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 Os controles do `MenuOpenedEvent` menu devem aumentar quando aparecerem na tela. O `MenuOpenedEvent` texto do controle incluirá o texto. O `MenuClosedEvent` deve ser levantado quando um menu desaparece da tela.  
  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de menu. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte/Valor|Observações|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.Menu>
- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
