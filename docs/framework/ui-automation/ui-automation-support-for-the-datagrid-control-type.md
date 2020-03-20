---
title: Suporte de automação de interface de usuário para o tipo de controle DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 69532c9836876c25e9f31395213b1a89e0307dcd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179798"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle DataGrid
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico fornece [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informações sobre suporte para o tipo de controle DataGrid. Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve cumprir para usar o `ControlType` imóvel. As condições incluem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diretrizes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] específicas para a estrutura das árvores, valores de propriedade e padrões de controle.  
  
 O tipo de controle DataGrid permite que um usuário trabalhe facilmente com itens que contenham metadados representados em colunas. Os controles de grade de dados têm linhas de itens e colunas de informações sobre esses itens. Um controle de exibição de lista no Microsoft Vista Explorer é um exemplo que suporta o tipo de controle DataGrid.  
  
 As seções a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir definem a estrutura da árvore necessária, propriedades, padrões de controle e eventos para o tipo de controle DataGrid. Os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]todos os controles de grade de dados, se , Win32 ou Formulários Windows.  
  
## <a name="required-ui-automation-tree-structure"></a>Estrutura da árvore de automação de iui necessária  
 A tabela a seguir mostra a exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de controle e a exibição de conteúdo da árvore que diz respeito aos controles da grade de dados e descreve o que pode ser contido em cada exibição. Para obter mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações sobre a árvore, consulte Visão geral da [árvore de automação de ui](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore - Visualização de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore - Exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Cabeçalho (0, 1 ou 2)<br /><br /> <ul><li>CabeçalhoItem (número de colunas ou linhas)</li></ul></li><li>DataItem (0 ou mais; pode ser estruturado em hierarquia)</li></ul>|DataGrid<br /><br /> - DataItem (0 ou mais; pode ser estruturado em hierarquia)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Propriedades de automação de ui necessárias  
 A tabela a seguir lista as propriedades cujo valor ou definição é especialmente relevante para os controles da grade de dados. Para obter [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mais informações sobre propriedades, consulte [Propriedades de Automação de Interface do Usuário para Clientes](ui-automation-properties-for-clients.md).  
  
|Propriedade|Valor|Observações|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Veja as notas.|O valor desta propriedade precisa ser único em todos os controles em uma aplicação.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Veja as notas.|O retângulo mais externo que contém todo o controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Veja as notas.|Suportado se houver um retângulo delimitador. Se nem todos os pontos dentro do retângulo delimitador forem clicáveis, e você realizar testes especializados de acerto, então anular e fornecer um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Este valor é o mesmo para todas as estruturas de IA.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|O valor desta propriedade deve ser sempre verdadeiro. Isso significa que o controle da grade de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dados deve estar sempre na visão de conteúdo da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|O valor desta propriedade deve ser sempre verdadeiro. Isso significa que o controle da grade de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dados deve estar sempre na visão de controle da árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Veja as notas.|Se o controle puder receber foco no teclado, ele deve suportar esta propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Veja as notas.|Se houver um rótulo de texto estático, então esta propriedade deve expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Grade de dados"|Seqüência localizada correspondente ao tipo de controle DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Veja as notas.|O controle da grade de dados `Name` normalmente obtém o valor de sua propriedade a partir de um rótulo de texto estático. Se não houver um rótulo de texto estático, um `Name` desenvolvedor de aplicativos deve atribuir um valor para a propriedade. O valor `Name` da propriedade nunca deve ser o conteúdo textual do controle de edição.|  
  
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de icarros necessários  
 A tabela a seguir lista os padrões de controle necessários para serem suportados por todos os controles de grade de dados. Para obter mais informações sobre padrões de controle, consulte [Visão geral dos padrões de controle de automação de ui](ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Sim|O controle da grade de dados em si sempre suporta o padrão de controle de Grade porque os itens que ele contém metadados que são dispostos em uma grade.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|A capacidade de rolar a grade de dados depende do conteúdo e se as barras de rolagem estão presentes.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Depende|A capacidade de selecionar a grade de dados depende do conteúdo.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Sim|O controle da grade de dados sempre tem um cabeçalho dentro de sua subárvore, de modo que o padrão de controle de tabela deve ser suportado.|  
  
 Os itens de dados dentro dos contêineres da grade de dados serão suportados no mínimo:  
  
- Padrão de controle de itens de seleção (se a grade de dados for selecionável)  
  
- Padrão de controle de itens de rolagem (se a grade de dados for rolável)  
  
- Padrão de controle de itens de grade  
  
- padrão de controle Item de Tabela  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Eventos de automação de ui obrigatórios  
 A tabela a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] seguir lista os eventos necessários para serem suportados por todos os controles de grade de dados. Para obter mais informações sobre eventos, consulte Visão geral de [eventos de automação de ui](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>evento alterado de propriedade.|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obrigatório|Nenhum|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>evento alterado de propriedade.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Scroll, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Scroll, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Scroll, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Scroll, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Scroll, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>evento alterado de propriedade.|Depende|Se o controle suportar o padrão Scroll, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Obrigatório|Nenhum|  
  
## <a name="date-grid-control-type-example"></a>Exemplo do tipo de controle da grade de data  
 A imagem a seguir ilustra um controle De exibição de lista que implementa o tipo de controle DataGrid.  
  
 ![Gráfico de um controle de exibição de lista com dois itens de dados](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 A exibição de controle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] e a exibição de conteúdo da árvore que pertence ao controle 'Exibição de lista' é exibida abaixo. Os padrões de controle para cada elemento de automação são mostrados entre parênteses.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore - Visualização de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Árvore - Exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (Tabela, Grade, Seleção)</li><li>Cabeçalho<br /><br /> <ul><li>CabeçalhoItem "Nome" (Invocar)</li><li>CabeçalhoItem "Data Modificada" (Invocar)</li><li>CabeçalhoItem "Tamanho" (Invocar)</li></ul></li><li>Grupo "Contoso" (TableItem, GridItem, SelectionItem,\*Table*, Grid )<br /><br /> <ul><li>DataItem "Contas a receber.doc" (SelectionItem, Invoke,\*TableItem\*, GridItem )</li><li>DataItem "Contas a pagar.doc" (SelectionItem,\*Invoke, TableItem , GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (Tabela, Grade, Seleção)</li><li>Grupo "Contoso" (TableItem, GridItem, SelectionItem,\*Table*, Grid )<br /><br /> <ul><li>DataItem "Contas a receber.doc" (SelectionItem, Invoke,\*TableItem\*, GridItem )</li><li>DataItem "Contas a pagar.doc" (SelectionItem,\*Invoke, TableItem , GridItem\*)</li></ul></li></ul>|  
  
 \*O exemplo anterior mostra um DataGrid que contém vários níveis de controles. O controle do Grupo ("Contoso") contém dois controles DataItem ("Contas a receber.doc" e "Contas a Pagar.doc"). Um par DataGrid/GridItem é independente de um par em outro nível. Os controles DataItem sob um Grupo também podem ser expostos como um tipo de controle ListItem, permitindo que eles sejam apresentados mais claramente como objetos selecionáveis, em vez de como elementos de dados simples. Este exemplo não inclui os subelementos dos itens de dados agrupados.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Visão Geral dos Tipos de Controle de Automação de Interface do Usuário](ui-automation-control-types-overview.md)
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
