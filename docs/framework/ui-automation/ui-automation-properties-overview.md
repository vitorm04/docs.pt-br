---
title: Visão geral das propriedades de automação da interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 8a44fd89017002ae51d9b15a22bac97668d0ff90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179865"
---
# <a name="ui-automation-properties-overview"></a>Visão geral das propriedades de automação da interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Os provedores de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] automação de ui expõem propriedades em elementos. Essas propriedades permitem que os aplicativos clientes de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]automação de interface do usuário descubram informações sobre peças dos controles, especialmente os da statice e dinâmica.  
  
 Esta seção dá uma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ampla visão geral das propriedades. Informações mais específicas são fornecidas nos seguintes tópicos:  
  
- [Automação de Propriedades de Interface de Usuário para Clientes.](ui-automation-properties-for-clients.md)  
  
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a>Identificadores de propriedades  
 Cada propriedade é identificada por um número e um nome. Os nomes das propriedades são usados apenas para depuração e diagnóstico. Os provedores usam os IDs numéricos para identificar solicitações de propriedade recebidas. Os aplicativos cliente, no <xref:System.Windows.Automation.AutomationProperty>entanto, só usam , o que encapsula o número e o nome, para identificar propriedades que desejam recuperar.  
  
 <xref:System.Windows.Automation.AutomationProperty>objetos que representam propriedades particulares estão disponíveis como campos em várias classes. Por razões de segurança, os provedores de automação de ui obtêm esses objetos de um conjunto separado de classes que estão contidos em Uiautomationtypes.dll.  
  
 A tabela a seguir categoriza as <xref:System.Windows.Automation.AutomationProperty>propriedades pelas classes que contêm os IDs.  
  
|Tipos de propriedades|Os clientes obtêm ids de|Provedores obtêm IDs de|  
|-------------------------|--------------------------|----------------------------|  
|Propriedades comuns a todos os elementos (ver tabelas a seguir)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Posição de uma janela de acoplamento|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Estado de um elemento que pode expandir e colapsar|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Propriedades de um item em uma grade|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Propriedades de uma grade|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Visão atual e suportada de um elemento que tem múltiplas visualizações|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Propriedades de um elemento que se move sobre uma gama de valores, como um controle deslizante|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Propriedades de uma janela de rolagem|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Status e contêiner de um item que pode ser selecionado, como em uma lista|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Propriedades de um controle que contém itens de seleção|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Cabeçalhos de coluna e linha de um item em uma tabela|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Cabeçalhos de coluna e linha, e orientação, de uma tabela|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|Estado de um controle alternado|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Capacidades de um elemento que pode ser movido, girado ou redimensionado|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Valor e recursos de leitura/gravação de um elemento que tem um valor|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Capacidades e estado de uma janela|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a>Propriedades por Categoria  
 As tabelas a seguir categorizam as <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElementIdentifiers>propriedades em que as ids são encontradas e . Essas propriedades são comuns a todos os controles. Todos, exceto alguns deles, provavelmente estarão estáticos ao longo da vida útil da aplicação do provedor; a maioria das propriedades dinâmicas estão associadas a padrões de controle.  
  
 A coluna **Acesso ao Imóvel** lista quaisquer outros <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> acessórios <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>para cada propriedade, além de e . Para obter mais informações sobre como obter propriedades em um aplicativo cliente, consulte [Propriedades de automação de interface do usuário para clientes](ui-automation-properties-for-clients.md).  
  
> [!NOTE]
> Para obter informações específicas sobre cada propriedade, siga o link na coluna **Acesso à Propriedade.**  
  
### <a name="display-characteristics"></a>Exibir Características  
  
|Identificador de propriedade|Acesso à propriedade|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|n/d|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>Tipo de elemento  
  
|Identificador de propriedade|Acesso à propriedade|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>Identificação  
  
|Identificador de propriedade|Acesso à propriedade|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Interação  
  
|Identificador de propriedade|Acesso à propriedade|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Suporte para Padrões  
  
|Identificador de propriedade|Acesso à propriedade|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a>Diversos  
  
|Identificador de propriedade|Acesso à propriedade|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a>Localização  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]os provedores devem apresentar as seguintes propriedades na linguagem do sistema operacional:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a>Propriedades e eventos  
 Intimamente ligado com as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades em é o conceito de eventos alterados de propriedade. Para propriedades dinâmicas, o aplicativo cliente precisa de uma maneira de saber que um valor de propriedade mudou, para que ele possa atualizar seu cache de informações ou reagir às novas informações de alguma outra forma.  
  
 Os provedores levantam [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] eventos quando algo nas mudanças. Por exemplo, se uma caixa de seleção for selecionada ou limpa, um evento alterado por propriedade será levantado pela implementação do padrão Alternar pelo provedor. Os provedores podem levantar eventos seletivamente, dependendo se algum cliente está ouvindo eventos ou ouvindo eventos específicos.  
  
 Nem todas as alterações de propriedade levantam eventos; que depende inteiramente da implementação do provedor de Automação de IU para o elemento. Por exemplo, os provedores proxy padrão para caixas <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> de lista não levantam um evento quando as alterações. Neste caso, a aplicação deve, <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>em vez disso, ouvir um .  
  
 Os clientes ouvem os eventos assinando-os. Subscrever eventos significa criar métodos de delegação que possam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lidar com os eventos e, em seguida, passar os métodos para juntamente com os eventos específicos que serão tratados nesses métodos. Para eventos alterados por propriedade, <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>em particular, os clientes devem implementar .  
  
## <a name="see-also"></a>Confira também

- [Armazenando em cache em clientes de automação de interface do usuário](caching-in-ui-automation-clients.md)
- [Automação de Propriedades de Interface de Usuário para Clientes.](ui-automation-properties-for-clients.md)
- [Implementação de provedor de Automação da Interface do Usuário no lado do servidor](server-side-ui-automation-provider-implementation.md)
- [Localizar um elemento de automação de interface do usuário com base na condição de uma propriedade](find-a-ui-automation-element-based-on-a-property-condition.md)
- [Retornando Propriedades de um Provedor de Automação de IU](return-properties-from-a-ui-automation-provider.md)
- [Disparar Eventos de um Provedor de Automação UI](raise-events-from-a-ui-automation-provider.md)
