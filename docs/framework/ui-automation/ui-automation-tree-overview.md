---
title: Visão geral da árvore de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: d1edbb82e0d5d6a6275c09646fbf8e54b4ff90df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800285"
---
# <a name="ui-automation-tree-overview"></a>Visão geral da árvore de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Produtos de tecnologia assistencial e scripts de teste navegam na árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para coletar informações sobre o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] e seus elementos.  
  
 Dentro da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] há um elemento raiz (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) que representa a área de trabalho atual e cujos elementos filho representam janelas de aplicativo. Cada um desses elementos filho pode conter elementos que representam partes de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] como menus, botões, barras de ferramentas e caixas de listagem. Esses elementos, por sua vez, podem conter elementos como itens de lista.  
  
 A árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] não é uma estrutura fixa e raramente é vista em sua totalidade porque ela pode conter milhares de elementos. Partes dele são criadas conforme necessário e podem sofrer alterações à medida que elementos são adicionados, movidos ou removidos.  
  
 Os provedores de automação de interface do usuário dão suporte à árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] implementando a navegação entre os itens dentro de um fragmento, que consiste em uma raiz (geralmente hospedada em uma janela) e uma subárvore. No entanto, os provedores não se preocupam com a navegação de um controle para outro. Isso é gerenciado pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Core, usando as informações dos provedores de janela padrão.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Exibições da árvore de automação  
 A árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pode ser filtrada para criar exibições que contêm somente os objetos <xref:System.Windows.Automation.AutomationElement> relevantes para um cliente específico. Essa abordagem permite que os clientes personalizem a estrutura apresentada por meio de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] às suas necessidades específicas.  
  
 O cliente tem duas maneiras de personalizar o modo de exibição: por escopo e filtrando. O escopo está definindo a extensão da exibição, a partir de um elemento base: por exemplo, o aplicativo pode querer localizar apenas os filhos diretos da área de trabalho ou todos os descendentes de uma janela do aplicativo. A filtragem está definindo os tipos de elementos que devem ser incluídos na exibição.  
  
 Os provedores de automação de interface do usuário dão suporte à filtragem definindo propriedades em elementos, incluindo as propriedades <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> e <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fornece três exibições padrão. Essas exibições são definidas pelo tipo de filtragem executada; o escopo de qualquer exibição é definido pelo aplicativo. Além disso, o aplicativo pode aplicar outros filtros nas propriedades; por exemplo, para incluir somente controles habilitados em um modo de exibição de controle.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Exibição bruta  
 A exibição bruta da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é a árvore completa de objetos <xref:System.Windows.Automation.AutomationElement> para os quais a área de trabalho é a raiz. A exibição bruta segue melhor a estrutura programática nativa de um aplicativo e, portanto, é a exibição mais detalhada disponível. Também é a base na qual as outras exibições da árvore são criadas. Como essa exibição depende da estrutura de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] subjacente, a exibição bruta de um botão de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] terá uma exibição bruta diferente de um botão de [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)].  
  
 A exibição bruta é obtida pesquisando elementos sem especificar propriedades ou usando o <xref:System.Windows.Automation.TreeWalker.RawViewWalker> para navegar pela árvore.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Exibição de controle  
 A exibição de controle da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] simplifica a tarefa do produto de tecnologia assistencial de descrever o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para o usuário final e ajudar o usuário final a interagir com o aplicativo, pois ele é mapeado de forma adequada para a estrutura de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] percebida por um usuário final.  
  
 O modo de exibição de controle é um subconjunto da exibição bruta. Ele inclui todos os itens de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] da exibição bruta que um usuário final entenderia como interativo ou contribuindo para a estrutura lógica do controle na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Exemplos de itens de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] que contribuem para a estrutura lógica do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], mas não são interativos, são contêineres de item, como cabeçalhos de exibição de lista, barras de ferramentas, menus e a barra de status. Itens não interativos usados simplesmente para fins de layout ou decorativo não serão vistos no modo de exibição de controle. Um exemplo é um painel que foi usado apenas para dispor os controles em uma caixa de diálogo, mas não contém nenhuma informação. Itens não interativos que serão vistos no modo de exibição de controle são elementos gráficos com informações e texto estático em uma caixa de diálogo. Os itens não interativos incluídos na exibição de controle não podem receber o foco do teclado.  
  
 O modo de exibição de controle é obtido pesquisando os elementos que têm a propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> definida como `true`ou usando o <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> para navegar na árvore.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Exibição de conteúdo  
 A exibição de conteúdo da árvore de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] é um subconjunto da exibição de controle. Ele contém [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que transmitem as informações verdadeiras em uma interface do usuário, incluindo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que podem receber o foco do teclado e algum texto que não seja um rótulo em um item de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Por exemplo, os valores em uma caixa de combinação suspensa aparecerão no modo de exibição de conteúdo porque representam as informações que estão sendo usadas por um usuário final. Na exibição de conteúdo, uma caixa de combinação e uma caixa de listagem são representadas como uma coleção de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens em que um ou talvez mais de um item pode ser selecionado. O fato de que um sempre está aberto e um pode ser expandido e reduzido é irrelevante na exibição de conteúdo porque ele foi projetado para mostrar os dados, ou conteúdo, que estão sendo apresentados ao usuário.  
  
 O modo de exibição de conteúdo é obtido pesquisando os elementos que têm a propriedade <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> definida como `true`ou usando o <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> para navegar na árvore.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Automation.AutomationElement>
- [Visão geral de Automação da Interface do Usuário](ui-automation-overview.md)
