---
title: Visão Geral de Padrões de Controle de Automação de Interface de Usuário
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns
- UI Automation, control patterns
ms.assetid: cc229b33-234b-469b-ad60-f0254f32d45d
ms.openlocfilehash: 6e2b5eaff3ee80434d5cdf39391273685da9faf0
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68434081"
---
# <a name="ui-automation-control-patterns-overview"></a>Visão Geral de Padrões de Controle de Automação de Interface de Usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Esta visão geral [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] apresenta padrões de controle. Os padrões de controle fornecem uma maneira de categorizar e expor a funcionalidade de um controle independentemente do tipo de controle ou da aparência do controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]usa padrões de controle para representar comportamentos de controle comuns. Por exemplo, você usa o padrão de controle Invoke para controles que podem ser invocados (como botões) e o padrão de controle Scroll para controles que têm barras de rolagem (como caixas de listagem, exibições de lista ou caixas de combinação). Como cada padrão de controle representa uma funcionalidade separada, eles podem ser combinados para descrever o conjunto completo de funcionalidades com suporte de um controle específico.  
  
> [!NOTE]
>  Controles agregados — criados com controles filho que fornecem [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a funcionalidade for exposta pelo pai — devem implementar todos os padrões de controle normalmente associados a cada controle filho. Por sua vez, os mesmos padrões de controle não precisam ser implementados pelos controles filho.  
  
<a name="uiautomation_control_pattern_includes"></a>   
## <a name="ui-automation-control-pattern-components"></a>Componentes do padrão de controle de automação da interface do usuário  
 Os padrões de controle dão suporte aos métodos, propriedades, eventos e relações necessários para definir uma parte discreta da funcionalidade disponível em um controle.  
  
- A relação entre um elemento de automação de interface do usuário e seu pai, filhos e irmãos descreve a estrutura do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento dentro da árvore.  
  
- Os métodos permitem que os clientes de automação da interface do usuário manipulem o controle.  
  
- As propriedades e os eventos fornecem informações sobre a funcionalidade do padrão de controle, bem como informações sobre o estado do controle.  
  
 Os padrões de controle [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estão relacionados a como interfaces do as Component Object Model (com). Em COM, você pode consultar um objeto para perguntar a quais interfaces ele dá suporte e, em seguida, usar essas interfaces para acessar a funcionalidade. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], os clientes de automação da interface do usuário podem pedir a um controle quais padrões de controle ele oferece suporte e interagir com o controle por meio de propriedades, métodos, eventos e estruturas expostas pelos padrões de controle com suporte. Por exemplo, para uma caixa de edição de várias linhas, os <xref:System.Windows.Automation.Provider.IScrollProvider>provedores de automação da interface do usuário implementam. Quando um cliente sabe que um <xref:System.Windows.Automation.AutomationElement> dá suporte <xref:System.Windows.Automation.ScrollPattern> ao padrão de controle, ele pode usar as propriedades, os métodos e os eventos expostos por esse padrão de controle para manipular o controle ou acessar informações sobre o controle.  
  
<a name="uiautomation_control_pattern_client_provider"></a>   
## <a name="ui-automation-providers-and-clients"></a>Provedores e clientes de automação da interface do usuário  
 Os provedores de automação da interface do usuário implementam padrões de controle para expor o comportamento apropriado para uma parte específica da funcionalidade com suporte do controle.  
  
 Os clientes de automação da interface do usuário [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] acessam métodos e propriedades de classes de padrão de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]controle e as usam para [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]obter informações sobre o ou para manipular o. Essas classes de padrão de controle são encontradas <xref:System.Windows.Automation> no namespace (por exemplo <xref:System.Windows.Automation.InvokePattern> , <xref:System.Windows.Automation.SelectionPattern>e).  
  
 Os clientes <xref:System.Windows.Automation.AutomationElement> usam métodos ( <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> como ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>) ou os acessadores Common Language Runtime (CLR) para acessar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] as propriedades em um padrão. Cada classe de padrão de controle tem um membro Field (por <xref:System.Windows.Automation.InvokePattern.Pattern?displayProperty=nameWithType> exemplo <xref:System.Windows.Automation.SelectionPattern.Pattern?displayProperty=nameWithType>, ou) que identifica esse padrão de controle e pode ser passado como <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> um <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> parâmetro para ou para recuperar esse <xref:System.Windows.Automation.AutomationElement>padrão para um.  
  
<a name="uiautomation_control_patterns_dynamic"></a>   
## <a name="dynamic-control-patterns"></a>Padrões de controle dinâmico  
 Alguns controles nem sempre dão suporte ao mesmo conjunto de padrões de controle. Padrões de controle são considerados compatíveis quando estão disponíveis para um cliente de automação de interface do usuário. Por exemplo, uma caixa de edição de várias linhas permite a rolagem vertical somente quando ela contém mais linhas de texto que podem ser exibidas em sua área visível. A rolagem é desabilitada quando texto suficiente é removido para que a rolagem não seja mais necessária. Para este exemplo, o padrão de controle ScrollPattern tem suporte dinâmico dependendo do estado atual do controle (a quantidade de texto na caixa de edição).  
  
<a name="Control_Pattern_Classes_and_Interfaces"></a>   
## <a name="control-pattern-classes-and-interfaces"></a>Classes e interfaces de padrão de controle  
 A tabela a seguir descreve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] os padrões de controle. A tabela também lista as classes usadas pelos clientes de automação da interface do usuário para acessar os padrões de controle, bem como as interfaces usadas pelos provedores de automação da interface do usuário para implementá-los.  
  
|Classe de padrão de controle|Interface do provedor|Descrição|  
|---------------------------|------------------------|-----------------|  
|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.Provider.IDockProvider>|Usado para controles que podem ser encaixados em um contêiner de encaixe. Por exemplo, barras de ferramentas ou paletas de ferramentas.|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Usado para controles que podem ser expandidos ou recolhidos. Por exemplo, itens de menu em um aplicativo, como o menu **arquivo** .|  
|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.Provider.IGridProvider>|Usado para controles que dão suporte à funcionalidade de grade, como dimensionar e mover para uma célula especificada. Por exemplo, o modo de exibição de ícones grandes no Windows Explorer ou tabelas simples [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]sem cabeçalhos no.|  
|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Usado para controles que têm células dentro de grades. As células individuais devem dar suporte ao padrão GridItem. Por exemplo, cada célula na [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] exibição de detalhes.|  
|<xref:System.Windows.Automation.InvokePattern>|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Usado para controles que podem ser invocados, como um botão.|  
|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Usado para controles que podem alternar entre as várias representações do mesmo conjunto de informações, dados ou filhos. Por exemplo, um controle de exibição de lista onde os dados estão disponíveis nas exibições de miniatura, bloco, ícone, lista ou detalhes.|  
|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Usado para controles que têm um intervalo de valores que podem ser aplicados ao controle. Por exemplo, um controle giratório contendo anos pode ter um intervalo de 1900 a 2010, enquanto outro controle giratório apresentando meses teria um intervalo de 1 a 12.|  
|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.Provider.IScrollProvider>|Usado para controles que podem rolar. Por exemplo, um controle que tem barras de rolagem que estão ativas quando há mais informações do que pode ser exibido na área visível do controle.|  
|<xref:System.Windows.Automation.ScrollItemPattern>|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Usado para controles que têm itens individuais em uma lista que rola. Por exemplo, um controle de lista que tem itens individuais na lista de rolagem, como um controle de caixa de combinação.|  
|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Usado para controles de contêiner de seleção. Por exemplo, caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Usado para itens individuais em controles de contêiner de seleção, como caixas de listagem e caixas de combinação.|  
|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.Provider.ITableProvider>|Usado para controles que têm uma grade, bem como informações de cabeçalho. Por exemplo, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilhas.|  
|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Usado para itens em uma tabela.|  
|<xref:System.Windows.Automation.TextPattern>|<xref:System.Windows.Automation.Provider.ITextProvider>|Usado para controles de edição e documentos que expõem informações textuais.|  
|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.Provider.IToggleProvider>|Usado para controles em que o estado pode ser alternado. Por exemplo, caixas de seleção e itens de menu verificável.|  
|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.Provider.ITransformProvider>|Usado para controles que podem ser redimensionados, movidos e girados. Usos típicos para o padrão de controle transformar são em designers, formulários, editores gráficos e aplicativos de desenho.|  
|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.Provider.IValueProvider>|Permite que os clientes obtenham ou definam um valor em controles que não dão suporte a um intervalo de valores. Por exemplo, um seletor de data e hora.|  
|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.Provider.IWindowProvider>|Expõe informações específicas ao Windows, um conceito fundamental para o [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] sistema operacional. Exemplos de controles que são janelas são janelas de aplicativo de nível superior[!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]( [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], e assim por diante) [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] , janelas filhas e caixas de diálogo.|  
  
## <a name="see-also"></a>Consulte também

- [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
- [Propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [Eventos de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
