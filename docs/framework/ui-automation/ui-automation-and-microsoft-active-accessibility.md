---
title: Automação de Interface do usuário e Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 3c8d23b5172cdcfcb009d85c6260c7c68d679bdb
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802323"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automação de Interface do usuário e Microsoft Active Accessibility
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Acessibilidade ativa da Microsoft foi a solução anterior para tornar aplicativos acessíveis. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] é o novo modelo de acessibilidade para [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] e se destina a atender às necessidades de produtos de tecnologia assistencial e ferramentas de teste automatizado. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oferece muitos aprimoramentos em Acessibilidade ativa.  
  
 Este tópico inclui os principais recursos do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] e explica como esses recursos diferem do Active Accessibility.  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Linguagens de programação  
< a acessibilidade ativa se baseia a [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] com suporte para interfaces duplas e, portanto, programáveis em C /C++, [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]e linguagens de script. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (incluindo a biblioteca do provedor do lado do cliente para controles padrão) é escrito em código gerenciado, e aplicativos cliente de automação de interface do usuário são programados com mais facilidade usando c# ou Visual Basic .NET. Provedores de automação de interface do usuário, que são implementações de interface, podem ser escritos em código gerenciado ou em C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Suporte no Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) é o novo modelo para criar interfaces do usuário. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementos não contêm suporte nativo para acessibilidade ativa; No entanto, eles são compatíveis com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], que inclui suporte para clientes de acessibilidade ativa a ponte. Somente os clientes criados especificamente para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podem se beneficiar dos recursos de acessibilidade do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], tais como o suporte avançado para texto.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Servidores e clientes  
 No Active Accessibility, servidores e clientes se comunicam diretamente, amplamente através da implementação do servidor de `IAccessible`.  
  
 No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um serviço principal se encontra entre o servidor (chamado de provedor) e o cliente. O serviço principal faz chamadas para as interfaces implementadas pelos provedores e fornece serviços adicionais, como a geração de identificadores de tempo de execução exclusivos para elementos. Aplicativos cliente usam funções de biblioteca para chamar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] service.  
  
 Provedores de automação de interface do usuário podem fornecer informações aos clientes de acessibilidade do Active Directory e servidores do Active Accessibility podem fornecer informações para aplicativos de cliente de automação de interface do usuário. No entanto, como Active Accessibility não expõe tanta informação quanto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], os dois modelos não são totalmente compatíveis.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Elementos da interface do usuário  
 Acessibilidade ativa apresenta [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos como uma `IAccessible` interface ou como um identificador filho. É difícil comparar dois `IAccessible` ponteiros para determinar se eles se referem ao mesmo elemento.  
  
 Na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], cada elemento é representado como um <xref:System.Windows.Automation.AutomationElement> objeto. Comparação é feita usando o operador de igualdade ou o <xref:System.Windows.Automation.AutomationElement.Equals%2A> método, que comparam os identificadores de tempo de execução exclusivos dos elementos.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Navegação e modos de exibição de árvore  
 O [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos na tela podem ser vistos como uma estrutura de árvore com a área de trabalho como a raiz, janelas de aplicativos como filhos imediatos e elementos em aplicativos como mais descendentes.  
  
 No Active Accessibility, muitos elementos de automação que são irrelevantes para os usuários finais são expostos na árvore. Aplicativos cliente precisam examinar todos os elementos para determinar quais são significativos.  
  
 Aplicativos cliente de automação de interface do usuário consulte o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] por meio de uma exibição filtrada. O modo de exibição contém apenas os elementos de seu interesse: aqueles que fornecem informações para o usuário ou habilitar a interação. As exibições predefinidas de apenas os elementos de controle e apenas os elementos de conteúdo estão disponíveis; Além disso, os aplicativos podem definir modos de exibição personalizados. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] simplifica a tarefa de descrever a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para o usuário e ajudar o usuário interagir com o aplicativo.  
  
 Navegação entre elementos, no Active Accessibility, é espacial (por exemplo, mudando para o elemento que está à esquerda na tela), lógica (por exemplo, movendo para o próximo item de menu, ou o próximo item na ordem de tabulação dentro de uma caixa de diálogo) ou hierárquica ( Por exemplo, mover o primeiro filho em um contêiner ou do filho para seu pai). Navegação hierárquica é complicada pelo fato de que elementos filho nem sempre são objetos que implementam `IAccessible`.  
  
 Na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos são <xref:System.Windows.Automation.AutomationElement> objetos que dão suporte a mesma funcionalidade básica. (Do ponto de vista do provedor, eles são objetos que implementam uma interface herdada de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) A navegação é principalmente hierárquica: de pais para filhos e de um irmão para o próximo. (A navegação entre irmãos tem um elemento lógico, como ele pode seguir a ordem de tabulação.) Você pode navegar de qualquer ponto inicial, usando qualquer exibição filtrada da árvore, usando o <xref:System.Windows.Automation.TreeWalker> classe. Você também pode navegar para determinados filhos ou descendentes por meio <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> e <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; por exemplo, é muito fácil recuperar todos os elementos dentro de uma caixa de diálogo que dão suporte a um padrão de controle especificado.  
  
 Navegação no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é mais consistente do que no Active Accessibility. Alguns elementos, como listas suspensas e janelas pop-up aparecem duas vezes na árvore de acessibilidade ativa e navegação deles pode ter resultados inesperados. É impossível implementar adequadamente a acessibilidade ativa para um controle rebar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Habilita a mudança de pai e reposicionamento, para que um elemento pode ser colocado em qualquer lugar na árvore apesar da hierarquia imposta pela propriedade do windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Funções e tipos de controle  
 Acessibilidade ativa usa o `accRole` propriedade (`IAccessible::get_actRole`) para recuperar uma descrição da função do elemento no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], como ROLE_SYSTEM_SLIDER ou ROLE_SYSTEM_MENUITEM. A função de um elemento é a dica principal à sua funcionalidade disponível. Interação com um controle é obtida usando métodos fixos, como `IAccessible::accSelect` e `IAccessible::accDoDefaultAction`. A interação entre o aplicativo cliente e o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] é limitado a que pode ser feito por meio de `IAccessible`.  
  
 Em contraste, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] amplamente desassocia o tipo de controle do elemento (descrito pelo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> propriedade) de sua funcionalidade esperada. Funcionalidade é determinada pelos padrões de controle que são compatíveis com o provedor por meio de sua implementação de interfaces especializadas. Padrões de controle podem ser combinados para descrever o conjunto completo de funcionalidade com suporte de um determinado [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elemento. Alguns provedores são necessários para dar suporte a um padrão de controle específico; Por exemplo, o provedor para uma caixa de seleção deve suportar o padrão de controle de alternância. Outros provedores são necessários para dar suporte a um ou mais de um conjunto de padrões de controle; Por exemplo, um botão deve oferecer suporte a alternância ou Invoke. Ainda outros dão suporte a nenhum controle padrões Por exemplo, um painel que não pode ser movido, redimensionado ou encaixado não tem nenhum padrão de controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dá suporte a controles personalizados que são identificados pela <xref:System.Windows.Automation.ControlType.Custom> propriedade e podem ser descritos pelo <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> propriedade.  
  
 A tabela a seguir mostra o mapeamento de funções do Active Accessibility para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tipos de controle.  
  
|Função de acessibilidade ativa|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tipo de controle|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Botão|  
|ROLE_SYSTEM_CLIENT|Calendário|  
|ROLE_SYSTEM_CHECKBUTTON|Caixa de seleção|  
|ROLE_SYSTEM_COMBOBOX|Caixa de combinação|  
|ROLE_SYSTEM_CLIENT|Personalizado|  
|ROLE_SYSTEM_LIST|Grade de dados|  
|ROLE_SYSTEM_LISTITEM|Item de dados|  
|ROLE_SYSTEM_DOCUMENT|Documento|  
|ROLE_SYSTEM_TEXT|Editar|  
|ROLE_SYSTEM_GROUPING|Grupo|  
|ROLE_SYSTEM_LIST|Cabeçalho|  
|ROLE_SYSTEM_COLUMNHEADER|Item de cabeçalho|  
|ROLE_SYSTEM_LINK|Hiperlink|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|Lista|  
|ROLE_SYSTEM_LISTITEM|Item de lista|  
|ROLE_SYSTEM_MENUPOPUP|Menu|  
|ROLE_SYSTEM_MENUBAR|Barra de menus|  
|ROLE_SYSTEM_MENUITEM|Item de menu|  
|ROLE_SYSTEM_PANE|Painel|  
|ROLE_SYSTEM_PROGRESSBAR|Barra de progresso|  
|ROLE_SYSTEM_RADIOBUTTON|Botão de opção|  
|ROLE_SYSTEM_SCROLLBAR|Barra de rolagem|  
|ROLE_SYSTEM_SEPARATOR|Separador|  
|ROLE_SYSTEM_SLIDER|Controle deslizante|  
|ROLE_SYSTEM_SPINBUTTON|Controle giratório|  
|ROLE_SYSTEM_SPLITBUTTON|Botão de divisão|  
|ROLE_SYSTEM_STATUSBAR|Barra de status|  
|ROLE_SYSTEM_PAGETABLIST|Tabulação|  
|ROLE_SYSTEM_PAGETAB|Item de guia|  
|ROLE_SYSTEM_TABLE|Tabela|  
|ROLE_SYSTEM_STATICTEXT|Texto|  
|ROLE_SYSTEM_INDICATOR|Posição|  
|ROLE_SYSTEM_TITLEBAR|Barra de título|  
|ROLE_SYSTEM_TOOLBAR|Barra de ferramentas|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|Árvore|  
|ROLE_SYSTEM_OUTLINEITEM|Item de árvore|  
|ROLE_SYSTEM_WINDOW|Janela|  
  
 Para obter mais informações sobre os diferentes tipos de controle, consulte [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Estados e propriedades  
 No Active Accessibility, elementos oferecem suporte a um conjunto comum de propriedades e algumas propriedades (como `accState`) devem descrever coisas muito diferentes, dependendo da função do elemento. Servidores devem implementar todos os métodos de `IAccessible` que retornam uma propriedade, mesmo aqueles que não são relevantes para o elemento.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] define várias propriedades mais, alguns dos quais correspondem aos estados no Active Accessibility. Alguns são comuns a todos os elementos, mas outras são específicas para tipos de controle e padrões de controle. As propriedades são distinguidas por identificadores exclusivos, e a maioria das propriedades pode ser recuperada por meio de um único método, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Muitas propriedades também são facilmente recuperáveis do <xref:System.Windows.Automation.AutomationElement.Current%2A> e <xref:System.Windows.Automation.AutomationElement.Cached%2A> acessadores de propriedade.  
  
 Um provedor de automação de interface do usuário não tem que implementar propriedades irrelevantes, mas pode simplesmente retornar um `null` valor para quaisquer propriedades que ele não oferece suporte. Além disso, o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principal serviço pode obter algumas propriedades do provedor de janela padrão, e essas são mescladas com propriedades explicitamente implementadas pelo provedor.  
  
 Bem como suporte a muitos mais propriedades [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fornece melhor desempenho, permitindo que várias propriedades a serem recuperadas com uma chamada única entre processos.  
  
 A tabela a seguir mostra a correspondência entre as propriedades nos dois modelos.  
  
|Acessador de propriedade de acessibilidade ativado|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ID de propriedade|Comentários|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> ou <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` tem precedência se ambos estiverem presentes.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Consulte a tabela anterior para mapeamento de funções para tipos de controle.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Válido somente para tipos de controle que dão suporte a ValuePattern ou RangeValuePattern. Valores RangeValue são normalizados para 0 a 100, para ser consistente com o comportamento MSAA. Itens de valor usam uma cadeia de caracteres.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Não tem suporte no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` não tinha uma especificação clara dentro de MSAA, o que resultou em provedores de colocação de diferentes partes de informações nessa propriedade.|  
|`get_accHelpTopic`|Não tem suporte no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 A tabela a seguir mostra quais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades correspondem às constantes de estado de acessibilidade ativa.  
  
|Estado de acessibilidade ativado|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Alteração de estado de disparadores?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Caixa de seleção <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Para o botão de opção <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|S|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|S|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> Ou <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|S|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> para itens de menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True e <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> faz com que <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> há suporte para|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|S|  
  
 Os seguintes estados não foram implementados pela maioria dos Active Accessibility controlar os servidores ou não têm equivalentes em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|Estado de acessibilidade ativado|Comentários|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_MARQUEED|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_SELFVOICING|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_TRAVERSED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_ALERT_MEDIUM|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_ALERT_LOW|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_FLOATING|Não foi amplamente implementada pelos servidores do Active Accessibility|  
|STATE_SYSTEM_HOTTRACKED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Para obter uma lista completa dos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identificadores de propriedade, consulte [visão geral das propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Eventos  
 O mecanismo de evento em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], diferente de acessibilidade ativa, não confie no Windows roteamento de eventos (que é intimamente vinculado a identificadores de janela) e não requer que o aplicativo cliente configure ganchos. Assinaturas de eventos podem ser ajustadas não apenas para determinados eventos, mas para determinados partes da árvore. Provedores também podem ajustar a sua criação de eventos por manter o controle de quais eventos estão sendo atendidos.  
  
 Também é mais fácil para os clientes recuperem os elementos que geram eventos, conforme eles são passados diretamente para o retorno de chamada do evento. Propriedades do elemento são pré-buscados automaticamente se uma solicitação de cache estava ativa quando o cliente assina o evento.  
  
 A tabela a seguir mostra a correspondência de WinEvents de acessibilidade ativa e [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Identificador de evento|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> Alteração de propriedade|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> alteração de propriedade nas barras de rolagem associado|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Não há equivalência|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Nenhum equivalente exato; Talvez <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> ou <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> alteração de propriedade|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> Alteração|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Alteração de propriedade|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> Alteração de propriedade|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Não consistentemente usado em Acessibilidade ativa. Nenhum evento diretamente correspondente é definido em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Não há equivalência|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Vários eventos de propriedade alterada|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> alterado|  
|EVENT_SYSTEM_ALERT|Não há equivalência|  
|EVENT_SYSTEM_CAPTUREEND|Não há equivalência|  
|EVENT_SYSTEM_CAPTURESTART|Não há equivalência|  
|EVENT_SYSTEM_CONTEXTHELPEND|Não há equivalência|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Não há equivalência|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Não há equivalência|  
|EVENT_SYSTEM_DRAGDROPSTART|Não há equivalência|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Alteração de propriedade|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Alteração de propriedade|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Alteração de propriedade|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Alteração de propriedade|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> alteração de propriedade|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> alteração de propriedade|  
|EVENT_SYSTEM_SOUND|Não há equivalência|  
|EVENT_SYSTEM_SWITCHEND|Não há equivalente, mas um <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> evento sinaliza que um novo aplicativo recebeu o foco|  
|EVENT_SYSTEM_SWITCHSTART|Não há equivalência|  
|Não há equivalência|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> Alteração de propriedade|  
|Não há equivalência|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Alteração de propriedade|  
|Não há equivalência|Evento <xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>|  
|Não há equivalência|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Segurança  
 Alguns `IAccessible` cenários de personalização exigem uma base de encapsulamento `IAccessible` e chamada através dela. Isso tem implicações de segurança, uma vez que um componente parcialmente confiável não deve ser um intermediário em um caminho de código.  
  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelo elimina a necessidade dos provedores chamar por meio de outro código de provedor. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] serviço principal faz toda a agregação necessário.  
  
## <a name="see-also"></a>Consulte também

- [UI Automation Fundamentals](../../../docs/framework/ui-automation/index.md) (Fundamentos da Automação da Interface do Usuário)
