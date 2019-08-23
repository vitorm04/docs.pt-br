---
title: Suporte de automação de interface do usuário para o tipo de controle Spinner
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
ms.openlocfilehash: c32fcffcbe360fc9158725b3eac2558377639abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954672"
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Suporte de automação de interface do usuário para o tipo de controle Spinner
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o suporte para o tipo de controle Spinner. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar a <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , valores de propriedade e padrões de controle.  
  
 Os controles Spinner são usados para selecionar de um domínio de itens ou um intervalo de números.  
  
 As seções a seguir definem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a estrutura de árvore, as propriedades, os padrões de controle e os eventos necessários para o tipo de controle Spinner. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Spinner [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], se [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], ou.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária  
 A tabela a seguir descreve a exibição de controle e a exibição de conteúdo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore que pertence aos controles Spinner quando eles dão suporte aos padrões de controle de valor de intervalo, valor e seleção e descreve o que pode ser contido em cada exibição. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a árvore, consulte [visão geral da árvore de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 **Valor de intervalo ou padrão de controle de valor**  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Controle giratório<br /><br /> -Editar (0 ou 1)<br />-Botão (2)|Controle giratório|  
  
 **Padrão de controle de seleção**  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Controle giratório<br /><br /> -Editar (0 ou 1)<br />-Botão (2)<br />-Item de lista (0 ou mais)|Controle giratório<br /><br /> -ListItem (0 ou mais)|  
  
 Para garantir que os dois botões na subárvore de exibição de controle possam ser diferenciados por ferramentas de teste `SmallIncrement` automatizadas, atribua o ou `SmallDecrement` `AutomationId` conforme apropriado. Para algumas implementações, o controle de edição associado pode ser um par do controle Spinner.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias  
 A tabela a seguir lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] as propriedades cujo valor ou definição é especialmente relevante para controles Spinner. Para obter mais informações [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sobre propriedades, consulte [Propriedades de automação da interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|O ponto clicável do controle Spinner dá enfoque à parte de edição do controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte observações.|O controle Spinner normalmente obtém seu nome de um rótulo de texto estático.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte observações.|Os controles Spinner têm um rótulo de texto estático.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Controle giratório|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|controle|Cadeia de caracteres localizada correspondente ao tipo de controle Spinner.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle Spinner sempre deve ser conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle Spinner sempre deve ser um controle.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Propriedades e padrões de controle de automação da interface do usuário necessários  
 A tabela a seguir lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os padrões de controle necessários para serem suportados pelos controles Spinner. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Propriedade padrão de controle/padrão|Suporte/valor|Observações|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Dependem|Os controles Spinner que têm uma lista de itens a serem selecionados devem dar suporte a esse padrão.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Os controles Spinner são sempre contêineres de seleção única.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Dependem|Os controles Spinner que abrangem um intervalo numérico podem dar suporte a esse padrão.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Dependem|Controles Spinner que abrangem um conjunto discreto de opções ou números podem dar suporte a esse padrão.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários  
 A tabela a seguir lista [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os eventos necessários para serem suportados por todos os controles Spinner. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Circunstância|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Dependem|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType.Spinner>
- [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
