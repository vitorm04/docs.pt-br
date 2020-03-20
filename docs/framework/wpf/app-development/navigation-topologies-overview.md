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
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174193"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="b50fc-102">Visão geral de topologias da navegação</span><span class="sxs-lookup"><span data-stu-id="b50fc-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="b50fc-103">Esta visão geral fornece uma introdução às topologias de navegação no WPF.</span><span class="sxs-lookup"><span data-stu-id="b50fc-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="b50fc-104">Em seguida, três topologias de navegação comuns, com amostras, são abordadas.</span><span class="sxs-lookup"><span data-stu-id="b50fc-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b50fc-105">Antes de ler este tópico, você deve estar familiarizado com o conceito de navegação estruturada no WPF usando funções de página.</span><span class="sxs-lookup"><span data-stu-id="b50fc-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="b50fc-106">Para obter mais informações sobre ambos os tópicos, consulte [Visão geral da navegação estruturada](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b50fc-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="b50fc-107">Este tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="b50fc-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="b50fc-108">Topologias de navegação</span><span class="sxs-lookup"><span data-stu-id="b50fc-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="b50fc-109">Topologias de navegação estruturada</span><span class="sxs-lookup"><span data-stu-id="b50fc-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="b50fc-110">Navegação em uma topologia linear fixa</span><span class="sxs-lookup"><span data-stu-id="b50fc-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="b50fc-111">Navegação dinâmica em uma topologia hierárquica fixa</span><span class="sxs-lookup"><span data-stu-id="b50fc-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="b50fc-112">Navegação em uma topologia gerada dinamicamente</span><span class="sxs-lookup"><span data-stu-id="b50fc-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a><span data-ttu-id="b50fc-113">Topologias de navegação</span><span class="sxs-lookup"><span data-stu-id="b50fc-113">Navigation Topologies</span></span>  
 <span data-ttu-id="b50fc-114">No WPF, a navegação normalmente<xref:System.Windows.Controls.Page>consiste em<xref:System.Windows.Documents.Hyperlink>páginas ( ) com hiperlinks ( ) que navegam para outras páginas quando clicados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="b50fc-115">As páginas que são navegadas são identificadas por identificadores de recursos uniformes (URIs) (ver [URIs pack in WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="b50fc-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="b50fc-116">Considere o exemplo simples a seguir que mostra páginas, hiperlinks e identificadores de recursos uniformes (URIs):</span><span class="sxs-lookup"><span data-stu-id="b50fc-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="b50fc-117">Essas páginas são dispostas em uma *topologia de navegação* cuja estrutura é determinada por como você pode navegar entre as páginas.</span><span class="sxs-lookup"><span data-stu-id="b50fc-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="b50fc-118">Essa topologia de navegação em particular é adequada para cenários simples, embora a navegação possa exigir topologias mais complexas, algumas das quais só podem ser definidas quando um aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="b50fc-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="b50fc-119">Este tópico abrange três topologias de navegação comuns: *linear fixa,* *hierárquica fixa*e *gerada dinamicamente.*</span><span class="sxs-lookup"><span data-stu-id="b50fc-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="b50fc-120">Cada topologia de navegação é demonstrada com uma amostra que tem uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semelhante à que é mostrada na seguinte figura:</span><span class="sxs-lookup"><span data-stu-id="b50fc-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Páginas de tarefas com itens de dados e botões de navegação.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a><span data-ttu-id="b50fc-122">Topologias de navegação estruturada</span><span class="sxs-lookup"><span data-stu-id="b50fc-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="b50fc-123">Há dois tipos gerais de topologias de navegação:</span><span class="sxs-lookup"><span data-stu-id="b50fc-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="b50fc-124">**Topologia fixa**: é definida em tempo de compilação e não é alterada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b50fc-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="b50fc-125">Topologias fixas são úteis para navegação em uma sequência fixa de páginas em ordem hierárquica ou ordem linear.</span><span class="sxs-lookup"><span data-stu-id="b50fc-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="b50fc-126">**Topologia dinâmica**: definida em tempo de execução com base em entradas coletadas do usuário, do aplicativo ou do sistema.</span><span class="sxs-lookup"><span data-stu-id="b50fc-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="b50fc-127">Topologias dinâmicas são úteis quando as páginas podem ser navegadas em sequências diferentes.</span><span class="sxs-lookup"><span data-stu-id="b50fc-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="b50fc-128">Embora seja possível criar topologias de navegação utilizando páginas, as amostras usam funções de página porque dão suporte adicional que simplifica o suporte para passar e retornar dados pelas páginas de uma topologia.</span><span class="sxs-lookup"><span data-stu-id="b50fc-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="b50fc-129">Navegação em uma topologia linear fixa</span><span class="sxs-lookup"><span data-stu-id="b50fc-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="b50fc-130">Uma topologia linear fixa é semelhante à estrutura de um assistente que tem uma ou mais páginas de assistente que são navegadas em sequência fixa.</span><span class="sxs-lookup"><span data-stu-id="b50fc-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="b50fc-131">A figura a seguir mostra a estrutura de alto nível e o fluxo de um assistente com uma topologia linear fixa:</span><span class="sxs-lookup"><span data-stu-id="b50fc-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagrama que mostra uma topologia linear fixa.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="b50fc-133">Os comportamentos típicos para navegar em uma topologia linear fixa incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b50fc-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="b50fc-134">Navegar da página de chamada para uma página de inicializador que inicia o assistente e navega até a primeira página do assistente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b50fc-135">Uma página de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]launcher <xref:System.Windows.Navigation.PageFunction%601>(a -less ) não é necessária, uma vez que uma página de chamada pode chamar a primeira página do assistente diretamente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b50fc-136">Entretanto, usar uma página de inicializador pode simplificar a inicialização do assistente, especialmente se ela for complexa.</span><span class="sxs-lookup"><span data-stu-id="b50fc-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="b50fc-137">Os usuários podem navegar entre páginas usando os botões Voltar e Avançar (ou hiperlinks).</span><span class="sxs-lookup"><span data-stu-id="b50fc-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="b50fc-138">Os usuários podem navegar entre páginas usando o diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="b50fc-139">Os usuários podem cancelar o assistente em qualquer página do assistente pressionando um botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="b50fc-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="b50fc-140">Os usuários podem aceitar o assistente na última página do assistente pressionando um botão Concluir.</span><span class="sxs-lookup"><span data-stu-id="b50fc-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="b50fc-141">Se um assistente for cancelado, o assistente retornará um resultado apropriado e não retornará dados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="b50fc-142">Se um usuário aceitar um assistente, o assistente retornará um resultado apropriado, bem como os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="b50fc-143">Quando o assistente for concluído (aceito ou cancelado), as páginas que compreendem o assistente serão removidas do diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b50fc-144">Isso mantém cada instância do assistente isolada, evitando assim potenciais anomalias de dados ou de estado.</span><span class="sxs-lookup"><span data-stu-id="b50fc-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="b50fc-145">Navegação dinâmica em uma topologia hierárquica fixa</span><span class="sxs-lookup"><span data-stu-id="b50fc-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="b50fc-146">Em alguns aplicativos, as páginas permitem a navegação para duas ou mais páginas, como mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="b50fc-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span>
  
 ![Diagrama que mostra uma página que pode navegar para várias páginas.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="b50fc-148">Essa estrutura é conhecida como topologia hierárquica fixa e a sequência na qual a hierarquia é atravessada geralmente é determinada em tempo de execução pelo aplicativo ou pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="b50fc-149">Em tempo de execução, cada página na hierarquia que permite a navegação para duas ou mais outras páginas reúne os dados necessários para determinar a página à qual deve navegar.</span><span class="sxs-lookup"><span data-stu-id="b50fc-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="b50fc-150">A figura a seguir ilustra uma das várias seqüências de navegação possíveis com base na figura anterior:</span><span class="sxs-lookup"><span data-stu-id="b50fc-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagrama que mostra uma possível seqüência de navegação.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="b50fc-152">Embora a sequência em que as páginas de uma estrutura hierárquica fixa são navegadas seja determinada em tempo de execução, a experiência do usuário é a mesma que a experiência do usuário para uma topologia linear fixa:</span><span class="sxs-lookup"><span data-stu-id="b50fc-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="b50fc-153">Navegar da página de chamada para uma página de inicializador que inicia o assistente e navega até a primeira página do assistente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b50fc-154">Uma página de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]launcher <xref:System.Windows.Navigation.PageFunction%601>(a -less ) não é necessária, uma vez que uma página de chamada pode chamar a primeira página do assistente diretamente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b50fc-155">Entretanto, usar uma página de inicializador pode simplificar a inicialização do assistente, especialmente se ela for complexa.</span><span class="sxs-lookup"><span data-stu-id="b50fc-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="b50fc-156">Os usuários podem navegar entre páginas usando os botões Voltar e Avançar (ou hiperlinks).</span><span class="sxs-lookup"><span data-stu-id="b50fc-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="b50fc-157">Os usuários podem navegar entre páginas usando o diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="b50fc-158">Os usuários podem alterar a sequência de navegação se navegarem de volta pelo diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="b50fc-159">Os usuários podem cancelar o assistente em qualquer página do assistente pressionando um botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="b50fc-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="b50fc-160">Os usuários podem aceitar o assistente na última página do assistente pressionando um botão Concluir.</span><span class="sxs-lookup"><span data-stu-id="b50fc-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="b50fc-161">Se um assistente for cancelado, o assistente retornará um resultado apropriado e não retornará dados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="b50fc-162">Se um usuário aceitar um assistente, o assistente retornará um resultado apropriado, bem como os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="b50fc-163">Quando o assistente for concluído (aceito ou cancelado), as páginas que compreendem o assistente serão removidas do diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b50fc-164">Isso mantém cada instância do assistente isolada, evitando assim potenciais anomalias de dados ou de estado.</span><span class="sxs-lookup"><span data-stu-id="b50fc-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="b50fc-165">Navegação em uma topologia gerada dinamicamente</span><span class="sxs-lookup"><span data-stu-id="b50fc-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="b50fc-166">Em alguns aplicativos, a sequência em que duas ou mais páginas são navegadas só pode ser determinada em tempo de execução, seja pelo usuário, pelo aplicativo ou por dados externos.</span><span class="sxs-lookup"><span data-stu-id="b50fc-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="b50fc-167">A figura a seguir ilustra um conjunto de páginas com uma seqüência de navegação indeterminada:</span><span class="sxs-lookup"><span data-stu-id="b50fc-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Um conjunto de páginas com uma seqüência de navegação indeterminada.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="b50fc-169">A próxima figura ilustra uma seqüência de navegação escolhida pelo usuário em tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="b50fc-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagrama que mostra uma seqüência de navegação escolhida no tempo de execução.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="b50fc-171">A sequência de navegação é conhecida como uma topologia gerada dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="b50fc-172">Para o usuário, assim como ocorre com as outras topologias de navegação, a experiência do usuário é a mesmo das topologias anteriores:</span><span class="sxs-lookup"><span data-stu-id="b50fc-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="b50fc-173">Navegar da página de chamada para uma página de inicializador que inicia o assistente e navega até a primeira página do assistente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="b50fc-174">Uma página de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]launcher <xref:System.Windows.Navigation.PageFunction%601>(a -less ) não é necessária, uma vez que uma página de chamada pode chamar a primeira página do assistente diretamente.</span><span class="sxs-lookup"><span data-stu-id="b50fc-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="b50fc-175">Entretanto, usar uma página de inicializador pode simplificar a inicialização do assistente, especialmente se ela for complexa.</span><span class="sxs-lookup"><span data-stu-id="b50fc-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="b50fc-176">Os usuários podem navegar entre páginas usando os botões Voltar e Avançar (ou hiperlinks).</span><span class="sxs-lookup"><span data-stu-id="b50fc-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="b50fc-177">Os usuários podem navegar entre páginas usando o diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="b50fc-178">Os usuários podem cancelar o assistente em qualquer página do assistente pressionando um botão Cancelar.</span><span class="sxs-lookup"><span data-stu-id="b50fc-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="b50fc-179">Os usuários podem aceitar o assistente na última página do assistente pressionando um botão Concluir.</span><span class="sxs-lookup"><span data-stu-id="b50fc-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="b50fc-180">Se um assistente for cancelado, o assistente retornará um resultado apropriado e não retornará dados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="b50fc-181">Se um usuário aceitar um assistente, o assistente retornará um resultado apropriado, bem como os dados coletados.</span><span class="sxs-lookup"><span data-stu-id="b50fc-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="b50fc-182">Quando o assistente for concluído (aceito ou cancelado), as páginas que compreendem o assistente serão removidas do diário.</span><span class="sxs-lookup"><span data-stu-id="b50fc-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="b50fc-183">Isso mantém cada instância do assistente isolada, evitando assim potenciais anomalias de dados ou de estado.</span><span class="sxs-lookup"><span data-stu-id="b50fc-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50fc-184">Confira também</span><span class="sxs-lookup"><span data-stu-id="b50fc-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="b50fc-185">Visão geral da navegação estruturada</span><span class="sxs-lookup"><span data-stu-id="b50fc-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
