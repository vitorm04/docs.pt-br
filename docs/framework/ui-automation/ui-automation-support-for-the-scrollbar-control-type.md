---
title: Suporte de automação de interface de usuário para o tipo de controle ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll Bar control type
- control types, Scroll Bar
- Scroll Bar control type
ms.assetid: 329891d7-b609-49e6-920a-09ea8a627d07
ms.openlocfilehash: 88a606369103e989b41ecf3569d54247cf3f83fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179624"
---
# <a name="ui-automation-support-for-the-scrollbar-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle ScrollBar
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle ScrollBar. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura das árvores, valores de propriedade e padrões de controle.  
  
 Os controles da barra de rolagem permitem que o usuário role o conteúdo dentro de uma janela ou contêiner de itens. O controle é composto por um conjunto de botões e um controle de polegar.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle ScrollBar. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de lista, se , Win32 ou Formulários windows.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a exibição de conteúdo da árvore que diz respeito aos controles da barra de rolagem e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte [Visão geral da árvore de automação de ui](ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|ScrollBar<br /><br /> - Botão (2 ou 4)<br />- Polegar (0 ou 1)|Não aplicável. O controle da barra de rolagem não contém conteúdo.|  
  
 O controle da barra de rolagem sempre tem três a cinco filhos. Como a subárvore tem mais de um controle <xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty> de botão, você deve definir um valor específico para cada item para torná-los descobertos para ferramentas de automação de teste.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista as propriedades cujo valor ou definição é especialmente relevante para os controles da barra de rolagem. Observe que um controle de barra de rolagem nunca tem conteúdo; sua funcionalidade é exposta através do padrão de controle Scroll, que é suportado no contêiner que está sendo rolado.  
  
 Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Veja as notas.|Se o controle puder receber foco no teclado, ele deve suportar esta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|`Null`|O controle da barra de rolagem não tem elementos de conteúdo e não `NameProperty` é necessário definir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Não é um número.|O controle da barra de rolagem não tem pontos clicáveis.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|As barras de rolagem não possuem etiquetas.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ScrollBar|Este valor é o mesmo para todos os quadros. As barras de rolagem que funcionam como controles deslizantes devem usar o tipo de controle Slider.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Barra de rolagem"|String localizada que corresponde ao tipo de controle Button.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Falso|O controle da barra de rolagem nunca é um elemento de conteúdo. Se a barra de rolagem for um controle autônomo, ela `ControlType.Slider` deve `ControlType` cumprir o tipo de controle Slider e retornar para a propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|A barra de rolagem deve ser sempre um controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|True|O controle da barra de rolagem deve sempre expor sua orientação horizontal ou vertical.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os padrões de controle necessários para serem suportados pelos controles da barra de rolagem. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md). Observe que quando uma barra de rolagem é usada como um controle apenas para manipulação do mouse, ela não suporta padrões de controle. Se for usado como controle deslizante dentro de um aplicativo, deve ser dado o tipo de controle Slider.  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Never|O padrão de controle Scroll nunca é suportado diretamente na barra de rolagem.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Depende|Essa funcionalidade só deve ser suportada se o padrão de controle Scroll não for suportado no recipiente que tem a barra de rolagem.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles da barra de rolagem. Para obter mais informações sobre eventos, consulte [Visão geral de eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte/Valor|Observações|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>evento alterado de propriedade.|Never|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>evento alterado de propriedade.|Never|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>evento alterado de propriedade.|Never|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>evento alterado de propriedade.|Never|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>evento alterado de propriedade.|Never|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>evento alterado de propriedade.|Never|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.ScrollBar>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
