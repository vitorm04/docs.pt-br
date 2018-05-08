---
title: Suporte de automação de interface de usuário para o Tipo de Controle Edit
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0cd1744702448836e6b4e1eb04d14725a1baba39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Edit
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de edição. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle precisa atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Controles de edição de permitem que um usuário exibir e editar uma linha de texto sem suporte à formatação de rich.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle de edição, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os controles de edição, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessário  
 A tabela a seguir descreve o modo de exibição de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore que pertence aos controles de edição e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Exibição de controle|Exibição de conteúdo|  
|------------------|------------------|  
|Editar|Editar|  
  
 Os controles que implementam o tipo de controle de edição sempre terá zero barras de rolagem na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore porque ele é um controle de linha única. A única linha de texto pode ser quebrado em alguns cenários de layout. O tipo de controle de edição é mais adequado para manter pequenas quantidades de texto editável ou selecionável.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades cujos valores ou definição são especialmente relevantes para controles de edição. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedade|Valor|Observações|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade deve ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|O controle de edição deve ter um ponto clicável que dá foco de entrada para a parte de edição do controle quando um usuário clica o mouse ali.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, deve suportar essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|Normalmente, o nome do controle de edição é gerado de um rótulo de texto estático. Se não houver um rótulo de texto estático, um valor de propriedade para `Name` deve ser atribuído pelo desenvolvedor do aplicativo. O `Name` propriedade nunca deve conter o conteúdo textual do controle de edição.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Se houver um rótulo de texto estático associado ao controle, essa propriedade deve expor uma referência para esse controle. Se o controle de texto é um subcomponente do outro controle, ele não terá um `LabeledBy` conjunto de propriedades.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Editar|Esse valor é o mesmo para todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estruturas.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"edit"|Cadeia de caracteres localizada correspondente ao tipo de controle de edição.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de edição é sempre incluído na exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de edição é sempre incluído na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Consulte as observações.|Deve ser definido como verdadeiro em controles que contêm as senhas de edição. Se um controle de edição contiver conteúdos de senha, em seguida, essa propriedade pode ser usada por um leitor de tela para determinar se pressionamentos de tecla devem ser lidas como os tipos de usuário-los.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Padrões de controle de automação de interface do usuário e propriedades necessários  
 A tabela a seguir lista os padrões de controle devem ser suportados por todos os controles de edição. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Propriedade de padrão de controle/padrão de controle|Valor do suporte|Observações|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Depende|Controles de edição devem dar suporte o padrão de controle de texto porque as informações detalhadas de texto devem estar sempre disponíveis para clientes.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Depende|Todos os controles de edição que usam uma cadeia de caracteres devem expor o padrão de valor.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Consulte as observações.|Essa propriedade deve ser definida para indicar se o controle pode ter um valor definido programaticamente ou pode ser editado pelo usuário.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Consulte as observações.|Esta propriedade retornará o conteúdo textual do controle de edição. Se o `IsPasswordProperty` é definido como `true`, esta propriedade deve lançar um `InvalidOpertaionException` quando solicitado.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Depende|Todos os controles de edição que levam um intervalo numérico devem expor o padrão de controle de valor de intervalo.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Consulte as observações.|Essa propriedade deve ser o menor valor que o conteúdo do controle de edição pode ser definido.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Consulte as observações.|Essa propriedade deve ser o maior valor que o conteúdo do controle de edição pode ser definido.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Consulte as observações.|Esta propriedade deve indicar o número de casas decimais que o valor pode ser definido como. Se a edição apenas receber inteiros, o `SmallChangeProperty` deve ser 1. Se a edição receber uma faixa de 1.0, 2.0, o `SmallChangeProperty` deve ser 0.1. Se o controle de edição recebe uma faixa de 1.00 a 2.00 o `SmallChangeProperty` deve ser 0.001.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Essa propriedade não precisa ser exposta em um controle de edição.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Consulte as observações.|Essa propriedade indicará o conteúdo numérico do controle de edição. Quando um valor mais preciso é definido um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cliente dentro dos intervalos especificados no `Minimum` e `Maximum` propriedades, o valor da propriedade automaticamente será arredondada para o valor mais próximo aceito.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessário  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos que devem ser suportados por todos os controles de edição. Para obter mais informações sobre eventos, consulte [visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> evento de propriedade alterada.|Nunca|Nenhum|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> evento de propriedade alterada.|Depende|Se o controle suporta o padrão de controle de valor de intervalo, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
