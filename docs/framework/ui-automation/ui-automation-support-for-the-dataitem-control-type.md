---
title: Suporte de automação de interface de usuário para o tipo de controle DataItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: 6263d7777becc1042cf477503c7f68af29fa7f4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125205"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle DataItem
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para o tipo de controle DataItem. Na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] um tipo de controle é um conjunto de condições que um controle deve atender para usar o <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 Uma entrada em uma lista de contatos é um exemplo de um controle de item de dados. Um controle de item de dados contém informações que são de interesse para o usuário final. É mais complicado do que o item de lista simples porque ele contém informações mais detalhadas.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle DataItem, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os dados de controles de item, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação de interface do usuário necessária  
 A tabela a seguir mostra a visualização de controle e exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore que pertence ao item de dados controla e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - modo de exibição de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -Varia (0 ou mais; pode ser estruturado de hierarquia)|DataItem<br /><br /> -Varia (0 ou mais; pode ser estruturado de hierarquia)|  
  
 Um elemento de item de dados em uma grade de dados pode hospedar uma variedade de objetos, incluindo outra camada de itens de dados ou elementos de grade específico, como texto, imagens, ou controles de edição. Se o elemento de item de dados possui uma função de objeto específico, o elemento deve ser exposto como um tipo de controle específicos; Por exemplo, um item de lista Tipo de controle para um item de dados podem ser selecionados na grade.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessária  
 A tabela a seguir lista as propriedades cujo valor ou definição são especialmente relevantes para os controles de item de dados. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriedade|Valor|Observações|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade precisa ser exclusivo entre todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Suporte se houver um retângulo delimitador. Se não for todo ponto dentro do retângulo delimitador é clicável, e você executar o teste de hit especializado, substituir e fornece um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O controle de item de dados deve sempre ser conteúdo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O controle de item de dados sempre deve ser um controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, ele deve oferecer suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Consulte as observações.|Se o controle contém um status que está sendo atualizado dinamicamente, em seguida, essa propriedade deve ser suportada para que uma tecnologia assistencial possa receber atualizações quando o status do elemento é alterado.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Consulte as observações.|Esse é o valor de cadeia de caracteres que transmite para o usuário final, o objeto subjacente que representa o item. Os exemplos são "Arquivo de mídia" ou "Contato".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Controles de item de dados não tem um rótulo de texto estático.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"item de dados"|Cadeia de caracteres localizada correspondente ao tipo de controle DataItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O controle de item de dados sempre contém um elemento de texto primário que está relacionado ao que o usuário associaria como o identificador mais semântico para o item.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessária  
 A seguinte tabela lista o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] padrões devem ser suportados por todos os controles de item de dados de controle. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Depende|Se o item de dados pode ser expandido ou recolhido para mostrar e ocultar informações, o padrão de expandir recolher deve ser suportado.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Depende|Itens de dados irá suportar o padrão de Item de grade quando uma coleção de itens de dados está disponível em um contêiner que pode ser navegada espacialmente item a item.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Depende|Todos os itens de dados dão suporte a capacidade de ser rolado para a exibição com o padrão de Item de rolagem quando seu contêiner de dados tem mais itens que pode caber na tela.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Sim|Todos os itens de dados devem suportar o padrão de Item de seleção para indicar quando o item está selecionado.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Depende|Se o item de dados está contido dentro de um tipo de controle de grade de dados, em seguida, ele dará suporte a esse padrão.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Depende|Se o item de dados contiver um estado que pode ser alternado em.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Depende|Se o texto primário do item de dados é editável e em seguida, o valor padrão deve ser suportado.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Trabalhando com itens de dados em listas grandes  
 Listas grandes geralmente são virtualizadas dentro [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estruturas para ajudar no desempenho. Devido a isso, um cliente de automação de interface do usuário não é possível usar o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] recurso de consulta para extrair o conteúdo da árvore inteira da mesma forma que ele pode em outros contêineres de itens. Um cliente deve rolar o item na exibição (ou expanda o controle para mostrar todas as opções de valiosas) antes de acessar o conjunto completo de informações do item de dados.  
  
 Ao chamar `SetFocus` sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento para o item de dados, o [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] caso retornará com êxito e fazer com que o foco seja definido para a edição dentro da subárvore do item de dados.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessária  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos devem ser suportados por todos os controles de item de dados. Para obter mais informações sobre eventos, consulte [visão geral de eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> evento de propriedade alterada.|Depende|Nenhum|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>Exemplo de tipo de controle DataItem  
 A imagem a seguir ilustra um tipo de controle DataItem em um controle de exibição de lista com suporte para informações avançadas para as colunas.  
  
 ![Gráfico de um controle de exibição de lista com dois itens de dados](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 O modo de exibição de controle e exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore que diz respeito ao controle de item de dados é exibida abaixo. Os padrões de controle para cada elemento de automação são mostrados entre parênteses. O grupo de "Contoso" também é parte da grade do controle de host de grade de dados.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - modo de exibição de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grupo "Contoso" (tabela, grade)<br />-DataItem "contas Receivable.doc" (item de tabela, GridItem, SelectionItem, Invoke)<br />-Image "Contas Receivable.doc"<br />-Edite "Name" (valor do item de tabela, GridItem, "Contas Receivable.doc")<br />-Edite "Data de modificação" (valor do item de tabela, GridItem, "25/8/2006 3:29 PM")<br />-Edite "Tamanho" (valor de GridItem, TableItem, "11.0 KB)<br />-DataItem "contas Payable.doc" (item de tabela, GridItem, SelectionItem, Invoke)<br />-   ...|-Grupo "Contoso" (tabela, grade)<br />-DataItem "contas Receivable.doc" (item de tabela, GridItem, SelectionItem, Invoke)<br />-Image "Contas Receivable.doc"<br />-Edite "Name" (valor do item de tabela, GridItem, "Contas Receivable.doc")<br />-Edite "Data de modificação" (valor do item de tabela, GridItem, "25/8/2006 3:29 PM")<br />-Edite "Tamanho" (valor de GridItem, TableItem, "11.0 KB)<br />-DataItem "contas Payable.doc" (item de tabela, GridItem, SelectionItem, Invoke)<br />-   …|  
  
 Se uma grade representa uma lista de itens selecionáveis, os elementos de interface do usuário correspondentes podem ser expostos pelo tipo de controle ListItem em vez do tipo de controle DataItem. No exemplo anterior, os elementos de DataItem ("Receivable.doc contas" e "Contas Payable.doc") no grupo ("Contoso") podem ser melhorados com expô-los como tipos de controle ListItem porque esse tipo já suporta o padrão de controle SelectionItem.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.ControlType.DataItem>
- [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
