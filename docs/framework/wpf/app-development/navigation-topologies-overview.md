---
title: Visão geral de topologias da navegação
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 5679bac06b87b3c4e50cbc4a238d7daf3e33a564
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636270"
---
# <a name="navigation-topologies-overview"></a>Visão geral de topologias da navegação
<a name="introduction"></a>Esta visão geral fornece uma introdução às topologias de navegação no WPF. Em seguida, três topologias de navegação comuns, com amostras, são abordadas.  
  
> [!NOTE]
> Antes de ler este tópico, você deve estar familiarizado com o conceito de navegação estruturada no WPF usando funções de página. Para obter mais informações sobre esses dois tópicos, consulte [visão geral de navegação estruturada](structured-navigation-overview.md).  
  
 Esse tópico contém as seguintes seções:  
  
- [Topologias de navegação](#Navigation_Topologies)  
  
- [Topologias de navegação estruturada](#Structured_Navigation_Topologies)  
  
- [Navegação em uma topologia linear fixa](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [Navegação dinâmica em uma topologia hierárquica fixa](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [Navegação em uma topologia gerada dinamicamente](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>   
## <a name="navigation-topologies"></a>Topologias de navegação  
 No WPF, a navegação normalmente consiste em páginas (<xref:System.Windows.Controls.Page>) com hiperlinks (<xref:System.Windows.Documents.Hyperlink>) que navegam para outras páginas quando clicados. As páginas que são navegadas são identificadas por URIs (identificadores de recursos uniformes) (consulte [URIs de pacote no WPF](pack-uris-in-wpf.md)). Considere o seguinte exemplo simples que mostra páginas, hiperlinks e URIs (identificadores de recursos uniformes):  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 Essas páginas são organizadas em uma *topologia de navegação* cuja estrutura é determinada por como você pode navegar entre as páginas. Essa topologia de navegação em particular é adequada para cenários simples, embora a navegação possa exigir topologias mais complexas, algumas das quais só podem ser definidas quando um aplicativo está em execução.  
  
 Este tópico aborda três topologias de navegação comuns: *linear fixa*, *hierárquica fixa*e *gerada dinamicamente*. Cada topologia de navegação é demonstrada com um exemplo que tem um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] como aquele mostrado na figura a seguir:  
  
 ![Páginas de tarefas com itens de dados e botões de navegação.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>   
## <a name="structured-navigation-topologies"></a>Topologias de navegação estruturada  
 Há dois tipos gerais de topologias de navegação:  
  
- **Topologia fixa**: é definida em tempo de compilação e não é alterada em tempo de execução. Topologias fixas são úteis para navegação em uma sequência fixa de páginas em ordem hierárquica ou ordem linear.  
  
- **Topologia dinâmica**: definida em tempo de execução com base em entradas coletadas do usuário, do aplicativo ou do sistema. Topologias dinâmicas são úteis quando as páginas podem ser navegadas em sequências diferentes.  
  
 Embora seja possível criar topologias de navegação utilizando páginas, as amostras usam funções de página porque dão suporte adicional que simplifica o suporte para passar e retornar dados pelas páginas de uma topologia.  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>   
## <a name="navigation-over-a-fixed-linear-topology"></a>Navegação em uma topologia linear fixa  
 Uma topologia linear fixa é semelhante à estrutura de um assistente que tem uma ou mais páginas de assistente que são navegadas em sequência fixa. A figura a seguir mostra a estrutura de alto nível e o fluxo de um assistente com uma topologia linear fixa:  
  
 ![Diagrama que mostra uma topologia linear fixa.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 Os comportamentos típicos para navegar em uma topologia linear fixa incluem o seguinte:  
  
- Navegar da página de chamada para uma página de inicializador que inicia o assistente e navega até a primeira página do assistente. Uma página do iniciador (um <xref:System.Windows.Navigation.PageFunction%601>sem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]) não é necessária, pois uma página de chamada pode chamar a primeira página do assistente diretamente. Entretanto, usar uma página de inicializador pode simplificar a inicialização do assistente, especialmente se ela for complexa.  
  
- Os usuários podem navegar entre páginas usando os botões Voltar e Avançar (ou hiperlinks).  
  
- Os usuários podem navegar entre páginas usando o diário.  
  
- Os usuários podem cancelar o assistente em qualquer página do assistente pressionando um botão Cancelar.  
  
- Os usuários podem aceitar o assistente na última página do assistente pressionando um botão Concluir.  
  
- Se um assistente for cancelado, o assistente retornará um resultado apropriado e não retornará dados.  
  
- Se um usuário aceitar um assistente, o assistente retornará um resultado apropriado, bem como os dados coletados.  
  
- Quando o assistente for concluído (aceito ou cancelado), as páginas que compreendem o assistente serão removidas do diário. Isso mantém cada instância do assistente isolada, evitando assim potenciais anomalias de dados ou de estado.  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>   
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a>Navegação dinâmica em uma topologia hierárquica fixa  
 Em alguns aplicativos, as páginas permitem a navegação para duas ou mais páginas, conforme mostrado na figura a seguir: 
  
 ![Diagrama que mostra uma página que pode navegar para várias páginas.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 Essa estrutura é conhecida como topologia hierárquica fixa e a sequência na qual a hierarquia é atravessada geralmente é determinada em tempo de execução pelo aplicativo ou pelo usuário. Em tempo de execução, cada página na hierarquia que permite a navegação para duas ou mais outras páginas reúne os dados necessários para determinar a página à qual deve navegar. A figura a seguir ilustra uma das várias sequências de navegação possíveis com base na figura anterior:  
  
 ![Diagrama que mostra uma possível sequência de navegação.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 Embora a sequência em que as páginas de uma estrutura hierárquica fixa são navegadas seja determinada em tempo de execução, a experiência do usuário é a mesma que a experiência do usuário para uma topologia linear fixa:  
  
- Navegar da página de chamada para uma página de inicializador que inicia o assistente e navega até a primeira página do assistente. Uma página do iniciador (um <xref:System.Windows.Navigation.PageFunction%601>sem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]) não é necessária, pois uma página de chamada pode chamar a primeira página do assistente diretamente. Entretanto, usar uma página de inicializador pode simplificar a inicialização do assistente, especialmente se ela for complexa.  
  
- Os usuários podem navegar entre páginas usando os botões Voltar e Avançar (ou hiperlinks).  
  
- Os usuários podem navegar entre páginas usando o diário.  
  
- Os usuários podem alterar a sequência de navegação se navegarem de volta pelo diário.  
  
- Os usuários podem cancelar o assistente em qualquer página do assistente pressionando um botão Cancelar.  
  
- Os usuários podem aceitar o assistente na última página do assistente pressionando um botão Concluir.  
  
- Se um assistente for cancelado, o assistente retornará um resultado apropriado e não retornará dados.  
  
- Se um usuário aceitar um assistente, o assistente retornará um resultado apropriado, bem como os dados coletados.  
  
- Quando o assistente for concluído (aceito ou cancelado), as páginas que compreendem o assistente serão removidas do diário. Isso mantém cada instância do assistente isolada, evitando assim potenciais anomalias de dados ou de estado.  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>   
## <a name="navigation-over-a-dynamically-generated-topology"></a>Navegação em uma topologia gerada dinamicamente  
 Em alguns aplicativos, a sequência em que duas ou mais páginas são navegadas só pode ser determinada em tempo de execução, seja pelo usuário, pelo aplicativo ou por dados externos. A figura a seguir ilustra um conjunto de páginas com uma sequência de navegação indeterminada:  
  
 ![Um conjunto de páginas com uma sequência de navegação indeterminada.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 A próxima figura ilustra uma sequência de navegação que foi escolhida pelo usuário em tempo de execução:  
  
 ![Diagrama que mostra uma sequência de navegação escolhida em tempo de execução.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 A sequência de navegação é conhecida como uma topologia gerada dinamicamente. Para o usuário, assim como ocorre com as outras topologias de navegação, a experiência do usuário é a mesmo das topologias anteriores:  
  
- Navegar da página de chamada para uma página de inicializador que inicia o assistente e navega até a primeira página do assistente. Uma página do iniciador (um <xref:System.Windows.Navigation.PageFunction%601>sem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]) não é necessária, pois uma página de chamada pode chamar a primeira página do assistente diretamente. Entretanto, usar uma página de inicializador pode simplificar a inicialização do assistente, especialmente se ela for complexa.  
  
- Os usuários podem navegar entre páginas usando os botões Voltar e Avançar (ou hiperlinks).  
  
- Os usuários podem navegar entre páginas usando o diário.  
  
- Os usuários podem cancelar o assistente em qualquer página do assistente pressionando um botão Cancelar.  
  
- Os usuários podem aceitar o assistente na última página do assistente pressionando um botão Concluir.  
  
- Se um assistente for cancelado, o assistente retornará um resultado apropriado e não retornará dados.  
  
- Se um usuário aceitar um assistente, o assistente retornará um resultado apropriado, bem como os dados coletados.  
  
- Quando o assistente for concluído (aceito ou cancelado), as páginas que compreendem o assistente serão removidas do diário. Isso mantém cada instância do assistente isolada, evitando assim potenciais anomalias de dados ou de estado.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Visão geral da navegação estruturada](structured-navigation-overview.md)
