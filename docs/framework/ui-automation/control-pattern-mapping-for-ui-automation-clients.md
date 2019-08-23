---
title: Mapeamento de Padrão de Controles para Clientes de Automação de IU
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 64c3dccac61ceb2934904c5d03fc96d961976d6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932622"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapeamento de Padrão de Controles para Clientes de Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico lista os tipos de controle e seus padrões de controle associados.  
  
 A tabela a seguir organiza os padrões de controle nas seguintes categorias:  
  
- Com suporte. O controle deve dar suporte a esse padrão de controle.  
  
- Suporte condicional. O controle pode dar suporte a esse padrão de controle dependendo do estado do controle.  
  
- Não compatível. O controle não oferece suporte a este padrão de controle; os controles personalizados podem dar suporte a esse padrão de controle.  
  
> [!NOTE]
> Alguns controles têm suporte condicional para vários padrões de controle, dependendo da funcionalidade do controle. Por exemplo, o controle de item de menu tem suporte condicional <xref:System.Windows.Automation.InvokePattern>para o <xref:System.Windows.Automation.TogglePattern>padrão de <xref:System.Windows.Automation.SelectionItemPattern> controle, <xref:System.Windows.Automation.ExpandCollapsePattern>, ou, dependendo de sua função no controle de menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Padrões de Controle para Clientes de Automação de IU  
  
|Tipo de controle|Com suporte|Suporte condicional|Sem suporte|  
|------------------|---------------|-------------------------|-------------------|  
|Botão|Nenhum|Invocar, ativar/desativar, expandir recolher|Nenhum|  
|Calendário|Grade, tabela|Seleção, rolar|Valor|  
|Caixa de seleção|Ativar/Desativar|Nenhum|Nenhum|  
|Caixa de Combinação|Expandir recolher|Seleção, valor|Rolar|  
|Grade de Dados|Grade|Rolar, selecionar, tabela|Nenhum|  
|Item de Dados|Item de Seleção|Expandir recolhimento, item de grade, item de rolagem, tabela, alternância, valor|Nenhum|  
|Documento|Texto|Rolar, valor|Nenhum|  
|Editar|Nenhum|Texto, valor do intervalo, valor|Nenhum|  
|Grupo|Nenhum|Expandir recolher|Nenhum|  
|Cabeçalho|Nenhum|Transformar|Nenhum|  
|Item de Cabeçalho|Nenhum|Transformar, invocar|Nenhum|  
|Hiperlink|Chamar|Valor|Nenhum|  
|Image|Nenhum|Item de grade, item de tabela|Invocar, item de seleção|  
|Lista|Nenhum|Grade, exibição múltipla, rolagem, seleção|Tabela|  
|Item de lista|Item de Seleção|Expandir recolhimento, item de grade, invocar, rolar item, alternar, valor|Nenhum|  
|Menu|Nenhum|Nenhum|Nenhum|  
|Barra de Menus|Nenhum|Expandir recolher, encaixar, transformar|Nenhum|  
|Item de menu|Nenhum|Expandir recolher, invocar, selecionar item, alternar|Nenhum|  
|Painel|Nenhum|Ancorá. Rolar, transformar|Janela|  
|Barra de Andamento|Nenhum|Valor do intervalo, valor|Nenhum|  
|Botão de Opção|Item de Seleção|Nenhum|Ativar/Desativar|  
|Barra de Rolagem|Nenhum|Valor de Intervalo|Rolar|  
|Separador|Nenhum|Nenhum|Nenhum|  
|Controle deslizante|Nenhum|Valor de intervalo, seleção, valor|Nenhum|  
|Controle giratório|Nenhum|Valor de intervalo, seleção, valor|Nenhum|  
|Botão de Divisão|Invocar, expandir recolher|Nenhum|Nenhum|  
|Barra de Status|Nenhum|Grade|Nenhum|  
|Tabulação|Seleção|Rolar|Nenhum|  
|Item da Guia|Item de Seleção|Nenhum|Chamar|  
|Tabela|Grade, item de grade, tabela, item de tabela|Nenhum|Nenhum|  
|Texto|Nenhum|Item de grade, item de tabela, texto|Valor|  
|Posição|Transformar|Nenhum|Nenhum|  
|Barra de Título|Nenhum|Nenhum|Nenhum|  
|Barra de ferramentas|Nenhum|Encaixar, expandir, recolher, transformar|Nenhum|  
|Dica de ferramenta|Nenhum|Texto, janela|Nenhum|  
|Árvore|Nenhum|Rolar, seleção|Nenhum|  
|Item de Árvore|Expandir recolher|Invocar, rolar item, item de seleção, alternar|Nenhum|  
|Janela|Transformação, janela|Encaixar|Nenhum|  
  
> [!NOTE]
> Se um tipo de controle não tiver padrões de controle com suporte listados, mas tiver um ou mais padrões de controle com suporte condicionalmente, um desses padrões de controle condicional terá suporte em todos os momentos.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
