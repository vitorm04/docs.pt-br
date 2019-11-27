---
title: Suporte de automação de interface de usuário para o Tipo de Controle Edit
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 500dc450ad171ed50316c8e08d62258d745049cb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448464"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Suporte de automação de interface de usuário para o Tipo de Controle Edit

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).

Este tópico fornece informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporte para o tipo de controle de edição. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar a propriedade <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore, valores de propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] e padrões de controle.

Os controles de edição permitem que um usuário exiba e edite uma linha de texto simples sem suporte a formatação avançada.

As seções a seguir definem a estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], propriedades, padrões de controle e eventos necessários para o tipo de controle de edição. Os requisitos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplicam a todos os controles de edição, sejam [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária

A tabela a seguir descreve a exibição de controle e a exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertence a controles de edição e descreve o que pode ser contido em cada exibição. Para obter mais informações sobre a árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md).

|Exibição de controle|Exibição de conteúdo|
|------------------|------------------|
|Editar|Editar|

Os controles que implementam o tipo de controle de edição sempre terão zero barras de rolagem na exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] porque ele é um controle de linha única. A única linha de texto pode ser encapsulada em alguns cenários de layout. O tipo de controle de edição é mais adequado para conter pequenas quantidades de texto editável ou selecionável.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias

A tabela a seguir lista as propriedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cujo valor ou definição é especialmente relevante para os controles de edição. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).

|Propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valor|{1&gt;Observações&lt;1}|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|O controle de edição deve ter um ponto clicável que forneça o foco de entrada para a parte de edição do controle quando um usuário clica no mouse lá.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte observações.|O nome do controle de edição normalmente é gerado a partir de um rótulo de texto estático. Se não houver um rótulo de texto estático, um valor de propriedade para `Name` deverá ser atribuído pelo desenvolvedor do aplicativo. A propriedade `Name` nunca deve conter o conteúdo textual do controle de edição.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte observações.|Se houver um rótulo de texto estático associado ao controle, essa propriedade deverá expor uma referência a esse controle. Se o controle de texto for um subcomponente de outro controle, ele não terá um conjunto de propriedades `LabeledBy`.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Editar|Esse valor é o mesmo para todas as estruturas de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|editar|Cadeia de caracteres localizada correspondente ao tipo de controle de edição.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de edição é sempre incluído na exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de edição é sempre incluído na exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Consulte observações.|Deve ser definido como true em controles de edição que contêm senhas. Se um controle de edição contiver conteúdo de senha, essa propriedade poderá ser usada por um leitor de tela para determinar se os pressionamentos de tecla devem ser lidos conforme o usuário os digita.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Propriedades e padrões de controle de automação da interface do usuário necessários

A tabela a seguir lista os padrões de controle necessários para serem suportados por todos os controles de edição. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).

|Propriedade padrão de controle/padrão de controle|Suporte/valor|{1&gt;Observações&lt;1}|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Dependem|Os controles de edição devem dar suporte ao padrão de controle de texto porque as informações detalhadas do texto devem estar sempre disponíveis para os clientes.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Dependem|Todos os controles de edição que usam uma cadeia de caracteres devem expor o padrão de valor.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Consulte observações.|Essa propriedade deve ser definida para indicar se o controle pode ter um valor definido programaticamente ou é editável pelo usuário.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Consulte observações.|Essa propriedade retornará o conteúdo textual do controle de edição. Se a `IsPasswordProperty` for definida como `true`, essa propriedade deverá gerar uma `InvalidOperationException` quando solicitado.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Dependem|Todos os controles de edição que usam um intervalo numérico devem expor o padrão de controle de valor de intervalo.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Consulte observações.|Essa propriedade deve ser o menor valor ao qual o conteúdo do controle de edição pode ser definido.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Consulte observações.|Essa propriedade deve ser o maior valor ao qual o conteúdo do controle de edição pode ser definido.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Consulte observações.|Essa propriedade deve indicar o número de casas decimais às quais o valor pode ser definido. Se a edição usar apenas inteiros, o `SmallChangeProperty` deverá ser 1. Se a edição levar um intervalo de 1,0 a 2,0, o `SmallChangeProperty` deverá ser 0,1. Se o controle de edição usa um intervalo de 1, 0 a 2, 0, o `SmallChangeProperty` deve ser 0, 1.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Essa propriedade não precisa ser exposta em um controle de edição.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Consulte observações.|Essa propriedade indicará o conteúdo numérico do controle de edição. Quando um valor mais preciso é definido por um cliente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dentro dos intervalos especificados nas propriedades `Minimum` e `Maximum`, a propriedade valor será automaticamente arredondada para o valor aceito mais próximo.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários

A tabela a seguir lista os eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de edição. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento|Suporte|{1&gt;Observações&lt;1}|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> evento de alteração de propriedade.|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> evento de alteração de propriedade.|Dependem|Nenhum|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> evento de alteração de propriedade.|{1&gt;Nunca&lt;1}|Nenhum|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> evento de alteração de propriedade.|{1&gt;Nunca&lt;1}|Nenhum|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> evento de alteração de propriedade.|{1&gt;Nunca&lt;1}|Nenhum|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> evento de alteração de propriedade.|{1&gt;Nunca&lt;1}|Nenhum|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> evento de alteração de propriedade.|{1&gt;Nunca&lt;1}|Nenhum|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> evento de alteração de propriedade.|{1&gt;Nunca&lt;1}|Nenhum|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> evento de alteração de propriedade.|Dependem|Se o controle oferecer suporte ao padrão de controle de valor de intervalo, ele deverá dar suporte a esse evento.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType.Edit>
- [Visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
