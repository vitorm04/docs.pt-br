---
title: Automação de Interface do usuário e Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: be7711fdbe9b2cb45d618e685a6f1ae2a941aa29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automação de Interface do usuário e Microsoft Active Accessibility
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] era a solução anterior para tornar aplicativos acessíveis. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] é o novo modelo de acessibilidade para [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] e destina-se para atender às necessidades de produtos de tecnologia assistencial e ferramentas de teste automatizadas. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oferece vários aprimoramentos em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Este tópico inclui os principais recursos do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] e explica como esses recursos diferem do [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Linguagens de programação  
<[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] se baseia o [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] com suporte para interfaces duplas e, portanto, programável em C/C++, [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]e linguagens de script. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (incluindo a biblioteca do provedor do lado do cliente para controles padrão) está escrito em código gerenciado e aplicativos de cliente de automação de interface do usuário são programados com mais facilidade usando c# ou Visual Basic .NET. Provedores de automação de interface do usuário, que são implementações de interface, podem ser escritos em código gerenciado ou C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Suporte no Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) é o novo modelo para a criação de interfaces do usuário. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementos não contêm o suporte nativo para [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]; no entanto, eles dão suporte a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], que inclui suporte para a ponte [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] clientes. Apenas clientes escritos especificamente para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podem se beneficiar dos recursos de acessibilidade do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], como o suporte avançado para texto.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Servidores e clientes  
 Em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], servidores e clientes se comunicam diretamente, amplamente através da implementação do servidor de `IAccessible`.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um serviço principal se encontra entre o servidor (chamado de provedor) e o cliente. O serviço principal faz chamadas para as interfaces implementadas por provedores e fornece serviços adicionais, como a geração de identificadores exclusivos de tempo de execução para elementos. Aplicativos clientes usam funções de biblioteca para chamar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] service.  
  
 Provedores de automação de interface do usuário podem fornecer informações para [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] clientes, e [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores podem fornecer informações para aplicativos clientes de automação de interface do usuário. No entanto, como [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] não expõe tanta informação quanto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], os dois modelos não são totalmente compatíveis.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Elementos da interface do usuário  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] apresenta [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos como um `IAccessible` interface ou um identificador filho. É difícil comparar dois `IAccessible` ponteiros para determinar se eles se referem ao mesmo elemento.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], cada elemento é representado como uma <xref:System.Windows.Automation.AutomationElement> objeto. Comparação é feita usando o operador de igualdade ou o <xref:System.Windows.Automation.AutomationElement.Equals%2A> método, ambos comparam os identificadores exclusivos de tempo de execução dos elementos.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Modos de exibição de árvore e navegação  
 O [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos na tela podem ser vistos como uma estrutura de árvore com a área de trabalho como a raiz, janelas de aplicativos como filhos imediatos e elementos em aplicativos como mais descendentes.  
  
 Em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], muitos elementos de automação que são irrelevantes para os usuários finais são expostos na árvore. Aplicativos clientes precisam examinar todos os elementos para determinar quais são significativos.  
  
 Aplicativos de cliente de automação de interface do usuário consulte o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] por meio de uma exibição filtrada. O modo de exibição contém apenas os elementos de interesse: aqueles que fornecem informações para o usuário ou habilitar a interação. Exibições predefinidas de apenas elementos de controle e apenas os elementos de conteúdo estão disponíveis; Além disso, os aplicativos podem definir modos de exibição personalizados. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] simplifica a tarefa de descrever a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para o usuário e ajudar o usuário interage com o aplicativo.  
  
 Navegação entre elementos, em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], é espacial (por exemplo, mover para o elemento que está à esquerda na tela), lógica (por exemplo, mover para o próximo item de menu ou o próximo item na ordem de tabulação dentro de uma caixa de diálogo), ou hierárquica (para exemplo, mover o primeiro filho em um contêiner, ou de filho para seu pai). Navegação hierárquica é complicada pelo fato de que elementos filhos nem sempre são objetos que implementam `IAccessible`.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos são <xref:System.Windows.Automation.AutomationElement> objetos que dão suporte a mesma funcionalidade básica. (Do ponto de vista do provedor, eles são objetos que implementam uma interface herdada de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Navegação é principalmente hierárquica: de pais para filhos e de um irmão para o próximo. (A navegação entre irmãos tem um elemento lógico, pois ela pode seguir a ordem de tabulação.) Você pode navegar de qualquer ponto inicial, usando qualquer exibição filtrada da árvore, usando o <xref:System.Windows.Automation.TreeWalker> classe. Você também pode navegar para determinados filhos ou descendentes usando <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> e <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; por exemplo, é muito fácil recuperar todos os elementos dentro de uma caixa de diálogo que oferecem suporte a um padrão de controle especificado.  
  
 Navegação no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é mais consistente do que em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Alguns elementos, como listas suspensas e janelas pop-up aparecem duas vezes no [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] árvore e navegação a partir deles podem ter resultados inesperados. É impossível implementar adequadamente [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] para um controle rebar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Habilita a mudança de pai e reposicionamento, para que um elemento pode ser colocado em qualquer lugar na árvore apesar da hierarquia imposta pela propriedade de janelas.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Funções e tipos de controle  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] usa o `accRole` propriedade (`IAccessible::get_actRole`) para recuperar uma descrição da função do elemento no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], como ROLE_SYSTEM_SLIDER ou ROLE_SYSTEM_MENUITEM. A função de um elemento é a dica principal à sua funcionalidade disponível. Interação com um controle é obtida usando métodos fixos como `IAccessible::accSelect` e `IAccessible::accDoDefaultAction`. A interação entre o aplicativo cliente e o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] é limitado a que pode ser feito por meio de `IAccessible`.  
  
 Por outro lado, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] amplamente desassocia o tipo de controle do elemento (descrito pelo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> propriedade) de sua funcionalidade esperada. Funcionalidade é determinada por padrões de controle que são suportados pelo provedor pela sua implementação de interfaces especializadas. Padrões de controle podem ser combinados para descrever o conjunto completo de funcionalidade com suporte em um determinado [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elemento. Alguns provedores são necessários para dar suporte a um determinado padrão de controle; Por exemplo, o provedor para uma caixa de seleção deve oferecer suporte o padrão de controle Toggle. Outros provedores são necessários para dar suporte a um ou mais de um conjunto de padrões de controle; Por exemplo, um botão deve suporte Toggle ou Invoke. Ainda outros não suportam nenhum padrão de controle. Por exemplo, um painel que não pode ser movido, redimensionado ou encaixado não tem nenhum padrão de controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] oferece suporte a controles personalizados, que são identificados pelo <xref:System.Windows.Automation.ControlType.Custom> propriedade e podem ser descritos pelo <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> propriedade.  
  
 A tabela a seguir mostra o mapeamento de [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] funções para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tipos de controle.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Função|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tipo de controle|  
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
  
 Para obter mais informações sobre os diferentes tipos de controle, consulte [tipos de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Estados e propriedades  
 Em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], elementos oferecem suporte a um conjunto comum de propriedades e algumas propriedades (como `accState`) deve descrever coisas muito diferentes, dependendo da função do elemento. Servidores devem implementar todos os métodos de `IAccessible` que retornam uma propriedade, mesmo aqueles que não são relevantes para o elemento.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] define várias propriedades mais, algumas das quais correspondem aos estados em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Alguns são comuns a todos os elementos, mas outras são específicas para tipos de controle e padrões de controle. Propriedades são diferenciadas por identificadores exclusivos, e a maioria das propriedades podem ser recuperadas usando um único método, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Muitas propriedades também são facilmente recuperáveis do <xref:System.Windows.Automation.AutomationElement.Current%2A> e <xref:System.Windows.Automation.AutomationElement.Cached%2A> acessadores de propriedade.  
  
 Um provedor de automação de interface do usuário não tem que implementar propriedades irrelevantes, mas pode simplesmente retornar um `null` valor de qualquer propriedade que não dá suporte. Além disso, o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principal serviço pode obter algumas propriedades do provedor de janela padrão, e essas são mescladas com propriedades explicitamente implementadas pelo provedor.  
  
 Além de suportar muitos mais propriedades [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fornece melhor desempenho, permitindo que várias propriedades sejam recuperadas com uma chamada única entre processos.  
  
 A tabela a seguir mostra a correspondência entre as propriedades nos dois modelos.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] acessador de propriedade|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ID de propriedade|Comentários|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> ou <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` tem precedência se ambos estiverem presentes.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Consulte a tabela anterior para mapeamento de funções para tipos de controle.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Válido somente para tipos de controle que oferecem suporte a ValuePattern ou RangeValuePattern. Valores RangeValue são normalizados para 0-100, para ser consistente com comportamento MSAA. Itens de valor usam uma cadeia de caracteres.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Não tem suporte no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` não tinha uma especificação clara dentro de MSAA, o que resultou em provedores colocassem partes diferentes de informações nessa propriedade.|  
|`get_accHelpTopic`|Não tem suporte no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 A tabela a seguir mostra quais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades correspondem a [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] constantes de estado.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Estado|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Alteração de estado de gatilhos?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Caixa de seleção <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Para o botão de opção <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|S|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|S|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> Ou <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|S|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> itens de menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True e <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> faz com que o <xref:System.Windows.Automation.NoClickablePointException>|N|  
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
  
 Os seguintes estados não foram implementados pela maioria [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] controlar os servidores ou não têm equivalente no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Estado|Comentários|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_MARQUEED|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_SELFVOICING|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_TRAVERSED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_ALERT_MEDIUM|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_ALERT_LOW|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_FLOATING|Não amplamente implementado por [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servidores|  
|STATE_SYSTEM_HOTTRACKED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Não disponível em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Para obter uma lista completa de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identificadores de propriedade, consulte [visão geral de propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Eventos  
 O mecanismo de evento em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], diferente de [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], não se baseia no Windows roteamento de eventos (que é intimamente vinculado a handles de janela) e não requer que o aplicativo cliente configure ganchos. Assinaturas de eventos podem ser ajustadas não apenas para determinados eventos, mas para determinados partes da árvore. Provedores também podem ajustar sua criação de eventos por manter o controle de quais eventos estão sendo atendidos.  
  
 Também é mais fácil para os clientes recuperar os elementos que geram eventos, como eles são passados diretamente para o retorno de chamada do evento. Propriedades do elemento são automaticamente pré-busca se uma solicitação do cache foi ativa quando o cliente assina o evento.  
  
 A tabela a seguir mostra a correspondência de [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents e [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Identificador de evento|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> Alteração de propriedade|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> alteração de propriedade em barras de rolagem associadas|  
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
|EVENT_OBJECT_REORDER|Não usado de forma consistente em [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Nenhum evento diretamente correspondente é definido em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
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
|EVENT_SYSTEM_SWITCHEND|Sem equivalente, mas um <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> evento sinaliza que um novo aplicativo recebeu o foco|  
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
 Alguns `IAccessible` cenários de personalização exigem uma base de encapsulamento `IAccessible` e chamada através dela. Isso tem implicações de segurança, pois um componente parcialmente confiável não deve ser um intermediário em um caminho de código.  
  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelo elimina a necessidade dos provedores chamarem através de outro código de provedor. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principal serviço faz toda a agregação necessária.  
  
## <a name="see-also"></a>Consulte também  
 [UI Automation Fundamentals](../../../docs/framework/ui-automation/index.md) (Fundamentos da Automação da Interface do Usuário)
