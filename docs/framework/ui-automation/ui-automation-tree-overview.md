---
title: Visão geral da árvore de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0823a569b19d46f32c1cb780470a935f20429c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-tree-overview"></a>Visão geral da árvore de automação de interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Produtos de tecnologia assistencial e scripts de teste navegam a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore para reunir informações sobre o [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] e seus elementos.  
  
 Dentro de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore existe é um elemento raiz (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) que representa a área de trabalho atual e cujos elementos filhos representam as janelas de aplicativo. Cada um desses elementos filho pode conter elementos que representam pedaços de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] como menus, botões, barras de ferramentas e caixas de listagem. Por sua vez, esses elementos podem conter elementos como itens de lista.  
  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore não é uma estrutura fixa e raramente é vista em sua totalidade porque ela pode conter milhares de elementos. Partes dele são criados conforme forem necessários, e ela poderá sofrer alterações conforme os elementos são adicionados, movidos ou removidos.  
  
 Suportam a provedores de automação de interface do usuário a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore implementando navegação entre itens em um fragmento, que consiste em uma raiz (geralmente hospedada em uma janela) e uma subárvore. No entanto, os provedores não estiver preocupados com navegação de um controle para outro. Isso é gerenciado pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core, com informações de provedores de janela padrão.  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>Modos de exibição de árvore de automação  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore pode ser filtrada para criar modos de exibição que contêm apenas os <xref:System.Windows.Automation.AutomationElement> objetos relevantes para um cliente específico. Essa abordagem permite que clientes personalizem a estrutura apresentada pela [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para suas necessidades específicas.  
  
 O cliente tem duas maneiras de personalizar o modo de exibição: por escopo e por filtragem. Escopo é definir a extensão do modo de exibição, a partir de um elemento base: por exemplo, o aplicativo talvez queira localizar somente filhos diretos da área de trabalho ou todos os descendentes de uma janela de aplicativo. A filtragem é definir os tipos de elementos que devem ser incluídos na exibição.  
  
 Provedores de automação de interface do usuário de suporte à filtragem definindo propriedades em elementos, incluindo o <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> e <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty> propriedades.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fornece três modos de exibição padrão. Essas exibições são definidas pelo tipo de filtragem executada; o escopo de qualquer modo de exibição é definido pelo aplicativo. Além disso, o aplicativo pode aplicar outros filtros nas propriedades; Por exemplo incluir somente habilitado controles em uma exibição de controle.  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>Modo de exibição bruto  
 O modo de exibição bruto do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore é a árvore completa de <xref:System.Windows.Automation.AutomationElement> objetos para que a área de trabalho é a raiz. O modo de exibição bruto segue rigorosamente a estrutura nativa de programação de um aplicativo e, portanto, o modo de exibição mais detalhado disponível. Também é a base na qual os outros modos de exibição de árvore são criados. Porque essa exibição depende subjacente [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework, o modo de exibição bruto de um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] botão terá outro modo de exibição bruto de um [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] botão.  
  
 O modo de exibição bruto é obtido por meio de pesquisa elementos sem especificar propriedades ou usando o <xref:System.Windows.Automation.TreeWalker.RawViewWalker> para navegar na árvore.  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>Exibição de controle  
 A exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore simplifica a tarefa do produto de tecnologia assistencial de descrever a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para o usuário final e ajudando a usuário final interage com o aplicativo porque ele é mapeado estritamente para a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estrutura visto por um usuário final.  
  
 O modo de exibição de controle é um subconjunto do modo de exibição bruto. Ele inclui todos os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens do modo de exibição bruta que um usuário final possa entender como interativo ou que contribui para a estrutura lógica do controle no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Exemplos de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que contribuem para a estrutura lógica do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], mas não são interativos, são contêineres de itens como cabeçalhos de exibição de lista, barras de ferramentas, menus e a barra de status. Itens não interativos usados simplesmente para fins decorativas ou de layout não serão vistos na exibição de controle. Um exemplo é um painel que foi usado somente para dispor controles em uma caixa de diálogo, mas ele próprio não contém todas as informações. Itens não interativos que serão vistos na exibição de controle são gráficos com informações e texto estático em uma caixa de diálogo. Itens não interativos que estão incluídos na exibição de controle não podem receber o foco do teclado.  
  
 O modo de exibição de controle é obtido por meio de pesquisa para elementos que têm o <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> propriedade definida como `true`, ou usando o <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> para navegar na árvore.  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>Exibição de conteúdo  
 Exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore é um subconjunto da exibição de controle. Ele contém [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que transmitem as verdadeiras informações em uma interface de usuário, incluindo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que podem receber foco do teclado e algum texto que não é um rótulo em uma [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] item. Por exemplo, os valores em uma caixa de combinação suspensa aparecerá na exibição de conteúdo porque eles representam as informações que está sendo usadas por um usuário final. Na exibição de conteúdo, uma caixa de combinação e caixa de listagem são representadas como uma coleção de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens onde um, ou talvez mais de um item pode ser selecionado. O fato de que um está sempre aberto e um pode expandir e recolher é irrelevante na exibição de conteúdo porque ele foi projetado para mostrar os dados ou conteúdo, que está sendo apresentado ao usuário.  
  
 Exibição de conteúdo é obtida por meio de pesquisa para elementos que têm o <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> propriedade definida como `true`, ou usando o <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> para navegar na árvore.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.AutomationElement>  
 [Visão geral de Automação da Interface do Usuário](../../../docs/framework/ui-automation/ui-automation-overview.md)
