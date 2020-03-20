---
title: Suporte de Automação de Interface de Usuário para o Tipo de Controle Button
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
ms.openlocfilehash: e98e027559be8c3e8ccdb4ac4369c09fd13805e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179841"
---
# <a name="ui-automation-support-for-the-button-control-type"></a>Suporte de Automação de Interface de Usuário para o Tipo de Controle Button
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle Button. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] das árvores, valores de propriedade, padrões de controle e eventos.  
  
 Um botão é um objeto com o qual um usuário interage para executar uma ação como os botões **OK** e **Cancel** em uma caixa de diálogo. O controle de botão é um controle simples de expor porque ele mapeia para um único comando que o usuário deseja completar.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle Button. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de botão, se , Win32 ou Formulários windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a visão de conteúdo da árvore que diz respeito aos controles de botão e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte Visão geral da [árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Botão<br /><br /> - Imagem (0 ou mais)<br />- Texto (0 ou mais)|Botão|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para os controles que implementam o tipo de controle Button (como controles de botão). Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|Veja as notas.|O controle Button normalmente deve suportar uma chave do acelerador para permitir que um usuário final execute a ação que representa rapidamente a partir do teclado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|Suportado se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis, e você realizar testes especializados de acerto, então anular e fornecer um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Botão|Este valor é o mesmo para todas as estruturas de IA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Veja as notas.|O Texto de Ajuda pode indicar qual será o resultado final da ativação do botão. Este é tipicamente o mesmo tipo de informação apresentada através de uma Dica de Ferramenta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|O controle button deve estar sempre satisfeito.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O controle button deve ser sempre um controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Veja as notas.|Se o controle puder receber foco no teclado, ele deve suportar esta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Os controles de botão são auto-rotulados pelo seu conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Botão"|Cadeia localizada correspondente ao tipo de controle Button.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O nome do controle de botão é o texto que é usado para rotulá-lo. Sempre que uma imagem é usada para rotular um botão, o texto alternativo deve ser fornecido para a propriedade Nome do botão.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados por todos os controles de botão. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Veja as notas.|Todos os botões devem suportar o padrão de controle Invocar ou o padrão de controle Alternar. Invocar é suportado quando o botão executa um comando a pedido do usuário. Este comando mapeia para uma única operação, como Cortar, Copiar, Colar ou Excluir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Veja as notas.|Todos os botões devem suportar o padrão de controle Invocar ou o padrão de controle Alternar. O alternador é suportado se o botão puder ser pedalado através de uma série de até três estados. Normalmente, isso é visto como um interruptor de liga/desliga para recursos específicos.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Veja as notas.|Quando um botão é hospedado como filho de um botão split, o botão criança pode suportar o padrão ExpandCollapse em vez do padrão Invocar ou Alternar. O padrão ExpandCollapse pode ser usado para abrir ou fechar um menu ou outra subestrutura associada ao elemento do botão.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de botão. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Se o controle suportar o padrão de controle Invocar, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão de controle Alternar, ele deve suportar este evento.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.Button>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
