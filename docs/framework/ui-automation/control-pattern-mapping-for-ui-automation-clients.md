---
title: Mapeamento de Padrão de Controles para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 48298cb8d89958c701d7150aeb497e82d565bde1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433864"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapeamento de Padrão de Controles para Clientes de Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 This topic lists control types and their associated control patterns.  
  
 The following table organizes the control patterns into the following categories:  
  
- Com suporte. The control must support this control pattern.  
  
- Conditional support. The control may support this control pattern depending on the state of the control.  
  
- Não há suporte. The control does not support this control pattern; custom controls may support this control pattern.  
  
> [!NOTE]
> Some controls have conditional support for several control patterns depending on the functionality of the control. For example, the menu item control has conditional support for the <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, or <xref:System.Windows.Automation.SelectionItemPattern> control pattern, depending on its function in the menu control.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU  
  
|Tipo de controle|Com suporte|Conditional Support|Sem suporte|  
|------------------|---------------|-------------------------|-------------------|  
|Botão|Nenhum|Invoke, Toggle, Expand Collapse|Nenhum|  
|Calendário|Grid, Table|Selection, Scroll|Valor|  
|Check Box|Ativar/Desativar|Nenhum|Nenhum|  
|Caixa de Combinação|Expand Collapse|Selection, Value|Rolar|  
|Grade de Dados|Grade|Scroll, Selection, Table|Nenhum|  
|Item de Dados|Item de Seleção|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|Nenhum|  
|Documento|Texto|Scroll, Value|Nenhum|  
|Editar|Nenhum|Text, Range Value, Value|Nenhum|  
|Grupo|Nenhum|Expand Collapse|Nenhum|  
|Cabeçalho|Nenhum|Transformar|Nenhum|  
|Item de Cabeçalho|Nenhum|Transform, Invoke|Nenhum|  
|Hiperlink|Chamar|Valor|Nenhum|  
|Image|Nenhum|Grid Item, Table Item|Invoke, Selection Item|  
|Lista|Nenhum|Grid, Multiple View, Scroll, Selection|Tabela|  
|List Item|Item de Seleção|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|Nenhum|  
|Menu|Nenhum|Nenhum|Nenhum|  
|Barra de Menus|Nenhum|Expand Collapse, Dock, Transform|Nenhum|  
|Item de menu|Nenhum|Expand Collapse, Invoke, Selection Item, Toggle|Nenhum|  
|Painel|Nenhum|Dock. Scroll, Transform|Janela|  
|Barra de Andamento|Nenhum|Range Value, Value|Nenhum|  
|Botão de Opção|Item de Seleção|Nenhum|Ativar/Desativar|  
|Barra de Rolagem|Nenhum|Valor de Intervalo|Rolar|  
|Separador|Nenhum|Nenhum|Nenhum|  
|Controle deslizante|Nenhum|Range Value, Selection, Value|Nenhum|  
|Controle giratório|Nenhum|Range Value, Selection, Value|Nenhum|  
|Botão de Divisão|Invoke, Expand Collapse|Nenhum|Nenhum|  
|Barra de Status|Nenhum|Grade|Nenhum|  
|Tabulação|Seleção|Rolar|Nenhum|  
|Item da Guia|Item de Seleção|Nenhum|Chamar|  
|Tabela|Grid, Grid Item, Table, Table Item|Nenhum|Nenhum|  
|Texto|Nenhum|Grid Item, Table Item, Text|Valor|  
|Posição|Transformar|Nenhum|Nenhum|  
|Barra de Título|Nenhum|Nenhum|Nenhum|  
|Tool Bar|Nenhum|Dock, Expand Collapse, Transform|Nenhum|  
|Tool Tip|Nenhum|Text, Window|Nenhum|  
|Árvore|Nenhum|Scroll, Selection|Nenhum|  
|Item de Árvore|Expand Collapse|Invoke, Scroll Item, Selection Item, Toggle|Nenhum|  
|Janela|Transform, Window|Encaixar|Nenhum|  
  
> [!NOTE]
> If a control type has no supported control patterns listed but has one or more conditionally-supported control patterns, then one of those conditional control patterns will be supported at all times.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
