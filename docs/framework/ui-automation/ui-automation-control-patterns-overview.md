---
title: "Visão Geral de Padrões de Controle de Automação de Interface de Usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
caps.latest.revision: "34"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 057aed4012a884ea13806a4d1174d53dd27ab609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-control-patterns-overview"></a>Visão Geral de Padrões de Controle de Automação de Interface de Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral apresenta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] padrões de controle. Padrões de controle fornecem uma maneira de categorizar e expor a funcionalidade de um controle independente do tipo de controle ou a aparência do controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]usa padrões para representar comportamentos de controle comuns de controle. Por exemplo, você deve usar o padrão de controle Invoke para controles que podem ser invocados (como botões) e o padrão de controle Scroll para controles que têm barras de rolagem (como caixas de listagem, exibições de listas ou caixas de combinação). Como cada padrão de controle representa uma funcionalidade separada, eles podem ser combinados para descrever o conjunto completo de funcionalidade com suporte em um determinado controle.  
  
> [!NOTE]
>  Controles agregados — construídos com controles filhos que fornecem o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] para funcionalidades expostas pelo pai — devem implementar padrões de controle normalmente associados com cada controle filho. Por sua vez, esses mesmos padrões de controle não são necessários para serem implementados pelos controles filhos.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Componentes de padrão de controle de automação de interface do usuário  
 Padrões de controle suportam os métodos, propriedades, eventos e relacionamentos necessários para definir a peça discreta da funcionalidade disponível em um controle.  
  
-   A relação entre um elemento de automação de interface do usuário e seu pai, filhos e irmãos descreve a estrutura do elemento dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.  
  
-   Os métodos de permitir que os clientes de automação de interface do usuário manipular o controle.  
  
-   As propriedades e eventos fornecem informações sobre a funcionalidade do padrão de controle, bem como informações sobre o estado do controle.  
  
 Padrões de controle se relacionam com [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] como interfaces relacionam a [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] objetos. Em [!INCLUDE[TLA2#tla_com](../../../includes/tla2sharptla-com-md.md)], você pode consultar um objeto para pedir quais interfaces ele suporta e então usar essas interfaces para acessar funcionalidades. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], clientes de automação de interface do usuário podem pedir um controle quais padrões de controle ele suporta e interagir com o controle por meio de propriedades, métodos, eventos e estruturas expostas por padrões de controle suportados. Por exemplo, para uma caixa de edição de várias linhas, provedores de automação de interface do usuário implementam <xref:System.Windows.Automation.Provider.IScrollProvider>. Quando um cliente sabe que um <xref:System.Windows.Automation.AutomationElement> oferece suporte a <xref:System.Windows.Automation.ScrollPattern> padrão de controle, ele pode usar as propriedades, métodos e eventos expostos por aquele padrão de controle para manipular o controle ou informações sobre o controle de acesso.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Os clientes e provedores de automação de interface do usuário  
 Provedores de automação de interface do usuário implementam os padrões de controle para expor o comportamento apropriado para uma parte específica de funcionalidade suportada pelo controle.  
  
 Clientes de automação de interface do usuário de acessam os métodos e propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes de padrão de controle e usá-los para obter informações sobre o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], ou para manipular o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Essas classes de padrão de controle são encontradas no <xref:System.Windows.Automation> namespace (por exemplo, <xref:System.Windows.Automation.InvokePattern> e <xref:System.Windows.Automation.SelectionPattern>).  
  
 Os clientes usam <xref:System.Windows.Automation.AutomationElement> métodos (como <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) ou o [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] acessadores para acessar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades em um padrão. Cada classe de padrão de controle tem um membro campo (por exemplo, <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType>' ou <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>) que identifica esse padrão de controle e pode ser passada como um parâmetro para <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> para recuperar esse padrão para um <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Padrões de controle dinâmico  
 Alguns controles não dão suporte sempre o mesmo conjunto de padrões de controle. Padrões de controle são considerados suportados quando estão disponíveis para um cliente de automação de interface do usuário. Por exemplo, um multiline Editar caixa habilita a rolagem vertical somente quando contém mais linhas de texto que podem ser exibidos na área visível. Rolagem é desabilitada quando texto suficiente é removido para que fiquem não é mais necessário. Neste exemplo, o padrão de controle ScrollPattern é dinamicamente suportado dependendo do estado atual do controle (quanto texto está na caixa de edição).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Interfaces e Classes de padrão de controle  
 A tabela a seguir descreve o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões de controle. A tabela também lista as classes usadas por clientes de automação de interface do usuário para os padrões de controle de acesso, bem como as interfaces usadas por provedores de automação de interface do usuário para implementá-las.  
  
|Classe de padrão de controle|Interface de provedor|Descrição|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Usado para controles que podem ser colocados em um contêiner de encaixe. Por exemplo, barras de ferramentas e paletas de ferramentas.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Usado para controles que podem ser expandidos ou recolhidos. Por exemplo, itens de menu em um aplicativo, como o **arquivo** menu.|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Usado para controles que oferecem suporte à funcionalidade de grade como redimensionar e mover para uma célula especificada. Por exemplo, o ícone grande exibir no Windows Explorer ou simples tabelas sem cabeçalho em [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)].|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Usado para controles que têm células de grade. As células individuais devem suportar o padrão GridItem. Por exemplo, cada célula na [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] exibição de detalhes.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Usado para controles que podem ser invocados, como um botão.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Usado para controles que podem alternar entre várias representações do mesmo conjunto de informações, dados ou filhos. Por exemplo, uma exibição de lista controlar onde os dados estão disponíveis em miniatura, lado a lado, ícone, lista ou modos de exibição de detalhes.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Usado para controles que têm um intervalo de valores que podem ser aplicados ao controle. Por exemplo, um controle giratório contendo anos pode ter um intervalo de 1900 até 2010, enquanto outro controle giratório apresentando meses teria um intervalo de 1 a 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Usado para controles que podem rolar. Por exemplo, um controle que tem barras de rolagem que estão ativas quando há mais informações que podem ser exibidos na área visível do controle.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Usado para controles que tem itens individuais na lista que rola. Por exemplo, um controle de lista que tem itens individuais na lista de rolagem, como um controle de caixa de combinação.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Usado para controles de contêiner de seleção. Por exemplo, caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Usado para itens individuais em controles de contêiner de seleção, como caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Usado para controles que têm uma grade, bem como informações de cabeçalho. Por exemplo, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilhas.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Usado para itens em uma tabela.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Usado para controles de edição e documentos que expõem informações textuais.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Usado para controles onde o estado pode ser alternado. Por exemplo, caixas de seleção e itens de menu selecionável.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Usado para controles que podem ser redimensionados, movidos e girados. Usos típicos para o padrão de controle de transformação estão em designers, formulários, editores gráficos e desenho de aplicativos.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Permite que os clientes obter ou definir um valor em controles que não oferecem suporte a um intervalo de valores. Por exemplo, um seletor de tempo de data.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Expõe as informações específicas do windows, um conceito fundamental para o [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] sistema operacional. Exemplos de controles que são janelas são janelas de nível superior do aplicativo ([!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)], [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], e assim por diante), [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] janelas filho e caixas de diálogo.|  
  
## <a name="see-also"></a>Consulte também  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Visão geral de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)  
 [Propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Eventos de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
