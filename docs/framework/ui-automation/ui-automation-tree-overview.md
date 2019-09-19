---
title: Visão geral da árvore de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: adb1d10e659254b5fa326e7c598107d768aa2685
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040403"
---
# <a name="ui-automation-tree-overview"></a>Visão geral da árvore de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Produtos de tecnologia assistencial e scripts de teste [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] navegam na árvore para reunir [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] informações sobre o e seus elementos.  
  
 Dentro da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore, há um elemento raiz (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) que representa a área de trabalho atual e cujos elementos filho representam janelas de aplicativo. Cada um desses elementos filho pode conter elementos que representam partes [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] como menus, botões, barras de ferramentas e caixas de listagem. Esses elementos, por sua vez, podem conter elementos como itens de lista.  
  
 A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore não é uma estrutura fixa e raramente é vista em sua totalidade porque pode conter milhares de elementos. Partes dele são criadas conforme necessário e podem sofrer alterações à medida que elementos são adicionados, movidos ou removidos.  
  
 Os provedores de automação de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] interface do usuário dão suporte à árvore implementando a navegação entre os itens dentro de um fragmento, que consiste em uma raiz (geralmente hospedada em uma janela) e uma subárvore. No entanto, os provedores não se preocupam com a navegação de um controle para outro. Isso é gerenciado pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] núcleo, usando as informações dos provedores de janela padrão.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Exibições da árvore de automação  
 A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore pode ser filtrada para criar exibições que contenham somente os <xref:System.Windows.Automation.AutomationElement> objetos relevantes para um cliente específico. Essa abordagem permite que os clientes personalizem a estrutura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] apresentada até suas necessidades específicas.  
  
 O cliente tem duas maneiras de personalizar o modo de exibição: por escopo e filtrando. O escopo está definindo a extensão da exibição, a partir de um elemento base: por exemplo, o aplicativo pode querer localizar apenas os filhos diretos da área de trabalho ou todos os descendentes de uma janela do aplicativo. A filtragem está definindo os tipos de elementos que devem ser incluídos na exibição.  
  
 Os provedores de automação de interface do usuário dão suporte à filtragem definindo <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> propriedades <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> em elementos, incluindo as propriedades e.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece três exibições padrão. Essas exibições são definidas pelo tipo de filtragem executada; o escopo de qualquer exibição é definido pelo aplicativo. Além disso, o aplicativo pode aplicar outros filtros nas propriedades; por exemplo, para incluir somente controles habilitados em um modo de exibição de controle.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Exibição bruta  
 A exibição bruta da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore é a árvore completa de <xref:System.Windows.Automation.AutomationElement> objetos para os quais a área de trabalho é a raiz. A exibição bruta segue melhor a estrutura programática nativa de um aplicativo e, portanto, é a exibição mais detalhada disponível. Também é a base na qual as outras exibições da árvore são criadas. Como essa exibição depende da estrutura subjacente [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , a exibição bruta de um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] botão terá uma exibição bruta diferente de um [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] botão.  
  
 A exibição bruta é obtida pesquisando elementos sem especificar propriedades ou usando o <xref:System.Windows.Automation.TreeWalker.RawViewWalker> para navegar na árvore.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Exibição de controle  
 A exibição de controle da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore simplifica a tarefa do produto de tecnologia assistencial de descrever o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para o usuário final e ajudar o usuário final a interagir com o aplicativo, pois ele é mapeado [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de forma adequada para a estrutura percebido por um usuário final.  
  
 O modo de exibição de controle é um subconjunto da exibição bruta. Ele inclui todos [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] os itens da exibição bruta que um usuário final entenderia como interativo ou contribuindo para a estrutura lógica do controle [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]no. Exemplos de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que contribuem para a estrutura lógica [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]do, mas não são interativos, são contêineres de item, como cabeçalhos de exibição de lista, barras de ferramentas, menus e a barra de status. Itens não interativos usados simplesmente para fins de layout ou decorativo não serão vistos no modo de exibição de controle. Um exemplo é um painel que foi usado apenas para dispor os controles em uma caixa de diálogo, mas não contém nenhuma informação. Itens não interativos que serão vistos no modo de exibição de controle são elementos gráficos com informações e texto estático em uma caixa de diálogo. Os itens não interativos incluídos na exibição de controle não podem receber o foco do teclado.  
  
 O modo de exibição de controle é obtido pesquisando os elementos <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> que têm a `true`propriedade definida como, ou <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> usando o para navegar na árvore.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Exibição de conteúdo  
 O modo de exibição de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] conteúdo da árvore é um subconjunto da exibição de controle. Ele contém [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que transmitem as informações verdadeiras em uma interface do usuário [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , incluindo itens que podem receber o foco do teclado e algum texto que não seja [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] um rótulo em um item. Por exemplo, os valores em uma caixa de combinação suspensa aparecerão no modo de exibição de conteúdo porque representam as informações que estão sendo usadas por um usuário final. Na exibição de conteúdo, uma caixa de combinação e uma caixa de listagem são representadas como [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uma coleção de itens em que um, ou talvez, mais de um, item pode ser selecionado. O fato de que um sempre está aberto e um pode ser expandido e reduzido é irrelevante na exibição de conteúdo porque ele foi projetado para mostrar os dados, ou conteúdo, que estão sendo apresentados ao usuário.  
  
 O modo de exibição de conteúdo é obtido pesquisando os elementos <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> que têm a `true`propriedade definida como, ou <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> usando o para navegar na árvore.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.AutomationElement>
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
