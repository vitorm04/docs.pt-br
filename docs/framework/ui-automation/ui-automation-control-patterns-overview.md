---
title: Visão Geral de Padrões de Controle de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 74e373610a78cbed5d31ff408e3c4ef8f11216f6
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066228"
---
# <a name="ui-automation-control-patterns-overview"></a>Visão Geral de Padrões de Controle de Automação de Interface de Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Esta visão geral apresenta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] padrões de controle. Padrões de controle fornecem uma maneira de categorizar e expor a funcionalidade de um controle independente do tipo de controle ou a aparência do controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usa o padrão para representar comportamentos de controle comum de controles. Por exemplo, você deve usar o padrão de controle Invoke para controles que podem ser invocados (como botões) e o padrão de controle de rolagem para controles que têm as barras de rolagem (como caixas de listagem, modos de exibição de lista ou caixas de combinação). Como cada padrão de controle representa uma funcionalidade separada, eles podem ser combinados para descrever o conjunto completo de funcionalidade com suporte de um controle específico.  
  
> [!NOTE]
>  Controles agregados — construídos com controles filhos que fornecem o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] para a funcionalidade exposta pelo pai — devem implementar padrões de controle normalmente associados a cada controle filho. Por sua vez, esses mesmos padrões de controle não são necessários para serem implementados pelos controles filhos.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Componentes de padrão de controle de automação de interface do usuário  
 Padrões de controle dão suporte a métodos, propriedades, eventos e as relações necessárias para definir uma parte distinta da funcionalidade disponível em um controle.  
  
-   A relação entre um elemento de automação de interface do usuário e seu pai, filhos e irmãos descreve a estrutura do elemento dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.  
  
-   Os métodos permitem que os clientes de automação de interface do usuário manipular o controle.  
  
-   As propriedades e eventos fornecem informações sobre a funcionalidade do padrão de controle, bem como informações sobre o estado do controle.  
  
 Padrões de controle se relacionam [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] como interfaces se relacionam com [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] objetos. No [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], você pode consultar um objeto para pedir quais interfaces ele suporta e então usar essas interfaces para acessar a funcionalidade. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], clientes de automação de interface do usuário podem fazer com que um controle de padrões de controle de quais ele dá suporte a e, em seguida, interaja com o controle por meio de propriedades, métodos, eventos e estruturas expostas pelos padrões de controle com suporte. Por exemplo, para uma caixa de edição de várias linhas, provedores de automação de interface do usuário implementam <xref:System.Windows.Automation.Provider.IScrollProvider>. Quando um cliente sabe que um <xref:System.Windows.Automation.AutomationElement> oferece suporte a <xref:System.Windows.Automation.ScrollPattern> padrão de controle, ele pode usar as propriedades, métodos e eventos expostos por esse padrão de controle para manipular o controle ou informações sobre o controle de acesso.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Os clientes e provedores de automação de interface do usuário  
 Provedores de automação de interface do usuário implementam padrões de controle para expor o comportamento apropriado para uma parte específica da funcionalidade com suporte pelo controle.  
  
 Clientes de automação de interface do usuário de acessam os métodos e propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes de padrão de controle e usá-los para obter informações sobre a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ou manipular o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Essas classes de padrão de controle são encontradas na <xref:System.Windows.Automation> namespace (por exemplo, <xref:System.Windows.Automation.InvokePattern> e <xref:System.Windows.Automation.SelectionPattern>).  
  
 Os clientes usam <xref:System.Windows.Automation.AutomationElement> métodos (como <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) ou o [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] acessadores para acessar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades em um padrão. Cada classe de padrão de controle tem um membro de campo (por exemplo, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> ou <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>) que identifica esse padrão de controle e pode ser passado como um parâmetro para <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> para recuperar esse padrão para um <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Padrões de controle dinâmico  
 Alguns controles não suportam sempre o mesmo conjunto de padrões de controle. Padrões de controle são considerados suportados quando estão disponíveis para um cliente de automação de interface do usuário. Por exemplo, um multiline Editar caixa habilita a rolagem vertical somente quando ela contém mais linhas de texto que pode ser exibido na área visível. Rolagem é desabilitada quando texto suficiente é removido para que a rolagem não for mais necessária. Neste exemplo, o padrão de controle ScrollPattern é dinamicamente suportado dependendo do estado atual do controle (a quantidade de texto está na caixa de edição).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Interfaces e Classes de padrão de controle  
 A tabela a seguir descreve o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões de controle. A tabela também lista as classes usadas por clientes de automação de interface do usuário para acessar os padrões de controle, bem como as interfaces usadas por provedores de automação de interface do usuário para implementá-los.  
  
|Classe de padrão de controle|Interface de provedor|Descrição|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Usado para controles que podem ser encaixados em um contêiner de encaixe. Por exemplo, as barras de ferramentas e paletas de ferramentas.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Usado para controles que podem ser expandidos ou recolhidos. Por exemplo, itens de menu em um aplicativo, como o **arquivo** menu.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Usado para controles que dão suporte à funcionalidade de grade como redimensionar e mover para uma célula especificada. Por exemplo, o ícone grande exibir no Windows Explorer ou tabelas simples sem cabeçalhos no [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Usado para controles que têm células dentro de grades. As células individuais devem suportar o padrão GridItem. Por exemplo, cada célula no [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] modo de exibição de detalhes.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Usado para controles que podem ser invocados, como um botão.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Usado para controles que podem alternar entre várias representações do mesmo conjunto de informações, dados ou filhos. Por exemplo, uma exibição de lista controlar onde os dados estão disponíveis em miniatura, lado a lado, ícone, lista ou modos de exibição de detalhes.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Usado para controles que têm um intervalo de valores que podem ser aplicados ao controle. Por exemplo, um controle giratório contendo anos pode ter um intervalo de 1900 até 2010, enquanto outro controle giratório apresentando meses teria um intervalo de 1 a 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Usado para controles que podem rolar. Por exemplo, um controle que tem barras de rolagem que estão ativas quando há mais informações que podem ser exibidos na área visível do controle.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Usado para controles que têm itens individuais em uma lista que rola. Por exemplo, um controle de lista que tem itens individuais na lista de rolagem, como um controle de caixa de combinação.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Usado para controles de contêiner de seleção. Por exemplo, caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Usado para itens individuais em controles de contêiner de seleção, como caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Usado para controles que têm uma grade, bem como informações de cabeçalho. Por exemplo, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilhas.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Usado para itens em uma tabela.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Usado para controles de edição e documentos que expõem informações textuais.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Usado para controles em que o estado pode ser alternado. Por exemplo, as caixas de seleção e itens de menu selecionável.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Usado para controles que podem ser redimensionados, movidos e girados. Usos típicos para o padrão de controle Transform estão em formulários, designers, editores gráficos e desenho de aplicativos.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Permite que os clientes obter ou definir um valor em controles que não dão suporte a um intervalo de valores. Por exemplo, um seletor de data hora.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Expõe as informações específicas do windows, um conceito fundamental para o [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] sistema operacional. Exemplos de controles que são janelas são janelas de aplicativo de nível superior ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]e assim por diante), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] caixas de diálogo e janelas filho.|  
  
## <a name="see-also"></a>Consulte também
- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
- [Propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Eventos de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
