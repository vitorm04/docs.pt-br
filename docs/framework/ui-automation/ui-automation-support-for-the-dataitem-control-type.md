---
title: Suporte de automação de interface de usuário para o tipo de controle DataItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: fc41b3eb775e80ae85026b226a60ce6a1d31c761
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123108"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle DataItem
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para o tipo de controle DataItem. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] um tipo de controle é um conjunto de condições que um controle deve atender para usar a propriedade <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Uma entrada em uma lista de contatos é um exemplo de controle de item de dados. Um controle de item de dados contém informações de interesse de um usuário final. É mais complicado do que o item de lista simples, pois contém informações mais ricas.  
  
 As seções a seguir definem a estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], propriedades, padrões de controle e eventos necessários para o tipo de controle DataItem. Os requisitos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se aplicam a todos os controles de item de dados, sejam [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação da interface do usuário necessária  
 A tabela a seguir descreve a exibição de controle e a exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertence a controles de item de dados e descreve o que pode ser contido em cada exibição. Para obter mais informações sobre a árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md).  
  
|Árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-exibição de controle|Árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -Varia (0 ou mais; pode ser estruturado na hierarquia)|DataItem<br /><br /> -Varia (0 ou mais; pode ser estruturado na hierarquia)|  
  
 Um elemento de item de dados em uma grade de dados pode hospedar uma variedade de objetos, incluindo outra camada de itens de dados ou elementos de grade específicos, como texto, imagens ou controles de edição. Se o elemento de item de dados tiver uma função de objeto específica, o elemento deverá ser exposto como um tipo de controle específico; por exemplo, um tipo de controle de ListItem para um item de dados selecionável na grade.  
  
## <a name="required-ui-automation-properties"></a>Propriedades de automação da interface do usuário necessárias  
 A tabela a seguir lista as propriedades cujo valor ou definição é especialmente relevante para os controles de item de dados. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades, consulte [Propriedades de automação da interface do usuário para clientes](ui-automation-properties-for-clients.md).  
  
|propriedade|Valor|Anotações|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte observações.|O valor dessa propriedade precisa ser exclusivo em todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte observações.|Com suporte se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis e você executar um teste de clique especializado, substitua e forneça um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de item de dados sempre deve ser conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de item de dados sempre deve ser um controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte observações.|Se o controle puder receber o foco do teclado, ele deverá dar suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Consulte observações.|Se o controle contiver o status que está sendo atualizado dinamicamente, essa propriedade deverá ter suporte para que uma tecnologia assistencial possa receber atualizações quando o status do elemento for alterado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Consulte observações.|Esse é o valor da cadeia de caracteres que transmite ao usuário final o objeto subjacente que o item representa. Os exemplos são "arquivo de mídia" ou "contato".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Os controles de item de dados não têm um rótulo de texto estático.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"item de dados"|Cadeia de caracteres localizada correspondente ao tipo de controle DataItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte observações.|O controle item de dados sempre contém um elemento de texto primário relacionado ao que o usuário iria associar como o identificador mais semântico para o item.|  
  
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação da interface do usuário necessários  
 A tabela a seguir lista os padrões de controle de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de item de dados. Para obter mais informações sobre padrões de controle, consulte [visão geral dos padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Anotações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Dependem|Se o item de dados puder ser expandido ou recolhido para mostrar e ocultar informações, o padrão expandir recolhimento deverá ter suporte.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Dependem|Os itens de dados oferecerão suporte ao padrão de item de grade quando uma coleção de itens de dados estiver disponível dentro de um contêiner que pode ter uma navegação espacial de item para item.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Dependem|Todos os itens de dados dão suporte à capacidade de serem rolados para o modo de exibição com o padrão de item de rolagem quando o contêiner de dados tem mais itens do que pode caber na tela.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Sim|Todos os itens de dados devem oferecer suporte ao padrão de item de seleção para indicar quando o item está selecionado.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Dependem|Se o item de dados estiver contido em um tipo de controle de grade de dados, ele dará suporte a esse padrão.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Dependem|Se o item de dados contiver um estado que possa ser alternado por meio de.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Dependem|Se o texto principal do item de dados for editável, o padrão de valor deverá ser suportado.|  
  
## <a name="working-with-data-items-in-large-lists"></a>Trabalhando com itens de dados em listas grandes  
 As listas grandes geralmente são dados virtualizados em estruturas [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para auxiliar no desempenho. Devido a isso, um cliente de automação de interface do usuário não pode usar o recurso de consulta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para refazer o conteúdo da árvore completa da mesma maneira que pode em outros contêineres de item. Um cliente deve rolar o item para a exibição (ou expandir o controle para mostrar todas as opções valiosas) antes de acessar o conjunto completo de informações do item de dados.  
  
 Ao chamar `SetFocus` no elemento [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para o item de dados, o caso do Microsoft Windows Explorer retornará com êxito e fará com que o foco seja definido para a edição dentro da subárvore do item de dados.  
  
## <a name="required-ui-automation-events"></a>Eventos de automação da interface do usuário necessários  
 A tabela a seguir lista os eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] necessários para serem suportados por todos os controles de item de dados. Para obter mais informações sobre eventos, consulte [visão geral dos eventos de automação da interface do usuário](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento|Suporte|Anotações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> evento de alteração de propriedade.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> evento de alteração de propriedade.|Dependem|Nenhum|  
  
## <a name="dataitem-control-type-example"></a>Exemplo de tipo de controle DataItem  
 A imagem a seguir ilustra um tipo de controle DataItem em um controle de exibição de lista com suporte para informações avançadas para as colunas.  
  
 ![Gráfico de um controle de exibição de lista com dois itens de dados](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 A exibição de controle e a exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertencem ao controle de item de dados é exibida abaixo. Os padrões de controle para cada elemento de automação são mostrados entre parênteses. O grupo "contoso" também faz parte da grade do controle de host de grade de dados.  
  
|Árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-exibição de controle|Árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grupo "contoso" (tabela, grade)<br />-DataItem "contas a receber. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Imagem "contas a receber. doc"<br />-Edite "Name" (TableItem, GridItem, valor "contas a receber. doc")<br />-Editar "data de modificação" (TableItem, GridItem, valor "8/25/2006 3:29 PM")<br />-Edite "tamanho" (GridItem, TableItem, valor "11,0 KB)<br />-DataItem "contas a pagar. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   ...|-Grupo "contoso" (tabela, grade)<br />-DataItem "contas a receber. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Imagem "contas a receber. doc"<br />-Edite "Name" (TableItem, GridItem, valor "contas a receber. doc")<br />-Editar "data de modificação" (TableItem, GridItem, valor "8/25/2006 3:29 PM")<br />-Edite "tamanho" (GridItem, TableItem, valor "11,0 KB)<br />-DataItem "contas a pagar. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />- ...|  
  
 Se uma grade representar uma lista de itens selecionáveis, os elementos da interface do usuário correspondentes poderão ser expostos com o tipo de controle ListItem em vez do tipo de controle DataItem. No exemplo anterior, os elementos de DataItem ("contas a receber. doc" e "contas a pagar. doc") em grupo ("contoso") podem ser aprimorados expondo-os como tipos de controle de ListItem porque esse tipo já dá suporte ao padrão de controle SelectionItem.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType.DataItem>
- [Visão geral de tipos de controle de automação da interface do usuário](ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
