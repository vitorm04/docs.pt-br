---
title: "Cenários de rede ponto a ponto"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: d23b1a64-2e08-4014-882a-c1dd766bdcc2
caps.latest.revision: 4
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: edf493f0999dc78e6b1065176f1638b23667d9b3
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="peer-to-peer-networking-scenarios"></a><span data-ttu-id="1ab97-102">Cenários de rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="1ab97-102">Peer-to-Peer Networking Scenarios</span></span>
<span data-ttu-id="1ab97-103">Rede ponto a ponto permite ou aprimora os cenários a seguir:</span><span class="sxs-lookup"><span data-stu-id="1ab97-103">Peer-to-peer networking enables or enhances the following scenarios:</span></span>  
  
## <a name="real-time-communications-rtc"></a><span data-ttu-id="1ab97-104">RTC (comunicação em tempo real)</span><span class="sxs-lookup"><span data-stu-id="1ab97-104">Real-Time Communications (RTC)</span></span>  
  
-   <span data-ttu-id="1ab97-105">Mensagens instantâneas sem servidor</span><span class="sxs-lookup"><span data-stu-id="1ab97-105">Serverless Instant Messaging</span></span>  
  
 <span data-ttu-id="1ab97-106">A RTC existe atualmente.</span><span class="sxs-lookup"><span data-stu-id="1ab97-106">RTC exists today.</span></span> <span data-ttu-id="1ab97-107">Atualmente, os usuários do computador podem conversar por chat e ter conversações por voz ou vídeo com seus colegas.</span><span class="sxs-lookup"><span data-stu-id="1ab97-107">Computer users can chat and have voice or video conversations with their peers today.</span></span> <span data-ttu-id="1ab97-108">No entanto, muitos dos programas existentes e dos respectivos protocolos de comunicação dependem de servidores para funcionar.</span><span class="sxs-lookup"><span data-stu-id="1ab97-108">However, many of the existing programs and their communications protocols rely on servers to function.</span></span> <span data-ttu-id="1ab97-109">Se você estiver participando de uma rede sem fio ad hoc ou fizer parte de uma rede isolada, não será possível usar esses recursos RTC.</span><span class="sxs-lookup"><span data-stu-id="1ab97-109">If you are participating in an ad-hoc wireless network or are a part of an isolated network, you are unable to use these RTC facilities.</span></span> <span data-ttu-id="1ab97-110">A tecnologia Pessoas ao Meu Redor permite a extensão de tecnologias de RTC para esses ambientes de rede adicionais.</span><span class="sxs-lookup"><span data-stu-id="1ab97-110">Peer-to-peer technology allows the extension of RTC technologies to these additional networking environments.</span></span>  
  
-   <span data-ttu-id="1ab97-111">Jogos e emparelhamento (organizar uma partida) em tempo real</span><span class="sxs-lookup"><span data-stu-id="1ab97-111">Real-time matchmaking and gameplay</span></span>  
  
 <span data-ttu-id="1ab97-112">Semelhante ao RTC, o jogo em tempo real existe nos dias de hoje.</span><span class="sxs-lookup"><span data-stu-id="1ab97-112">Similar to RTC, real-time game play exists today.</span></span> <span data-ttu-id="1ab97-113">Há muitos sites de jogos baseados na Web que atendem à comunidade de jogos através da Internet.</span><span class="sxs-lookup"><span data-stu-id="1ab97-113">There are many Web-based game sites that cater to the gaming community via the Internet.</span></span> <span data-ttu-id="1ab97-114">Eles oferecem a capacidade de localizar outros jogadores com interesses semelhantes e jogar juntos.</span><span class="sxs-lookup"><span data-stu-id="1ab97-114">They offer the ability to find other gamers with similar interests and play a game together.</span></span> <span data-ttu-id="1ab97-115">O problema é que os sites de jogos existem apenas na Internet e são direcionados para o jogador ávido, que deseja competir com os melhores gamers do mundo.</span><span class="sxs-lookup"><span data-stu-id="1ab97-115">The problem is that the game sites exist only on the Internet and are geared toward the avid gamer who wants to play against the best gamers in the world.</span></span> <span data-ttu-id="1ab97-116">Esses sites acompanham e fornecem as estatísticas para ajudar no processo.</span><span class="sxs-lookup"><span data-stu-id="1ab97-116">These sites track and provide the statistics to help in the process.</span></span> <span data-ttu-id="1ab97-117">No entanto, esses sites não permitem que um jogador configure um jogo ad-hoc entre amigos em uma variedade de ambientes de rede.</span><span class="sxs-lookup"><span data-stu-id="1ab97-117">However, these sites do not allow a gamer to set up an ad-hoc game among friends in a variety of networking environments.</span></span> <span data-ttu-id="1ab97-118">A rede ponto a ponto pode oferecer essa capacidade.</span><span class="sxs-lookup"><span data-stu-id="1ab97-118">Peer-to-peer networking can provide this capability.</span></span>  
  
## <a name="collaboration"></a><span data-ttu-id="1ab97-119">Colaboração</span><span class="sxs-lookup"><span data-stu-id="1ab97-119">Collaboration</span></span>  
  
-   <span data-ttu-id="1ab97-120">Espaços de trabalho de projeto atingindo uma meta</span><span class="sxs-lookup"><span data-stu-id="1ab97-120">Project workspaces solving a goal</span></span>  
  
 <span data-ttu-id="1ab97-121">Aplicativos de espaço de trabalho compartilhado permitem a criação de grupos de trabalho ad hoc e, em seguida, permitem que os proprietários do grupo de trabalho preencham o espaço de trabalho compartilhado com as ferramentas e o conteúdo que permitirão que o grupo solucione um problema.</span><span class="sxs-lookup"><span data-stu-id="1ab97-121">Shared workspace applications allow for the creation of ad-hoc workgroups and then allow the workgroup owners to populate the shared workspace with the tools and content that will allow the group to solve a problem.</span></span> <span data-ttu-id="1ab97-122">Isso pode incluir arquivos, ferramentas de produtividade e quadros de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1ab97-122">This could include message boards, productivity tools, and files.</span></span>  
  
-   <span data-ttu-id="1ab97-123">Compartilhamento de arquivos com outras pessoas</span><span class="sxs-lookup"><span data-stu-id="1ab97-123">Sharing files with others</span></span>  
  
 <span data-ttu-id="1ab97-124">Um subconjunto do compartilhamento de espaço de trabalho de projeto é a capacidade de compartilhar arquivos.</span><span class="sxs-lookup"><span data-stu-id="1ab97-124">A subset of project workspace sharing is the ability to share files.</span></span> <span data-ttu-id="1ab97-125">Embora essa capacidade exista atualmente com a versão atual do Windows, ela pode ser aprimorada por meio da rede ponto a ponto para disponibilizar o conteúdo do arquivo de uma maneira fácil e amigável.</span><span class="sxs-lookup"><span data-stu-id="1ab97-125">Although this ability exists today with the current version of Windows, it can be enhanced through peer-to-peer networking to make file content available in an easy and friendly way.</span></span> <span data-ttu-id="1ab97-126">Permitir o acesso fácil à incrível riqueza de conteúdo na borda da Internet ou em ambientes de computação ad-hoc aumenta o valor da computação de rede.</span><span class="sxs-lookup"><span data-stu-id="1ab97-126">Allowing easy access to the incredible wealth of content at the edge of the Internet or in ad-hoc computing environments increases the value of network computing.</span></span>  
  
-   <span data-ttu-id="1ab97-127">Compartilhando experiências</span><span class="sxs-lookup"><span data-stu-id="1ab97-127">Sharing experiences</span></span>  
  
 <span data-ttu-id="1ab97-128">Com a conectividade sem fio se tornando mais predominante, a rede ponto a ponto permite que você esteja online em um grupo de pares e seja capaz de compartilhar suas experiências (como um pôr-do-sol, um show de rock ou um cruzeiro de férias) enquanto elas estão ocorrendo.</span><span class="sxs-lookup"><span data-stu-id="1ab97-128">With wireless connectivity becoming more prevalent, peer-to-peer networking allows you to be online in a group of peers and to be able to share your experiences (such as a sunset, a rock concert, or a vacation cruise) while they are occurring.</span></span>  
  
## <a name="content-distribution"></a><span data-ttu-id="1ab97-129">Distribuição de conteúdo</span><span class="sxs-lookup"><span data-stu-id="1ab97-129">Content Distribution</span></span>  
  
-   <span data-ttu-id="1ab97-130">Mensagens de texto</span><span class="sxs-lookup"><span data-stu-id="1ab97-130">Text messages</span></span>  
  
 <span data-ttu-id="1ab97-131">A rede ponto a ponto pode permitir a divulgação de informações baseadas em texto na forma de arquivos ou mensagens para um grande grupo de usuários.</span><span class="sxs-lookup"><span data-stu-id="1ab97-131">Peer-to-peer networking can allow for the dissemination of text-based information in the form of files or messages to a large group of users.</span></span> <span data-ttu-id="1ab97-132">Um exemplo é uma lista de notícias.</span><span class="sxs-lookup"><span data-stu-id="1ab97-132">An example is a news list.</span></span>  
  
-  
  
-   <span data-ttu-id="1ab97-133">Áudio e vídeo</span><span class="sxs-lookup"><span data-stu-id="1ab97-133">Audio and video</span></span>  
  
 <span data-ttu-id="1ab97-134">A rede ponto a ponto também pode permitir a divulgação de informações de áudio ou vídeo para um grande grupo de usuários, tal como um grande concerto ou uma reunião da empresa.</span><span class="sxs-lookup"><span data-stu-id="1ab97-134">Peer-to-peer networking can also allow for the dissemination of audio or video information to a large group of users, such as a large concert or company meeting.</span></span> <span data-ttu-id="1ab97-135">Para distribuir o conteúdo hoje em dia, você deve configurar servidores de alta capacidade para coletar e distribuir a carga entre centenas ou milhares de usuários.</span><span class="sxs-lookup"><span data-stu-id="1ab97-135">To distribute the content today, you must configure high-capacity servers to collect and distribute the load to hundreds or thousands of users.</span></span> <span data-ttu-id="1ab97-136">Com a rede ponto a ponto, apenas alguns pares realmente obteriam o conteúdo de servidores centralizados.</span><span class="sxs-lookup"><span data-stu-id="1ab97-136">With peer-to-peer networking, only a handful of peers would actually get their content from the centralized servers.</span></span> <span data-ttu-id="1ab97-137">Esses pares propagariam essas informações para algumas pessoas mais, que por sua vez as enviariam para outras e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1ab97-137">These peers would flood this information out to a few more people who send it to others, and so on.</span></span> <span data-ttu-id="1ab97-138">A carga de distribuir o conteúdo é distribuída para os pares na nuvem.</span><span class="sxs-lookup"><span data-stu-id="1ab97-138">The load of distributing the content is distributed to the peers in the cloud.</span></span> <span data-ttu-id="1ab97-139">Um par que desejasse receber o conteúdo localizaria o par mais próximo distribuindo o conteúdo e obteria o conteúdo dele.</span><span class="sxs-lookup"><span data-stu-id="1ab97-139">A peer that wants to receive the content would find the closest distributing peer and get the content from them.</span></span>  
  
-  
  
-   <span data-ttu-id="1ab97-140">Distribuição de atualizações de produtos</span><span class="sxs-lookup"><span data-stu-id="1ab97-140">Distribution of product updates</span></span>  
  
 <span data-ttu-id="1ab97-141">Redes ponto a ponto também pode fornecer um mecanismo eficiente para distribuir software como atualizações de produtos (service packs e atualizações de segurança).</span><span class="sxs-lookup"><span data-stu-id="1ab97-141">Peer-to-peer networking can also provide an efficient mechanism to distribute software such as product updates (security updates and service packs).</span></span> <span data-ttu-id="1ab97-142">Um par que tenha uma conexão a um servidor de distribuição de software pode obter a atualização de produto e propagá-la a outros membros do seu grupo.</span><span class="sxs-lookup"><span data-stu-id="1ab97-142">A peer that has a connection to a software distribution server can obtain the product update and propagate it to the other members of its group.</span></span>  
  
-  
  
## <a name="distributed-processing"></a><span data-ttu-id="1ab97-143">Processamento distribuído</span><span class="sxs-lookup"><span data-stu-id="1ab97-143">Distributed Processing</span></span>  
  
-   <span data-ttu-id="1ab97-144">Divisão e distribuição de uma tarefa</span><span class="sxs-lookup"><span data-stu-id="1ab97-144">Division and distribution of a task</span></span>  
  
 <span data-ttu-id="1ab97-145">Uma tarefa de computação grande pode primeiro ser dividida em tarefas de computação menores separadas adequadas para os recursos de computação de um par.</span><span class="sxs-lookup"><span data-stu-id="1ab97-145">A large computing task can first be divided into separate smaller computing tasks well suited to the computing resources of a peer.</span></span> <span data-ttu-id="1ab97-146">Um par pode fazer a divisão da tarefa de computação grande.</span><span class="sxs-lookup"><span data-stu-id="1ab97-146">A peer could do the dividing of the large computing task.</span></span> <span data-ttu-id="1ab97-147">Em seguida, a rede ponto a ponto pode distribuir as tarefas individuais para os pares separados no grupo.</span><span class="sxs-lookup"><span data-stu-id="1ab97-147">Then, peer-to-peer networking can distribute the individual tasks to the separate peers in the group.</span></span> <span data-ttu-id="1ab97-148">Cada par executa sua tarefa de computação e reporta o resultado para um ponto de acúmulo centralizado.</span><span class="sxs-lookup"><span data-stu-id="1ab97-148">Each peer performs its computing task and reports its result back to a centralized accumulation point.</span></span>  
  
-   <span data-ttu-id="1ab97-149">Agregação de recursos do computador</span><span class="sxs-lookup"><span data-stu-id="1ab97-149">Aggregation of computer resources</span></span>  
  
 <span data-ttu-id="1ab97-150">Outra maneira de usar a rede ponto a ponto para processamento distribuído é executar programas em cada par que é executado durante tempos de processador ocioso e que faz parte de uma tarefa de computação maior que é coordenada por um servidor central.</span><span class="sxs-lookup"><span data-stu-id="1ab97-150">Another way to utilize peer-to-peer networking for distributed processing is to run programs on each peer that run during idle processor times and are part of a larger computing task that is coordinated by a central server.</span></span> <span data-ttu-id="1ab97-151">Agregando os processadores de vários computadores, redes ponto a ponto podem transformar um grupo de computadores de par em um grande processador paralelo para tarefas de computação grandes.</span><span class="sxs-lookup"><span data-stu-id="1ab97-151">By aggregating the processors of multiple computers, peer-to-peer networking can turn a group of peer computers into a large parallel processor for large computing tasks.</span></span>  
  
-  
  
## <a name="see-also"></a><span data-ttu-id="1ab97-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ab97-152">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Collaboration>

