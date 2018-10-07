---
title: Suporte de automação de interface de usuário para o Tipo de Controle Image
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Image control type
- control types, Image
- Image control type
ms.assetid: 4e0eeefb-e09b-46d2-b83b-0a7e35543ab8
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 8e2d1e6774c6a8c00478bdb89bf541bb47a8a8a5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847277"
---
# <a name="ui-automation-support-for-the-image-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Image
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de imagem. Na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Controles de imagem usados como ícones, elementos gráficos informativos e gráficos dará suporte ao tipo de controle de imagem. Os controles usados como plano de fundo ou imagens de marca d'água não suportará o tipo de controle de imagem.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle de imagem, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de imagem, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação de interface do usuário necessária  
 A tabela a seguir mostra a visualização de controle e exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore que pertence aos controles de imagem e descreve o que podem estar contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Modo de exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Image|Imagem (depende se a imagem contém informações (com base no valor de `IsContentElement` propriedade))|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessária  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para a imagem do tipo de controle. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade precisa ser exclusivo entre todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Ponto clicável do controle de imagem deve ser um ponto dentro do retângulo delimitador do controle de imagem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, ele deve oferecer suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|A propriedade de nome deve ser exposta para todos os controles de imagem que contêm informações. Acesso programático a essas informações requer que um equivalente textual para o gráfico a ser fornecido. Se o controle de imagem é puramente decorativo, ele somente deve aparecer na exibição do controle a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore e não é necessário ter um nome. Estruturas de interface do usuário devem oferecer suporte a um ALT ou alternativo de propriedade de texto em imagens que podem ser definidas de dentro do framework. Essa propriedade, em seguida, será mapeado para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedade Name.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Se houver um rótulo de texto estático, em seguida, essa propriedade deve expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Image|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"imagem"|Cadeia de caracteres localizada correspondente ao tipo de controle de imagem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Consulte as observações.|O controle de imagem deve ser incluído na exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore quando ele contém informações significativas que não estiverem expostas ao usuário final.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de imagem é sempre incluído na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Consulte as observações.|A propriedade HelpText expõe uma cadeia de caracteres localizada que descreve a aparência visual real do controle (por exemplo, um quadrado vermelho com um 'X' branco) ou outras informações de dica de ferramenta associado à imagem.<br /><br /> Essa propriedade deve ser suportada quando uma descrição longa é necessária para transmitir mais informações sobre o controle de imagem. Por exemplo, um gráfico complicado ou um diagrama. Essa propriedade é mapeado para a marca HTML LongDesc e a marca Desc Scalable Vector Graphics (SVG). Os desenvolvedores que trabalham com controles de imagem devem dar suporte a uma propriedade para permitir que a descrição do visual a ser definido no controle. Essa propriedade deve ser mapeada para a propriedade VisualDescription de automação de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Consulte as observações.|Se o controle de imagem representa informações de estado sobre um item específico na tela, o controle deve estar contido dentro do item. Quando a imagem está contida dentro de um item o item deve dar suporte a propriedade status e gerar notificações apropriadas quando o status é alterado.<br /><br /> Se uma imagem é um controle autônomo e transmite status essa propriedade deve ser suportada.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessária  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões devem ser suportados por todos os controles de imagem de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Depende|O controle de imagem compatível com o padrão de Item de grade se o controle estiver dentro de um contêiner de grade.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Depende|O controle de imagem compatível com o padrão de Item de tabela se o controle estiver dentro de um contêiner que tem controles de cabeçalho.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Nunca|Se o controle de imagem contém uma imagem que pode ser clicada, o controle deve dar suporte a um tipo de controle que suporta o padrão de Invoke, como o tipo de controle de botão.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Nunca|Controles de imagem não devem suportar o padrão de Item de seleção.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessária  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos devem ser suportados por todos os controles de imagem. Para obter mais informações sobre eventos, consulte [visão geral de eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Nunca|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Nunca|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Nunca|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Nunca|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.Image>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
