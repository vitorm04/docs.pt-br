---
title: Visão geral da assincronia
description: Saiba como a programação assíncrona é uma técnica chave que torna fácil lidar com o bloqueio de E/S e operações simultâneas em vários núcleos.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 2f76eb7d2b769b59809bec81aefacb7cec90a450
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106694"
---
# <a name="async-overview"></a><span data-ttu-id="6e6b7-103">Visão geral da assincronia</span><span class="sxs-lookup"><span data-stu-id="6e6b7-103">Async Overview</span></span>

<span data-ttu-id="6e6b7-104">Não muito tempo atrás, os aplicativos ficavam mais rápidos simplesmente comprando um computador ou servidor mais novo e então essa tendência parou.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="6e6b7-105">Na verdade, ela foi invertida.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-105">In fact, it reversed.</span></span> <span data-ttu-id="6e6b7-106">Surgiram telefones celulares com chips ARM de núcleo único de 1 GHz e as cargas de trabalho do servidor passaram para VMs.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="6e6b7-107">Os usuários ainda querem uma interface do usuário responsiva e os proprietários de negócios querem servidores que ajustem a escala com seus negócios.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="6e6b7-108">A transição para celular e nuvem e uma população conectada à Internet de >3B usuários resultaram em um novo conjunto de padrões de software.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

- <span data-ttu-id="6e6b7-109">Os aplicativos cliente devem estar sempre ativos, sempre conectados e constantemente responsivos à interação do usuário (por exemplo, toque) com classificações altas na loja de aplicativos!</span><span class="sxs-lookup"><span data-stu-id="6e6b7-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="6e6b7-110">Os serviços devem lidar com picos de tráfego escalando e reduzindo horizontalmente sem problemas.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="6e6b7-111">A programação assíncrona é uma técnica chave que torna fácil de lidar com o bloqueio de E/S e operações simultâneas em vários núcleos.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="6e6b7-112">O .NET fornece a capacidade para os aplicativos e serviços serem responsivos e elásticos com modelos de programação assíncrona fáceis de usar e em nível de linguagem em C#, VB e F#.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="6e6b7-113">Por que escrever código assíncrono?</span><span class="sxs-lookup"><span data-stu-id="6e6b7-113">Why Write Async Code?</span></span>

<span data-ttu-id="6e6b7-114">Os aplicativos modernos fazem amplo uso de E/S de arquivos e rede.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="6e6b7-115">As APIs de E/S tradicionalmente bloqueiam por padrão, resultando em experiências de usuário e utilização de hardware ruins, a menos que você deseje aprender e usar padrões desafiadores.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="6e6b7-116">O modelo de programação assíncrona em nível de linguagem e as APIs assíncronas baseadas em tarefa invertem esse modelo, tornando a execução assíncrona o padrão com poucos novos conceitos para aprender.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="6e6b7-117">O código assíncrono tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="6e6b7-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="6e6b7-118">Lida com mais solicitações de servidor gerando threads para lidar com mais solicitações enquanto espera as solicitações de E/S retornarem.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="6e6b7-119">Permite que as interfaces do usuário sejam mais responsivas gerando threads para a interação da interface do usuário enquanto espera as solicitações de E/S e fazendo a transição do trabalho de longa execução para outros núcleos de CPU.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="6e6b7-120">Muitas das APIs do .NET mais novas são assíncronas.</span><span class="sxs-lookup"><span data-stu-id="6e6b7-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="6e6b7-121">É fácil escrever código assíncrono no .NET!</span><span class="sxs-lookup"><span data-stu-id="6e6b7-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="6e6b7-122">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="6e6b7-122">What's next?</span></span>

<span data-ttu-id="6e6b7-123">Para obter mais informações, consulte os comentários no tópico [Assincronia detalhada](async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b7-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="6e6b7-124">O tópico [Padrões de programação assíncrona](asynchronous-programming-patterns/index.md) fornece uma visão geral dos três padrões de programação assíncronos com suporte no .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6e6b7-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="6e6b7-125">[APM (Modelo assíncrono de programação)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (herdado)</span><span class="sxs-lookup"><span data-stu-id="6e6b7-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="6e6b7-126">[EAP (Padrão assíncrono baseado em evento)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (herdado)</span><span class="sxs-lookup"><span data-stu-id="6e6b7-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="6e6b7-127">[TAP (Padrão assíncrono baseado em tarefa)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recomendado para novos desenvolvimentos)</span><span class="sxs-lookup"><span data-stu-id="6e6b7-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="6e6b7-128">Para obter mais informações sobre o modelo de programação baseado em tarefa recomendado, consulte o tópico [Programação assíncrona baseada em tarefas](parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b7-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
