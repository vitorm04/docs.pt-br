---
title: "Árvores no WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56237bccb2bf61994c6114fa01d15c254267ca20
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="trees-in-wpf"></a>Árvores no WPF
Em muitas tecnologias, elementos e componentes são organizados em uma estrutura de árvore em que os desenvolvedores manipulam diretamente os nós de objeto na árvore para afetar a renderização ou o comportamento de um aplicativo. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] também usa várias metáforas de estrutura de árvore para definir relações entre elementos do programa. Em geral, os desenvolvedores de WPF conseguem criar um aplicativo em código ou definir partes do aplicativo em XAML enquanto pensam conceitualmente sobre a metáfora da árvore de objeto, mas chamarão uma API específica ou usarão marcação específica para fazer isso em vez de alguma API geral de manipulação de árvore de objeto, como a que poderia ser usada em XML DOM. WPF expõe duas classes auxiliares que fornecem uma exibição em árvore metáfora, <xref:System.Windows.LogicalTreeHelper> e <xref:System.Windows.Media.VisualTreeHelper>. Os termos “árvore visual” e “árvore lógica” também são utilizados na documentação do WPF porque essas mesmas árvores são úteis para entender o comportamento de alguns recursos principais do WPF. Este tópico define o que representam a árvore visual e a árvore lógica, discute como tais árvores se relacionam com um conceito de árvore de objeto geral e apresenta <xref:System.Windows.LogicalTreeHelper> e <xref:System.Windows.Media.VisualTreeHelper>s.  
  

  
<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>Árvores no WPF  
 A estrutura de árvore mais completa no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é a árvore de objetos. Se você definir uma página de aplicativo no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e, em seguida, carregar o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a estrutura de árvore será criada com base nas relações de aninhamento dos elementos na marcação. Se você definir um aplicativo ou uma parte do aplicativo em código, a estrutura de árvore será criada com base em como os valores de propriedade são designados para propriedades que implementam o modelo de conteúdo de um determinado objeto. No [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], a árvore de objetos completa é conceitualizada e pode ser reportada à API pública de duas maneiras: como árvore lógica e como árvore visual. As distinções entre a árvore lógica e a árvore visual não são sempre necessariamente importantes, mas, ocasionalmente, podem causar problemas com alguns subsistemas do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e afetar opções feitas na marcação ou código.  
  
 Apesar de a árvore lógica ou a árvore visual não serem sempre manipuladas diretamente, entender os conceitos de como elas interagem é útil para entender o WPF como uma tecnologia. Ver o WPF como uma metáfora de árvore de algum tipo também é crucial para entender como a herança de propriedades e roteamento de evento funcionam no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
> [!NOTE]
>  Como a árvore de objetos é mais um conceito de uma API real, outra maneira de pensar o conceito é como um grafo de objeto. Na prática, existem relações entre objetos em tempo de execução em que a metáfora de árvore travará. No entanto, especialmente com a interface do usuário definida em XAML, a metáfora da árvore é relevante o suficiente para a maior parte da documentação do WPF usar o termo “árvore de objetos” ao fazer referência a esse conceito geral.  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>A árvore lógica  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], conteúdo é adicionado aos elementos da interface do usuário mediante a configuração dos objetos que apoiam esses elementos. Por exemplo, você pode adicionar itens a um <xref:System.Windows.Controls.ListBox> controle manipulando seu <xref:System.Windows.Controls.ItemsControl.Items%2A> propriedade. Ao fazer isso, você está colocando itens para o <xref:System.Windows.Controls.ItemCollection> que é o <xref:System.Windows.Controls.ItemsControl.Items%2A> o valor da propriedade. Da mesma forma, para adicionar objetos em um <xref:System.Windows.Controls.DockPanel>, você manipular seu <xref:System.Windows.Controls.Panel.Children%2A> o valor da propriedade. Aqui, você está adicionando objetos para o <xref:System.Windows.Controls.UIElementCollection>. Para ver um exemplo de código, consulte [Adicionar um elemento dinamicamente](http://msdn.microsoft.com/en-us/d00f258a-7973-4de7-bc54-a3fc1f638419).  
  
 Em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], quando você coloca itens de lista em um <xref:System.Windows.Controls.ListBox> ou controles ou outros elementos de interface do usuário em um <xref:System.Windows.Controls.DockPanel>, você também usar o <xref:System.Windows.Controls.ItemsControl.Items%2A> e <xref:System.Windows.Controls.Panel.Children%2A> propriedades, explícita ou implicitamente, como no exemplo a seguir.  
  
 [!code-xaml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 Se você fosse processar esse XAML como XML em um Modelo de Objeto do Documento e se tivesse incluído as marcas de comentário como implícitas (o que seria legal), a árvore DOM XML resultante incluiria elementos para o `<ListBox.Items>` e os outros itens implícitos. Contudo, o XAML não processa dessa forma quando você lê a marcação e grava em objetos; o grafo do objeto resultante não inclui, literalmente, o `ListBox.Items`. No entanto, ele tem um <xref:System.Windows.Controls.ListBox> propriedade denominada `Items` que contém um <xref:System.Windows.Controls.ItemCollection>e que <xref:System.Windows.Controls.ItemCollection> é inicializada mas vazio quando o <xref:System.Windows.Controls.ListBox> XAML é processado. Em seguida, cada elemento de objeto filho existente como o conteúdo para o <xref:System.Windows.Controls.ListBox> é adicionado ao <xref:System.Windows.Controls.ItemCollection> por chamadas de analisador para `ItemCollection.Add`. Esse exemplo de processamento de XAML em uma árvore de objetos é, até o momento, aparentemente um exemplo em que a árvore de objetos criada é, basicamente, a árvore lógica.  
  
 Todavia, a árvore lógica não é o grafo de objeto inteiro que existe para a interface do usuário do aplicativo no tempo de execução, mesmo com os itens de sintaxe implícitos do XAML fatorados. O principal motivo para isso são visuais e modelos. Por exemplo, considere o <xref:System.Windows.Controls.Button>. Os relatórios de árvore lógica a <xref:System.Windows.Controls.Button> objeto e também sua cadeia de caracteres `Content`. Porém, esse botão contém mais recursos na árvore de objetos de tempo de execução. Em particular, o botão só é exibido na tela da forma que faz porque um determinado <xref:System.Windows.Controls.Button> aplicação do modelo de controle. Os visuais que vêm de um modelo aplicado (como o modelo definido <xref:System.Windows.Controls.Border> de cinza escura ao redor do botão visual) não são relatados na árvore lógica, mesmo se você estiver procurando na árvore lógica durante o tempo de execução (como manipular um evento de entrada das interface do usuário visível e, em seguida, ler a árvore lógica). Para encontrar os visuais do modelo, seria necessário examinar a árvore visual.  
  
 Para obter mais informações a respeito de como a sintaxe do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é mapeada para o grafo de objeto criado, bem como sobre a sintaxe implícita em XAML, consulte [Sintaxe XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md) ou [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>A finalidade da árvore lógica  
 A árvore lógica existe para que os modelos de conteúdo possam ser iterados imediatamente sobre os possíveis objetos filho e para que os modelos de conteúdo possam ser extensíveis. Além disso, a árvore lógica fornece uma estrutura para determinadas notificações, como nos casos em que todos os objetos na árvore lógica são carregados. Basicamente, a árvore lógica é uma aproximação de um grafo de objeto de tempo de execução no nível da estrutura, que exclui visuais, mas é adequada para várias operações de consulta em relação à composição do seu próprio aplicativo de tempo de execução.  
  
 Além disso, ambas as referências a recursos estáticos e dinâmicos são resolvidas olhando para cima através de árvore lógica para <xref:System.Windows.FrameworkElement.Resources%2A> coleções no objeto de solicitação inicial e, em seguida, continuando a árvore lógica e verificação de cada <xref:System.Windows.FrameworkElement> (ou <xref:System.Windows.FrameworkContentElement>) Por outro `Resources` valor que contém um <xref:System.Windows.ResourceDictionary>, possivelmente que contém essa chave. A árvore lógica é usada para pesquisa de recursos quando a árvore lógica e a árvore visual estão presentes. Para obter mais informações sobre dicionários de recursos e pesquisa, consulte [Recursos de XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>Composição da árvore lógica  
 A árvore lógica é definida o nível WPF framework-, que significa que o elemento base WPF que é mais relevante para operações de árvore lógica está <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. No entanto, como você pode ver se você realmente usa o <xref:System.Windows.LogicalTreeHelper> API, a árvore lógica, às vezes, contém nós que não seja <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Por exemplo, a árvore lógica relata o <xref:System.Windows.Controls.TextBlock.Text%2A> valor de um <xref:System.Windows.Controls.TextBlock>, que é uma cadeia de caracteres.  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>Substituindo a árvore lógica  
 Autores de controle avançados podem substituir a árvore lógica mediante a substituição de vários [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], que definem como um objeto geral ou modelo de conteúdo adiciona ou remove objetos dentro da árvore lógica. Para ver um exemplo de como substituir a árvore lógica, consulte [Substituir a árvore lógica](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md).  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>Herança do valor de propriedade  
 A herança do valor da propriedade opera por meio de uma árvore híbrida. Os metadados que contém o <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> propriedade que permite a herança de propriedade é o nível de framework WPF <xref:System.Windows.FrameworkPropertyMetadata> classe. Portanto, o pai que contém o valor original e o objeto filho que herda esse valor devem ser <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, e ambos devem fazer parte de alguma árvore lógica. No entanto, para propriedades existentes do WPF que dão suporte à herança de propriedade, a herança de valor da propriedade pode ser perpetuada por meio de um objeto intermediário que não está na árvore lógica. Principalmente, isso é relevante para fazer com que elementos de modelo usem valores da propriedade herdados definidos na instância que é modelada ou em níveis ainda mais altos de composição de nível de página e, portanto, mais altos na árvore lógica. Para a herança de valor da propriedade funcionar consistentemente em tal limite, a propriedade que herda deve ser registrada como uma propriedade anexada. Você deve seguir esse padrão caso pretenda definir uma propriedade de dependência personalizada com comportamento de herança de propriedade. A árvore exata usada para a herança de propriedade não pode ser totalmente prevista por um método de utilitário de classe auxiliar, mesmo em tempo de execução. Para obter mais informações, consulte [Herança do valor da propriedade](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>A árvore visual  
 Além do conceito de árvore lógica, há também o conceito de árvore visual no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A árvore visual descreve a estrutura de objetos visuais, conforme representado pela <xref:System.Windows.Media.Visual> classe base. Quando você grava um modelo para um controle, define ou redefine a árvore visual que se aplica a ele. A árvore visual também interessa aos desenvolvedores que desejam controle de baixo nível sobre o desenho por motivos de desempenho e otimização. Uma exposição da árvore visual como parte da programação convencional do aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é que as rotas de eventos para um evento roteado viajam principalmente junto à árvore visual, não à árvore lógica. Essa sutileza do comportamento do evento roteado pode não ser imediatamente aparente, a menos que você seja um autor de controle. O roteamento de eventos através da árvore visual habilita controles que implementam composição no nível visual para manipular eventos ou criar setters de eventos.  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>Árvores, elementos de conteúdo e hosts de conteúdo  
 Elementos de conteúdo (classes que derivam de <xref:System.Windows.ContentElement>) não fazem parte da árvore visual; eles não herdam de <xref:System.Windows.Media.Visual> e não têm uma representação visual. Para aparecer em uma interface do usuário, uma <xref:System.Windows.ContentElement> deve ser hospedado em um host de conteúdo que é um <xref:System.Windows.Media.Visual> e um participante da árvore lógica. Normalmente esse tipo de objeto é um <xref:System.Windows.FrameworkElement>. É possível conceitualizar que o host de conteúdo se assemelha a um “navegador” para o conteúdo e escolhe como exibir esse conteúdo dentro da região da tela controlada pelo host. Quando o conteúdo é hospedado, pode se tornar um participante em determinados processos de árvore que, normalmente, estão associados à árvore visual. Em geral, o <xref:System.Windows.FrameworkElement> classe de host inclui o código de implementação que adiciona qualquer hospedado <xref:System.Windows.ContentElement> à rota de eventos através de subnós da árvore lógica de conteúdo, embora o conteúdo hospedado não é parte da árvore visual verdadeira. Isso é necessário para que um <xref:System.Windows.ContentElement> pode extrair um evento roteado que roteia qualquer elemento diferente dele mesmo.  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>Passagem da árvore  
 O <xref:System.Windows.LogicalTreeHelper> classe fornece a <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>, <xref:System.Windows.LogicalTreeHelper.GetParent%2A>, e <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> métodos para passagem da árvore lógica. Na maioria dos casos, não deve ser necessário atravessar a árvore lógica de controles existentes, porque esses controles quase sempre expõem seus elementos filho lógicos como uma propriedade de coleção dedicada que dá suporte ao acesso de coleção, como `Add`, um indexador etc. Passagem da árvore é principalmente um cenário que é usado por autores de controle que não queiram derivar de padrões de controle desejados, como <xref:System.Windows.Controls.ItemsControl> ou <xref:System.Windows.Controls.Panel> onde as propriedades da coleção já estão definidas, e que pretendem fornecer sua própria coleção suporte de propriedade.  
  
 A árvore visual também oferece suporte a uma classe auxiliar para passagem da árvore visual, <xref:System.Windows.Media.VisualTreeHelper>. A árvore visual não é exposta como convenientemente através das propriedades de controle específico, portanto, a <xref:System.Windows.Media.VisualTreeHelper> classe é a maneira recomendada para percorrer a árvore visual se for necessário para sua situação de programação. Para obter mais informações, consulte [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
> [!NOTE]
>  Às vezes, é necessário examinar a árvore visual de um modelo aplicado. Você deve ter cuidado ao usar essa técnica. Mesmo que você está atravessando uma árvore visual para um controle onde você define o modelo, os consumidores de seu controle sempre podem alterar o modelo definindo o <xref:System.Windows.Controls.Control.Template%2A> propriedade nas instâncias e até mesmo o usuário final pode influenciar o modelo aplicado, alterando o tema do sistema.  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>Rotas para eventos roteados como “árvore”  
 Como mencionado antes, a rota de qualquer evento roteado percorre um caminho único e predeterminado de uma árvore que é um híbrido das representações de árvore visual e lógica. A rota do evento pode percorrer as direções para cima ou para baixo dentro da árvore, dependendo de ser um evento roteado por túnel ou propagação. O conceito de rota de evento não tem uma classe auxiliar diretamente de suporte que possa ser usada para “conduzir” a rota do evento independentemente de gerar um evento que seja realmente roteado. Há uma classe que representa a rota, <xref:System.Windows.EventRoute>, mas os métodos dessa classe geralmente são somente para uso interno.  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>Dicionários de recursos e árvores  
 A pesquisa de dicionário de recursos para todos os `Resources` definidos em uma página basicamente atravessa a árvore lógica. Os objetos que não estão na árvore lógica podem fazer referência a recursos com chave, mas a sequência de pesquisa de recursos começa no ponto em que o objeto está conectado à árvore lógica. No WPF, somente nós de árvore lógica podem ter um `Resources` propriedade que contém um <xref:System.Windows.ResourceDictionary>, portanto não há nenhuma vantagem em atravessar a árvore visual procurando recursos com chave de um <xref:System.Windows.ResourceDictionary>.  
  
 No entanto, a pesquisa de recursos também pode se estender além da árvore lógica imediata. Para marcação de aplicativo, a pesquisa de recurso pode seguir adiante até dicionários de recursos no nível do aplicativo e, a seguir, até valores de suporte e sistema de tema que são referenciados como propriedades estáticas ou chaves. Os próprios temas também poderão fazer referência a valores do sistema fora da árvore lógica de tema se as referências de recurso forem dinâmicas. Para obter mais informações sobre dicionários de recursos e lógica de pesquisa, consulte [Recursos de XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Visão geral de renderização de gráficos do WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [Visão geral de eventos roteados](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Inicialização de elementos de objeto que não estão em uma árvore de objetos](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [Arquitetura do WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
