---
title: Suporte de automação de interface de usuário para o tipo de controle DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 0c9873638bca43e5e0d005d36053e7c75d48168b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679067"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Suporte de automação de interface de usuário para o tipo de controle DataGrid
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Este tópico fornece informações sobre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] suporte para o tipo de controle DataGrid. Na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], um tipo de controle é um conjunto de condições que um controle deve atender para usar o `ControlType` propriedade. As condições incluem diretrizes específicas para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] estrutura de árvore [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] valores de propriedade e padrões de controle.  
  
 O tipo de controle DataGrid permite ao usuário trabalhar facilmente com os itens que contêm metadados representados em colunas. Controles de grade de dados tem linhas de itens e colunas de informações sobre esses itens. Um controle de exibição de lista no Microsoft Vista Explorer é um exemplo que suporta o tipo de controle DataGrid.  
  
 As seções a seguir definem as [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos para o tipo de controle DataGrid, propriedades, padrões de controle e estrutura de árvore. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos se aplicam a todos os dados de controles de grade, se [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Estrutura de árvore de automação de interface do usuário necessária  
 A tabela a seguir mostra a visualização de controle e exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore referente à grade de dados controla e descreve o que pode ser contido em cada modo de exibição. Para obter mais informações sobre o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore, consulte [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - modo de exibição de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Cabeçalho (0, 1 ou 2)<br /><br /> <ul><li>HeaderItem (número de colunas ou linhas)</li></ul></li><li>DataItem (0 ou mais; pode ser estruturado de hierarquia)</li></ul>|DataGrid<br /><br /> -DataItem (0 ou mais; pode ser estruturado de hierarquia)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Propriedades de automação de interface do usuário necessária  
 A tabela a seguir lista as propriedades cujo valor ou definição são especialmente relevantes para os controles de grade de dados. Para obter mais informações sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades, consulte [propriedades de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriedade|Valor|Observações|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consulte as observações.|O valor dessa propriedade precisa ser exclusivo entre todos os controles em um aplicativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consulte as observações.|O retângulo mais externo que contém o controle inteiro.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consulte as observações.|Suporte se houver um retângulo delimitador. Se não for todo ponto dentro do retângulo delimitador é clicável, e você executar o teste de hit especializado, substituir e fornece um ponto clicável.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Esse valor é o mesmo para todas as estruturas de interface do usuário.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|verdadeiro|O valor dessa propriedade deve sempre ser verdadeiro. Isso significa que o controle de grade de dados sempre deve ser na exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|verdadeiro|O valor dessa propriedade deve sempre ser verdadeiro. Isso significa que o controle de grade de dados sempre deve ser no modo de exibição de controle do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consulte as observações.|Se o controle pode receber o foco do teclado, ele deve oferecer suporte a essa propriedade.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consulte as observações.|Se houver um rótulo de texto estático, em seguida, essa propriedade deve expor uma referência a esse controle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"grade de dados"|Cadeia de caracteres localizada correspondente ao tipo de controle DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consulte as observações.|O controle de grade de dados normalmente obtém o valor para o seu `Name` propriedade de um rótulo de texto estático. Se não houver um rótulo de texto estático um desenvolvedor de aplicativos deve atribuir um valor para o `Name` propriedade. O valor da `Name` propriedade nunca deve ser o conteúdo textual do controle de edição.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Padrões de controle de automação de interface do usuário necessária  
 A tabela a seguir lista os padrões de controle devem ser suportados por todos os controles de grade de dados. Para obter mais informações sobre padrões de controle, consulte [visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Padrão de controle|Suporte|Observações|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Sim|O controle de grade de dados em si sempre oferece suporte o padrão de controle de grade porque os itens que ele contém metadados que está disposto em uma grade.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Depende|A capacidade de rolar a grade de dados depende do conteúdo e se as barras de rolagem estão presentes.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Depende|A capacidade de selecionar a grade de dados depende do conteúdo.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Sim|O controle de grade de dados sempre tem um cabeçalho em sua subárvore, portanto, deve haver suporte para o padrão de controle de tabela.|  
  
 Itens de dados dentro dos contêineres de grade de dados serão compatível com no mínimo:  
  
-   Padrão de controle de Item de seleção (se a grade de dados é selecionável)  
  
-   Role o padrão de controle de Item (se a grade de dados for rolável)  
  
-   Padrão de controle de Item de grade  
  
-   padrão de controle Item de Tabela  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventos de automação de interface do usuário necessária  
 A seguinte tabela lista o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos devem ser suportados por todos os controles de grade de dados. Para obter mais informações sobre eventos, consulte [visão geral de eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Evento|Suporte|Observações|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> evento de propriedade alterada.|Necessária|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Depende|Nenhum|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Necessária|Nenhum|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> evento de propriedade alterada.|Depende|Nenhum|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> evento de propriedade alterada.|Depende|Se o controle é compatível com o padrão de rolagem, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> evento de propriedade alterada.|Depende|Se o controle é compatível com o padrão de rolagem, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> evento de propriedade alterada.|Depende|Se o controle é compatível com o padrão de rolagem, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> evento de propriedade alterada.|Depende|Se o controle é compatível com o padrão de rolagem, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> evento de propriedade alterada.|Depende|Se o controle é compatível com o padrão de rolagem, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> evento de propriedade alterada.|Depende|Se o controle é compatível com o padrão de rolagem, ele deve suportar este evento.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Necessária|Nenhum|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Exemplo de tipo de controle de grade de data  
 A imagem a seguir ilustra um controle de exibição de lista que implementa o tipo de controle DataGrid.  
  
 ![Gráfico de um controle de exibição de lista com dois itens de dados](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 O modo de exibição de controle e exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que diz respeito ao controle de exibição de lista de árvore é exibida abaixo. Os padrões de controle para cada elemento de automação são mostrados entre parênteses.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - modo de exibição de controle|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Árvore - exibição de conteúdo|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tabela, grade, seleção)</li><li>Cabeçalho<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "Data de modificação" (Invoke)</li><li>HeaderItem "Tamanho" (Invoke)</li></ul></li><li>Grupo "Contoso" (item de tabela, GridItem, SelectionItem, tabela *, grade\*)<br /><br /> <ul><li>DataItem "contas Receivable.doc" (SelectionItem, invocar TableItem\*, GridItem\*)</li><li>DataItem "contas Payable.doc" (SelectionItem, invocar TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (tabela, grade, seleção)</li><li>Grupo "Contoso" (item de tabela, GridItem, SelectionItem, tabela *, grade\*)<br /><br /> <ul><li>DataItem "contas Receivable.doc" (SelectionItem, invocar TableItem\*, GridItem\*)</li><li>DataItem "contas Payable.doc" (SelectionItem, invocar TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 * O exemplo anterior mostra um DataGrid que contém vários níveis de controles. O controle de grupo ("Contoso") contém dois controles de DataItem ("Receivable.doc contas" e "Contas Payable.doc"). Um par de DataGrid/GridItem é independente de um par em outro nível. Os controles de DataItem em um grupo também podem ser expostos como um tipo de controle, permitindo que eles sejam apresentados mais selecionáveis claramente como objetos, em vez de elementos de dados simples. Este exemplo não inclui os subelementos dos itens de dados agrupados.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
