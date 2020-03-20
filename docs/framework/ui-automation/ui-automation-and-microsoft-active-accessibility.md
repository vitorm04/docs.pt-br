---
title: Automação de Interface do usuário e Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 9a84c344ffabdaaa9d0aed68b05b7a4449776789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179989"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automação de Interface do usuário e Microsoft Active Accessibility
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 O Microsoft Active Accessibility foi a solução anterior para tornar os aplicativos acessíveis. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]é o novo modelo de acessibilidade do Microsoft Windows e destina-se a atender às necessidades de produtos de tecnologia assistiva e ferramentas de teste automatizadas. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]oferece muitas melhorias sobre a Acessibilidade Ativa.  
  
 Este tópico inclui as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] principais características e explica como esses recursos diferem da Acessibilidade Ativa.  
  
<a name="Programming_Languages_compare"></a>
## <a name="programming-languages"></a>Linguagens de Programação  
<Acessibilidade Ativa é baseada no Modelo de Objeto Componente (COM) com suporte para interfaces duplas e, portanto, programável em C/C++, Microsoft Visual Basic 6.0 e scripting. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](incluindo a biblioteca do provedor do lado do cliente para controles padrão) é escrita em código gerenciado, e os aplicativos clientes de automação de interface do usuário são mais facilmente programados usando C# ou Visual Basic .NET. Os provedores de automação de interface, que são implementações de interface, podem ser gravados em código gerenciado ou em C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>
## <a name="support-in-windows-presentation-foundation"></a>Suporte na Windows Presentation Foundation  
 O Windows Presentation Foundation (WPF) é o novo modelo para criar interfaces de usuário. Os elementos WPF não contêm suporte nativo à Acessibilidade Ativa; no entanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]eles fazem suporte, o que inclui suporte de ponte para clientes de Acessibilidade Ativa. Somente clientes escritos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] especificamente para podem aproveitar ao máximo os recursos de acessibilidade do WPF, como o rico suporte ao texto.  
  
<a name="Servers_and_Clients_compare"></a>
## <a name="servers-and-clients"></a>Servidores e Clientes  
 Na Acessibilidade Ativa, servidores e clientes se comunicam diretamente, `IAccessible`em grande parte através da implementação do servidor de .  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um serviço principal está entre o servidor (chamado de provedor) e o cliente. O serviço principal faz chamadas para as interfaces implementadas pelos provedores e fornece serviços adicionais, como gerar identificadores de tempo de execução exclusivos para elementos. Os aplicativos clientes usam funções de biblioteca para chamar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] serviço.  
  
 Os provedores de automação de interface do usuário podem fornecer informações aos clientes de acessibilidade ativa e os servidores de acessibilidade ativa podem fornecer informações aos aplicativos clientes de automação de interface do usuário. No entanto, como a Acessibilidade Ativa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]não expõe tantas informações quanto , os dois modelos não são totalmente compatíveis.  
  
<a name="UI_Elements_compare"></a>
## <a name="ui-elements"></a>Elementos da interface do usuário  
 A Acessibilidade [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] Ativa apresenta `IAccessible` elementos como uma interface ou como um identificador infantil. É difícil comparar `IAccessible` dois ponteiros para determinar se eles se referem ao mesmo elemento.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], cada elemento <xref:System.Windows.Automation.AutomationElement> é representado como um objeto. A comparação é feita usando o <xref:System.Windows.Automation.AutomationElement.Equals%2A> operador de igualdade ou o método, ambos comparando os identificadores únicos de tempo de execução dos elementos.  
  
<a name="Tree_Views_and_Navigation_compare"></a>
## <a name="tree-views-and-navigation"></a>Visualizações e navegação de árvores  
 Os [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] elementos na tela podem ser vistos como uma estrutura de árvore com a área de trabalho como raiz, janelas de aplicativos como crianças imediatas e elementos dentro de aplicativos como descendentes adicionais.  
  
 Na Acessibilidade Ativa, muitos elementos de automação que são irrelevantes para os usuários finais são expostos na árvore. Os aplicativos clientes devem olhar para todos os elementos para determinar quais são significativos.  
  
 Os aplicativos clientes de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] automação de interface do usuário veem o através de uma exibição filtrada. A visualização contém apenas elementos de interesse: aqueles que dão informações ao usuário ou permitem a interação. Vistas predefinidas de apenas elementos de controle e apenas elementos de conteúdo estão disponíveis; além disso, os aplicativos podem definir visualizações personalizadas. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]simplifica a tarefa de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] descrever o usuário e ajudar o usuário a interagir com o aplicativo.  
  
 A navegação entre elementos, na Acessibilidade Ativa, é espacial (por exemplo, movendo-se para o elemento que se encontra à esquerda na tela), lógica (por exemplo, movendo-se para o próximo item do menu, ou o próximo item na ordem de guia dentro de uma caixa de diálogo) ou hierárquica ( por exemplo, mover a primeira criança em um recipiente, ou da criança para o pai). A navegação hierárquica é complicada pelo `IAccessible`fato de que elementos infantis nem sempre são objetos que implementam .  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] todos <xref:System.Windows.Automation.AutomationElement> os elementos são objetos que suportam a mesma funcionalidade básica. (Do ponto de vista do provedor, são objetos <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>que implementam uma interface herdada de .) A navegação é principalmente hierárquica: de pais para filhos, e de um irmão para o outro. (A navegação entre irmãos tem um elemento lógico, pois pode seguir a ordem da guia.) Você pode navegar a partir de qualquer ponto de partida, <xref:System.Windows.Automation.TreeWalker> usando qualquer visão filtrada da árvore, usando a classe. Você também pode navegar para determinadas <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A>crianças ou descendentes usando e ; por exemplo, é muito fácil recuperar todos os elementos dentro de uma caixa de diálogo que suportam um padrão de controle especificado.  
  
 A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] navegação é mais consistente do que na Acessibilidade Ativa. Alguns elementos, como listas de paradas e janelas pop-up aparecem duas vezes na árvore De acessibilidade ativa, e a navegação deles pode ter resultados inesperados. Na verdade, é impossível implementar adequadamente a Acessibilidade Ativa para um controle de vergalhões. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]permite reparentar e reposicionar, para que um elemento possa ser colocado em qualquer lugar da árvore, apesar da hierarquia imposta pela propriedade das janelas.  
  
<a name="Roles_and_Control_Types"></a>
## <a name="roles-and-control-types"></a>Funções e tipos de controle  
 A Acessibilidade Ativa `accRole` usa`IAccessible::get_actRole`a propriedade ( ) para recuperar [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]uma descrição do papel do elemento no , como ROLE_SYSTEM_SLIDER ou ROLE_SYSTEM_MENUITEM. O papel de um elemento é a principal pista de sua funcionalidade disponível. A interação com um controle é alcançada `IAccessible::accSelect` `IAccessible::accDoDefaultAction`usando métodos fixos como e . A interação entre o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplicativo cliente e o `IAccessible`é limitada ao que pode ser feito através de .  
  
 Em contraste, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em grande parte desacopla o tipo <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> de controle do elemento (descrito pela propriedade) de sua funcionalidade esperada. A funcionalidade é determinada pelos padrões de controle que são suportados pelo provedor através de sua implementação de interfaces especializadas. Padrões de controle podem ser combinados para descrever o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] conjunto completo de funcionalidade suportada por um elemento específico. Alguns provedores são obrigados a suportar um padrão de controle específico; por exemplo, o provedor de uma caixa de seleção deve suportar o padrão de controle Alternar. Outros provedores são obrigados a suportar um ou mais de um conjunto de padrões de controle; por exemplo, um botão deve suportar alternar ou invocar. Ainda outros não suportam padrões de controle em tudo; por exemplo, um painel que não pode ser movido, redimensionado ou ancorado não tem nenhum padrão de controle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]suporta controles personalizados, que são <xref:System.Windows.Automation.ControlType.Custom> identificados pela propriedade <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> e podem ser descritos pela propriedade.  
  
 A tabela a seguir mostra o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mapeamento das funções de Acessibilidade Ativa para os tipos de controle.  
  
|Função de Acessibilidade Ativa|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tipo de controle|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Botão|  
|ROLE_SYSTEM_CLIENT|Calendário|  
|ROLE_SYSTEM_CHECKBUTTON|Caixa de seleção|  
|ROLE_SYSTEM_COMBOBOX|Caixa de combinação|  
|ROLE_SYSTEM_CLIENT|Personalizado|  
|ROLE_SYSTEM_LIST|Grade de dados|  
|ROLE_SYSTEM_LISTITEM|Item de dados|  
|ROLE_SYSTEM_DOCUMENT|Document|  
|ROLE_SYSTEM_TEXT|Editar|  
|ROLE_SYSTEM_GROUPING|Agrupar|  
|ROLE_SYSTEM_LIST|Cabeçalho|  
|ROLE_SYSTEM_COLUMNHEADER|Item de cabeçalho|  
|ROLE_SYSTEM_LINK|Hyperlink|  
|ROLE_SYSTEM_GRAPHIC|Imagem|  
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
|ROLE_SYSTEM_PAGETABLIST|Tab|  
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
  
 Para obter mais informações sobre os diferentes tipos de controle, consulte [Tipos de Controle de Automação de ICarros](ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>
## <a name="states-and-properties"></a>Estados e Propriedades  
 Na Acessibilidade Ativa, os elementos suportam um conjunto `accState`comum de propriedades, e algumas propriedades (como ) devem descrever coisas muito diferentes, dependendo do papel do elemento. Os servidores devem implementar `IAccessible` todos os métodos de devolução de uma propriedade, mesmo aqueles que não são relevantes para o elemento.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]define muito mais propriedades, algumas das quais correspondem a estados em Acessibilidade Ativa. Alguns são comuns a todos os elementos, mas outros são específicos para controlar tipos e padrões de controle. As propriedades são distinguidas por identificadores únicos, e a <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> maioria <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>das propriedades pode ser recuperada usando um único método, ou . Muitas propriedades também são facilmente <xref:System.Windows.Automation.AutomationElement.Current%2A> <xref:System.Windows.Automation.AutomationElement.Cached%2A> recuperáveis dos acessórios de propriedade.  
  
 Um provedor de automação de ia de usuário não `null` precisa implementar propriedades irrelevantes, mas pode simplesmente devolver um valor para quaisquer propriedades que não suporta. Além disso, o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] serviço principal pode obter algumas propriedades do provedor de janela padrão, e estas são amalgamadas com propriedades explicitamente implementadas pelo provedor.  
  
 Além de suportar muito [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais propriedades, fornece melhor desempenho, permitindo que várias propriedades sejam recuperadas com uma única chamada de processo cruzado.  
  
 A tabela a seguir mostra a correspondência entre as propriedades nos dois modelos.  
  
|Acessório de propriedade de acessibilidade ativa|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ID de propriedade|Comentários|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> ou <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`tem precedência se ambos estão presentes.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Consulte a tabela anterior para mapeamento de funções para tipos de controle.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Válido apenas para tipos de controle que suportam ValuePattern ou RangeValuePattern. Os valores do RangeValue são normalizados para 0-100, para serem consistentes com o comportamento do MSAA. Os itens de valor usam uma string.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Não suportado em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`não possuía uma especificação clara dentro da MSAA, o que resultou em provedores colocando diferentes informações nesta propriedade.|  
|`get_accHelpTopic`|Não suportado em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir mostra quais propriedades correspondem às constantes do estado de acessibilidade ativa.  
  
|Estado de Acessibilidade Ativa|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Aciona a mudança de estado?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Para caixa de seleção,<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Para o botão de rádio,<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|S|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|S|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> ou <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|S|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>para itens de menu|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Verdade <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> e causas<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Verdadeiro|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> e <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> é compatível|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|S|  
  
 Os seguintes estados não foram implementados pela maioria dos [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]servidores de controle de acessibilidade ativa ou não têm equivalente em .  
  
|Estado de Acessibilidade Ativa|Comentários|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Não disponível em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Não disponível em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Não disponível em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_MARQUEED|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_SELFVOICING|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_TRAVERSED|Não disponível em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_ALERT_MEDIUM|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_ALERT_LOW|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_FLOATING|Não amplamente implementado por servidores de acessibilidade ativa|  
|STATE_SYSTEM_HOTTRACKED|Não disponível em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Não disponível em[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Para obter uma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lista completa de identificadores de propriedades, consulte [Visão geral de propriedades de automação de ui](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>
## <a name="events"></a>Eventos  
 O mecanismo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]de evento em , ao contrário do que em Acessibilidade Ativa, não conta com o roteamento de eventos do Windows (que está intimamente ligado com as alças de janela) e não requer o aplicativo cliente para configurar ganchos. As assinaturas para eventos podem ser ajustadas não apenas para eventos específicos, mas para partes específicas da árvore. Os provedores também podem ajustar sua captação de eventos, acompanhando quais eventos estão sendo ouvidos.  
  
 Também é mais fácil para os clientes recuperar os elementos que levantam eventos, pois estes são repassados diretamente para o callback do evento. As propriedades do elemento são automaticamente solicitadas se uma solicitação de cache estiver ativa quando o cliente se inscreveu no evento.  
  
 A tabela a seguir mostra a correspondência [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de Eventos e eventos de Acessibilidade Ativa.  
  
|Winevent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]identificador de eventos|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>mudança de propriedade|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> mudança de propriedade nas barras de rolagem associadas|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Sem equivalente|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Nenhum equivalente exato; talvez <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> ou mudança de propriedade|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>Mudar|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>mudança de propriedade|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>mudança de propriedade|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Não é usado consistentemente em Acessibilidade Ativa. Nenhum evento correspondente diretamente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]é definido em .|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Sem equivalente|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Vários eventos alterados por propriedades|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>e <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> mudou|  
|EVENT_SYSTEM_ALERT|Sem equivalente|  
|EVENT_SYSTEM_CAPTUREEND|Sem equivalente|  
|EVENT_SYSTEM_CAPTURESTART|Sem equivalente|  
|EVENT_SYSTEM_CONTEXTHELPEND|Sem equivalente|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Sem equivalente|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Sem equivalente|  
|EVENT_SYSTEM_DRAGDROPSTART|Sem equivalente|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>mudança de propriedade|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>mudança de propriedade|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>mudança de propriedade|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>mudança de propriedade|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> mudança de propriedade|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> mudança de propriedade|  
|EVENT_SYSTEM_SOUND|Sem equivalente|  
|EVENT_SYSTEM_SWITCHEND|Nenhum equivalente, <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> mas um evento sinaliza que um novo aplicativo recebeu o foco|  
|EVENT_SYSTEM_SWITCHSTART|Sem equivalente|  
|Sem equivalente|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>mudança de propriedade|  
|Sem equivalente|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>mudança de propriedade|  
|Sem equivalente|Evento <xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>|  
|Sem equivalente|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>
## <a name="security"></a>Segurança  
 Alguns `IAccessible` cenários de `IAccessible` personalização exigem embrulhar uma base e chamá-la. Isso tem implicações de segurança, uma vez que um componente parcialmente confiável não deve ser um intermediário em um caminho de código.  
  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelo elimina a necessidade de os provedores ligarem para outro código do provedor. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] serviço central faz toda a agregação necessária.  
  
## <a name="see-also"></a>Confira também

- [Fundamentos de Automação de UI](index.md)
