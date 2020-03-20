---
title: Mapeamento de Padrão de Controles para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 689e649343c93d0670c6870098a09f61097f4fb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180234"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapeamento de Padrão de Controles para Clientes de Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico lista os tipos de controle e seus padrões de controle associados.  
  
 A tabela a seguir organiza os padrões de controle nas seguintes categorias:  
  
-  Com suporte. O controle deve suportar este padrão de controle.  
  
- Suporte condicional. O controle pode suportar este padrão de controle dependendo do estado do controle.  
  
- Sem suporte. O controle não suporta esse padrão de controle; controles personalizados podem suportar esse padrão de controle.  
  
> [!NOTE]
> Alguns controles têm suporte condicional para vários padrões de controle, dependendo da funcionalidade do controle. Por exemplo, o controle do item <xref:System.Windows.Automation.InvokePattern>do <xref:System.Windows.Automation.ExpandCollapsePattern> <xref:System.Windows.Automation.TogglePattern>menu <xref:System.Windows.Automation.SelectionItemPattern> tem suporte condicional para o padrão de controle, dependendo de sua função no controle do menu.  
  
<a name="control_mapping_clients"></a>
## <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU  
  
|Tipo de controle|Com suporte|Suporte Condicional|Sem suporte|  
|------------------|---------------|-------------------------|-------------------|  
|Botão|Nenhum|Invocar, Alternar, Expandir o Colapso|Nenhum|  
|Calendário|Grade, Tabela|Seleção, Pergaminho|Valor|  
|Caixa de seleção|Ativar/Desativar|Nenhum|Nenhum|  
|Caixa de Combinação|Expandir o colapso|Seleção, Valor|Rolar|  
|Grade de dados|Grade|Pergaminho, Seleção, Tabela|Nenhum|  
|Item de Dados|Item de Seleção|Expandir o colapso, o item da grade, o item do pergaminho, a tabela, o alterne, o valor|Nenhum|  
|Document|Texto|Pergaminho, Valor|Nenhum|  
|Editar|Nenhum|Texto, Valor de Intervalo, Valor|Nenhum|  
|Agrupar|Nenhum|Expandir o colapso|Nenhum|  
|Cabeçalho|Nenhum|Transformar|Nenhum|  
|Item de Cabeçalho|Nenhum|Transforme, Invoque|Nenhum|  
|Hyperlink|Invoke|Valor|Nenhum|  
|Imagem|Nenhum|Item da grade, item de tabela|Invocar, Item de Seleção|  
|Lista|Nenhum|Grade, visão múltipla, pergaminho, seleção|Tabela|  
|Item de lista|Item de Seleção|Expandir o colapso, o item da grade, invocar, rolar item, alternar, valorizar|Nenhum|  
|Menu|Nenhum|Nenhum|Nenhum|  
|Barra de menu|Nenhum|Expandir o colapso, doca, transformar|Nenhum|  
|Item de menu|Nenhum|Expandir o colapso, invocar, o item de seleção, alternar|Nenhum|  
|Painel|Nenhum|Doca. Rolar, Transformar|Janela|  
|Barra de Andamento|Nenhum|Valor de intervalo, valor|Nenhum|  
|Botão de Opção|Item de Seleção|Nenhum|Ativar/Desativar|  
|Barra de Rolagem|Nenhum|Valor de Intervalo|Rolar|  
|Separador|Nenhum|Nenhum|Nenhum|  
|Controle deslizante|Nenhum|Valor de intervalo, seleção, valor|Nenhum|  
|Controle giratório|Nenhum|Valor de intervalo, seleção, valor|Nenhum|  
|Botão de Divisão|Invocar, Expandir o Colapso|Nenhum|Nenhum|  
|Barra de Status|Nenhum|Grade|Nenhum|  
|Tab|Seleção|Rolar|Nenhum|  
|Item da Guia|Item de Seleção|Nenhum|Invoke|  
|Tabela|Grade, Item da Grade, Tabela, Item de Tabela|Nenhum|Nenhum|  
|Texto|Nenhum|Item da grade, item da tabela, texto|Valor|  
|Posição|Transformar|Nenhum|Nenhum|  
|Barra de Título|Nenhum|Nenhum|Nenhum|  
|Barra de ferramentas|Nenhum|Doca, expanda o colapso, transforme|Nenhum|  
|Dica da ferramenta|Nenhum|Texto, janela|Nenhum|  
|Árvore|Nenhum|Pergaminho, Seleção|Nenhum|  
|Item de Árvore|Expandir o colapso|Invocar, Rolar Item, Item de Seleção, Alternar|Nenhum|  
|Janela|Transformar, Janela|Encaixar|Nenhum|  
  
> [!NOTE]
> Se um tipo de controle não tiver padrões de controle suportados listados, mas tiver um ou mais padrões de controle condicionalmente suportados, então um desses padrões de controle condicional será suportado em todos os momentos.  
  
## <a name="see-also"></a>Confira também

- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
