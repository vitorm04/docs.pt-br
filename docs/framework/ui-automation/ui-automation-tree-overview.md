---
title: Visão geral da árvore de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
ms.openlocfilehash: a0b888e8ecc80e3739c583931a86da3cdb7242d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179446"
---
# <a name="ui-automation-tree-overview"></a>Visão geral da árvore de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Produtos de tecnologia assistiva e [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] scripts de [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] teste navegam na árvore para coletar informações sobre o e seus elementos.  
  
 Dentro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore há um<xref:System.Windows.Automation.AutomationElement.RootElement%2A>elemento raiz ( ) que representa a área de trabalho atual e cujos elementos filhos representam janelas de aplicativos. Cada um desses elementos infantis pode [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] conter elementos que representam peças como menus, botões, barras de ferramentas e caixas de lista. Esses elementos, por sua vez, podem conter elementos como itens de lista.  
  
 A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore não é uma estrutura fixa e raramente é vista em sua totalidade porque pode conter milhares de elementos. Partes dela são construídas conforme necessário, e podem sofrer alterações à medida que os elementos são adicionados, movidos ou removidos.  
  
 Os provedores de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] automação de ui suportam a árvore implementando a navegação entre itens dentro de um fragmento, que consiste em uma raiz (geralmente hospedada em uma janela) e uma subárvore. No entanto, os provedores não estão preocupados com a navegação de um controle para outro. Isso é gerenciado [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pelo núcleo, usando informações dos provedores de janela padrão.  
  
<a name="uiautomation_tree_view"></a>
## <a name="views-of-the-automation-tree"></a>Vistas da árvore de automação  
 A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore pode ser filtrada para <xref:System.Windows.Automation.AutomationElement> criar visualizações que contenham apenas os objetos relevantes para um determinado cliente. Essa abordagem permite que os [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] clientes personalizem a estrutura apresentada através de suas necessidades particulares.  
  
 O cliente tem duas formas de personalizar a vista: por escopo e filtragem. O escopo está definindo a extensão da exibição, a partir de um elemento base: por exemplo, o aplicativo pode querer encontrar apenas filhos diretos da área de trabalho ou todos os descendentes de uma janela de aplicativo. Filtragem é definir os tipos de elementos que devem ser incluídos na exibição.  
  
 Os provedores de automação de ui suportam a filtragem definindo propriedades em elementos, incluindo as <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty> propriedades. <xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece três visualizações padrão. Essas visualizações são definidas pelo tipo de filtragem realizada; o escopo de qualquer exibição é definido pelo aplicativo. Além disso, o aplicativo pode aplicar outros filtros nas propriedades; por exemplo, para incluir apenas controles habilitados em uma exibição de controle.  
  
<a name="uiautomation_raw_view"></a>
### <a name="raw-view"></a>Vista bruta  
 A visão bruta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore é <xref:System.Windows.Automation.AutomationElement> a árvore completa de objetos para os quais a área de trabalho é a raiz. A visão bruta acompanha de perto a estrutura programática nativa de um aplicativo e, portanto, é a visão mais detalhada disponível. É também a base em que as outras vistas da árvore são construídas. Como essa visão depende da [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] estrutura subjacente, a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] visão bruta de um botão terá uma visão bruta diferente de um botão Win32.  
  
 A visão bruta é obtida pela busca de elementos <xref:System.Windows.Automation.TreeWalker.RawViewWalker> sem especificar propriedades ou usando o para navegar na árvore.  
  
<a name="uiautomation_control_view"></a>
### <a name="control-view"></a>Exibição de controle  
 A visão de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controle da árvore simplifica a tarefa do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] produto de tecnologia assistiva de descrever o usuário final e [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ajudar o usuário final a interagir com o aplicativo porque ele mapeia de perto a estrutura percebida por um usuário final.  
  
 A visão de controle é um subconjunto da visão bruta. Ele inclui [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] todos os itens da visão bruta que um usuário final entenderia como interativo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ou contribuindo para a estrutura lógica do controle no . Exemplos de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que contribuem para a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]estrutura lógica do , mas não são interativos em si, são recipientes de itens como cabeçalhos de exibição de lista, barras de ferramentas, menus e a barra de status. Itens não interativos usados simplesmente para fins de layout ou decorativos não serão vistos na exibição de controle. Um exemplo é um painel que foi usado apenas para definir os controles em um diálogo, mas não contém nenhuma informação. Itens não interativos que serão vistos na exibição de controle são gráficos com informações e texto estático em uma caixa de diálogo. Itens não interativos incluídos na exibição de controle não podem receber foco no teclado.  
  
 A visão de controle é obtida pela <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> busca `true`de elementos <xref:System.Windows.Automation.TreeWalker.ControlViewWalker> que tenham a propriedade definida para , ou usando o para navegar na árvore.  
  
<a name="uiautomation_content_view"></a>
### <a name="content-view"></a>Exibição de conteúdo  
 A visualização [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de conteúdo da árvore é um subconjunto da exibição de controle. Ele [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] contém itens que transmitem as informações verdadeiras em uma interface de usuário, incluindo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] itens que [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] podem receber foco no teclado e algum texto que não seja um rótulo em um item. Por exemplo, os valores em uma caixa de combinação parada será exibido na exibição de conteúdo porque eles representam as informações usadas por um usuário final. Na exibição de conteúdo, uma caixa de combinação e [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uma caixa de lista são representadas como uma coleção de itens onde um, ou talvez mais de um, item pode ser selecionado. O fato de estar sempre aberto e se pode expandir e colapsar é irrelevante na visão de conteúdo porque foi projetado para mostrar os dados, ou conteúdo, que está sendo apresentado ao usuário.  
  
 A visualização de conteúdo é obtida <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> pela busca `true`de elementos <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> que tenham a propriedade definida para , ou usando o para navegar na árvore.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.AutomationElement>
- [Visão geral de automação da interface do usuário](ui-automation-overview.md)
