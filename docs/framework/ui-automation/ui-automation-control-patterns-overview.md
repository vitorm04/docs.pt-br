---
title: Visão Geral de Padrões de Controle de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: f62631a15dd348b6f6ea27a82d7b45aab92ceed2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179943"
---
# <a name="ui-automation-control-patterns-overview"></a>Visão Geral de Padrões de Controle de Automação de Interface de Usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] introduz padrões de controle. Os padrões de controle permitem categorizar e expor a funcionalidade de um controle independente do tipo ou da aparência do controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]usa padrões de controle para representar comportamentos comuns de controle. Por exemplo, você usa o padrão de controle Invocar para controles que podem ser invocados (como botões) e o padrão de controle Scroll para controles que têm barras de rolagem (como caixas de lista, exibições de lista ou caixas de combinação). Como cada padrão de controle representa uma funcionalidade separada, eles podem ser combinados para descrever o conjunto completo de funcionalidade suportada por um controle específico.  
  
> [!NOTE]
> Os controles agregados — construídos [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] com controles de crianças que fornecem a funcionalidade exposta pelo pai — devem implementar todos os padrões de controle normalmente associados ao controle de cada filho. Por sua vez, esses mesmos padrões de controle não são necessários para serem implementados pelos controles da criança.  
  
<a name="uiautomation_control_pattern_includes"></a>
## <a name="ui-automation-control-pattern-components"></a>Componentes de padrão de controle de automação de ui  
 Os padrões de controle suportam os métodos, propriedades, eventos e relacionamentos necessários para definir uma discreta peça de funcionalidade disponível em um controle.  
  
- A relação entre um elemento de Automação de UI e seus pais, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] filhos e irmãos descreve a estrutura do elemento dentro da árvore.  
  
- Os métodos permitem que os clientes de Automação de Interface do Usuário manipulem o controle.  
  
- As propriedades e eventos fornecem informações sobre a funcionalidade do padrão de controle, bem como informações sobre o estado do controle.  
  
 Os padrões [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de controle se relacionam com os objetos do Component Object Model (COM). No COM, você pode consultar um objeto para saber a quais interfaces ele dá suporte e usar essas interfaces para acessar a funcionalidade. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], UI Automation os clientes podem pedir um controle que padrões de controle suporta e, em seguida, interagir com o controle através das propriedades, métodos, eventos e estruturas expostas pelos padrões de controle suportados. Por exemplo, para uma caixa de edição <xref:System.Windows.Automation.Provider.IScrollProvider>multilinha, os provedores de automação de ui implementam . Quando um cliente <xref:System.Windows.Automation.AutomationElement> sabe que <xref:System.Windows.Automation.ScrollPattern> um suporta o padrão de controle, ele pode usar as propriedades, métodos e eventos expostos por esse padrão de controle para manipular o controle ou acessar informações sobre o controle.  
  
<a name="uiautomation_control_pattern_client_provider"></a>
## <a name="ui-automation-providers-and-clients"></a>Provedores e clientes de automação de interface do usuário  
 Os provedores de automação de ui implementam padrões de controle para expor o comportamento apropriado para uma peça específica de funcionalidade suportada pelo controle.  
  
 Os clientes de automação de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interface do usuário acessam [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]métodos e [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]propriedades de classes de padrões de controle e as usam para obter informações sobre o , ou para manipular o . Essas classes de padrão <xref:System.Windows.Automation> de controle são <xref:System.Windows.Automation.InvokePattern> encontradas no namespace (por exemplo, e <xref:System.Windows.Automation.SelectionPattern>).  
  
 Os <xref:System.Windows.Automation.AutomationElement> clientes usam <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> métodos (como ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) ou os acessórios de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tempo de execução de linguagem comum (CLR) para acessar as propriedades em um padrão. Cada classe de padrão de controle <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> tem <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>um membro de campo (por exemplo, ou <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ) que identifica <xref:System.Windows.Automation.AutomationElement>esse padrão de controle e pode ser passado como parâmetro para ou para recuperar esse padrão para um .  
  
<a name="uiautomation_control_patterns_dynamic"></a>
## <a name="dynamic-control-patterns"></a>Padrões de controle dinâmico  
 Alguns controles nem sempre suportam o mesmo conjunto de padrões de controle. Os padrões de controle são considerados suportados quando estão disponíveis para um cliente de Automação de UI. Por exemplo, uma caixa de edição multilinha permite rolagem vertical somente quando contém mais linhas de texto do que pode ser exibida em sua área visível. A rolagem é desativada quando o texto suficiente é removido para que a rolagem não seja mais necessária. Para este exemplo, o padrão de controle ScrollPattern é suportado dinamicamente dependendo do estado atual do controle (quanto texto está na caixa de edição).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>
## <a name="control-pattern-classes-and-interfaces"></a>Classes e interfaces de padrões de controle  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir descreve os padrões de controle. A tabela também lista as classes usadas pelos clientes de Automação de Interface para acessar os padrões de controle, bem como as interfaces usadas pelos provedores de Automação de Interface para implementá-los.  
  
|Classe padrão de controle|Interface do provedor|Descrição|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Usado para controles que podem ser encaixados em um contêiner. Por exemplo, barras de ferramentas ou paletas de ferramentas.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Usado para controles que podem ser expandidos ou colapsados. Por exemplo, itens de menu em um aplicativo, como o menu **Arquivo.**|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Usado para controles que dão suporte à funcionalidade de grade, como dimensionamento e transferência para uma célula especificada. Por exemplo, a grande visualização de ícones no Windows Explorer ou tabelas simples sem cabeçalhos no Microsoft Word.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Usado para controles que possuem células nas grades. As células individuais devem suportar o padrão GridItem. Por exemplo, cada célula no Microsoft Windows Explorer visualiza detalhes.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Usado para controles que podem ser invocados, como um botão.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Usado para controles que podem alternar entre várias representações do mesmo conjunto de informações, dados ou filhos. Por exemplo, um controle de exibição de lista onde os dados estão disponíveis em miniatura, azulejo, ícone, lista ou visualizações de detalhes.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Usado para controles que possuem um intervalo de valores que podem ser aplicados ao controle. Por exemplo, um controle rotador contendo anos pode ter um alcance de 1900 a 2010, enquanto outro controle rotador apresentando meses teria um alcance de 1 a 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Usado para controles que podem ser rolados. Por exemplo, um controle que tenha barras de rolagem que ficam ativas quando há mais informações que podem ser exibidas na área de visualização do controle.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Usado para controles que possuem itens individuais em uma lista de rolagem. Por exemplo, um controle de lista que possua itens individuais na lista de rolagem, como um controle de caixa de combinação.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Usado para controles de contêiner de seleção. Por exemplo, liste caixas e caixas de combinação.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Usado para itens individuais nos controles do contêiner de seleção, como caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Usado para controles que possuem uma grade e informações de cabeçalho. Por exemplo, planilhas do Microsoft Excel.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Usado para itens em uma tabela.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Usado para editar controles e documentos que exponham informações textuais.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Usado para controles onde é possível alternar o estado. Por exemplo, caixas de seleção e itens de menu seletíveis.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Usado para controles que podem ser redimensionados, transferidos e girados. O padrão de controle de transformação costuma ser usado em aplicativos de desenho, design, formulários e editores gráficos.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Possibilita que os clientes obtenham ou definam um valor nos controles que não dão suporte a um intervalo de valores. Por exemplo, um catador de datas.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Expõe informações específicas de janelas, um conceito fundamental para o sistema operacional Microsoft Windows. Exemplos de controles que são janelas são janelas de aplicativos de nível superior (Microsoft Word, Microsoft Windows Explorer e assim por diante), janelas de crianças de interface de vários documentos (MDI) e diálogos.|  
  
## <a name="see-also"></a>Confira também

- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Mapeamento de Padrão de Controles para Clientes de Automação de IU](control-pattern-mapping-for-ui-automation-clients.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
- [Automação de Propriedades de Interface de Usuário para Clientes.](ui-automation-properties-for-clients.md)
- [Automação de Eventos de Interface de Usuário para Clientes.](ui-automation-events-for-clients.md)
