---
title: Mapeamento de Padrão de Controles para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 78274e2a5597291adcdafccf759b826f54a264ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647193"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapeamento de Padrão de Controles para Clientes de Automação de IU
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico lista os tipos de controle e seus padrões de controle associado.  
  
 A tabela a seguir organiza os padrões de controle nas seguintes categorias:  
  
- Com suporte. O controle deve oferecer suporte a esse padrão de controle.  
  
- Suporte condicional. O controle pode dar suporte a esse padrão de controle dependendo do estado do controle.  
  
- Sem suporte. O controle não dá suporte a esse padrão de controle; controles personalizados podem dar suporte a esse padrão de controle.  
  
> [!NOTE]
>  Alguns controles têm suporte condicional para vários padrões de controle, dependendo da funcionalidade do controle. Por exemplo, o controle de item de menu tem suporte condicional para o <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, ou <xref:System.Windows.Automation.SelectionItemPattern> padrão de controle, dependendo da sua função no controle do menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU  
  
|Tipo de controle|Com suporte|Suporte condicional|Sem suporte|  
|------------------|---------------|-------------------------|-------------------|  
|Botão|Nenhum|Invocar, ativar/desativar, expandir e recolher|Nenhum|  
|Calendário|Grade de tabela|Seleção de rolagem|Valor|  
|Caixa de seleção|Ativar/Desativar|Nenhum|Nenhum|  
|Caixa de Combinação|Expandir e recolher|Seleção de valor|Rolar|  
|Grade de Dados|Grade|Tabela de rolagem, seleção,|Nenhum|  
|Item de Dados|Item de Seleção|Expandir recolher, Item de grade, Item de rolagem, tabela, ativar/desativar, valor|Nenhum|  
|Documento|Texto|Rolagem, o valor|Nenhum|  
|Editar|Nenhum|Valor de texto, o valor de intervalo|Nenhum|  
|Grupo|Nenhum|Expandir e recolher|Nenhum|  
|Cabeçalho|Nenhum|Transformar|Nenhum|  
|Item de Cabeçalho|Nenhum|Transform, Invoke|Nenhum|  
|Hiperlink|Chamar|Valor|Nenhum|  
|Image|Nenhum|Item de grade, o Item de tabela|Invocar o Item de seleção|  
|Lista|Nenhum|Rolagem da grade, exibição de várias, seleção|Tabela|  
|Item de lista|Item de Seleção|Expandir e recolher, Item de grade, invocar, role para o Item, alternar, valor|Nenhum|  
|Menu|Nenhum|Nenhum|Nenhum|  
|Barra de Menus|Nenhum|Expandir recolher, encaixe, transformação|Nenhum|  
|Item de menu|Nenhum|Expandir e recolher, invocar, Item de seleção Ativar/desativar|Nenhum|  
|Painel|Nenhum|Encaixe. Role, transformar|Janela|  
|Barra de Andamento|Nenhum|Valor de intervalo de valor|Nenhum|  
|Botão de Opção|Item de Seleção|Nenhum|Ativar/Desativar|  
|Barra de Rolagem|Nenhum|Valor de Intervalo|Rolar|  
|Separador|Nenhum|Nenhum|Nenhum|  
|Controle deslizante|Nenhum|Valor, seleção, o valor de intervalo|Nenhum|  
|Controle giratório|Nenhum|Valor, seleção, o valor de intervalo|Nenhum|  
|Botão de Divisão|Invocar, expandir e recolher|Nenhum|Nenhum|  
|Barra de Status|Nenhum|Grade|Nenhum|  
|Tabulação|Seleção|Rolar|Nenhum|  
|Item da Guia|Item de Seleção|Nenhum|Chamar|  
|Tabela|Grade de Item de grade, tabela, o Item de tabela|Nenhum|Nenhum|  
|Texto|Nenhum|Texto do Item, o Item de tabela de grade|Valor|  
|Posição|Transformar|Nenhum|Nenhum|  
|Barra de Título|Nenhum|Nenhum|Nenhum|  
|Barra de ferramentas|Nenhum|Encaixar, expandir e recolher, transformar|Nenhum|  
|Dica de ferramenta|Nenhum|Texto, a janela|Nenhum|  
|Árvore|Nenhum|Rolagem, seleção|Nenhum|  
|Item de Árvore|Expandir e recolher|Invocar, Item de rolagem, Item de seleção Ativar/desativar|Nenhum|  
|Janela|Transformação de janela|Encaixar|Nenhum|  
  
> [!NOTE]
>  Se um tipo de controle não tem nenhum padrão de controle com suporte listado, mas tem um ou mais padrões de controle tem suporte condicionalmente, em seguida, um desses padrões de controle condicional terão suporte em todos os tempos.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
