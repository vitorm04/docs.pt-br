---
title: "Mapeamento de Padrão de Controles para Clientes de Automação de IU"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
caps.latest.revision: "18"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6a5f9d115c601775cc4f5b1c61d71d739f7a405b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapeamento de Padrão de Controles para Clientes de Automação de IU
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico lista os tipos de controle e seus padrões de controle associado.  
  
 A tabela a seguir organiza os padrões de controle nas seguintes categorias:  
  
-   Com suporte. O controle deve oferecer suporte a esse padrão de controle.  
  
-   Suporte condicional. O controle pode suportar esse padrão de controle dependendo do estado do controle.  
  
-   Sem suporte. O controle não oferece suporte a esse padrão de controle; controles personalizados podem dar suporte a esse padrão de controle.  
  
> [!NOTE]
>  Alguns controles têm suporte condicional para diversos padrões de controle, dependendo da funcionalidade do controle. Por exemplo, o controle de item de menu tem suporte condicional para o <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, ou <xref:System.Windows.Automation.SelectionItemPattern> padrão de controle, dependendo de sua função no controle do menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU  
  
|Tipo de controle|Com suporte|Suporte condicional|Sem suporte|  
|------------------|---------------|-------------------------|-------------------|  
|Botão|Nenhum|Invocação de alternância, expanda recolher|Nenhum|  
|Calendário|Grade de tabela|Seleção de rolagem|Valor|  
|Caixa de seleção|Ativar/Desativar|Nenhum|Nenhum|  
|Caixa de Combinação|Expanda recolher|Seleção de valor|Rolar|  
|Grade de Dados|Grade|Tabela de rolagem, seleção,|Nenhum|  
|Item de Dados|Item de Seleção|Expanda recolher, Item de grade, o Item de rolagem, tabela, alternância, valor|Nenhum|  
|Documento|Texto|Rolagem, valor|Nenhum|  
|Editar|Nenhum|Valor de texto, o valor de intervalo|Nenhum|  
|Grupo|Nenhum|Expanda recolher|Nenhum|  
|Cabeçalho|Nenhum|Transformar|Nenhum|  
|Item de Cabeçalho|Nenhum|Transformar, invoque|Nenhum|  
|Hiperlink|Chamar|Valor|Nenhum|  
|Image|Nenhum|Item da grade, o Item de tabela|Invocar a seleção de Item|  
|Lista|Nenhum|Rolagem de grade, exibição de várias, seleção|Tabela|  
|Item de lista|Item de Seleção|Expanda o recolhimento de Item da grade, invocar, role a tela de Item, alternar, valor|Nenhum|  
|Menu|Nenhum|Nenhum|Nenhum|  
|Barra de Menus|Nenhum|Expanda a transformação de recolher, encaixe,|Nenhum|  
|Item de menu|Nenhum|Expanda recolher, invocar, Item de seleção Ativar/desativar|Nenhum|  
|Painel|Nenhum|Encaixe. Role, transformar|Janela|  
|Barra de Andamento|Nenhum|Valor de intervalo e valor|Nenhum|  
|Botão de Opção|Item de Seleção|Nenhum|Ativar/Desativar|  
|Barra de Rolagem|Nenhum|Valor de Intervalo|Rolar|  
|Separador|Nenhum|Nenhum|Nenhum|  
|Controle deslizante|Nenhum|Valor, a seleção, o valor de intervalo|Nenhum|  
|Controle giratório|Nenhum|Valor, a seleção, o valor de intervalo|Nenhum|  
|Botão de Divisão|Invocar, expanda recolher|Nenhum|Nenhum|  
|Barra de Status|Nenhum|Grade|Nenhum|  
|Tabulação|Seleção|Rolar|Nenhum|  
|Item da Guia|Item de Seleção|Nenhum|Chamar|  
|Tabela|Grade de Item da grade, tabela, o Item de tabela|Nenhum|Nenhum|  
|Texto|Nenhum|Texto do Item, o Item de tabela de grade|Valor|  
|Posição|Transformar|Nenhum|Nenhum|  
|Barra de Título|Nenhum|Nenhum|Nenhum|  
|Barra de ferramentas|Nenhum|Encaixar, expanda o recolhimento de transformação|Nenhum|  
|Dica de ferramenta|Nenhum|Texto, janela|Nenhum|  
|Árvore|Nenhum|Rolagem, seleção|Nenhum|  
|Item de Árvore|Expanda recolher|Invocar, Item de rolagem, seleção de Item, alternar|Nenhum|  
|Janela|Transformação de janela|Encaixar|Nenhum|  
  
> [!NOTE]
>  Se um tipo de controle não tiver nenhum padrão de controle com suporte listado mas tem um ou mais padrões de controle condicionalmente suportados, então um desses padrões de controle terão suporte em todos os tempos.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
