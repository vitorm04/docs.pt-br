---
title: Visão geral da assincronia
description: Saiba como a programação assíncrona é uma técnica chave que torna fácil lidar com o bloqueio de E/S e operações simultâneas em vários núcleos.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 1570909b7b416eff81dd90a936ff5ed10aad94f1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346081"
---
# <a name="async-overview"></a><span data-ttu-id="34b37-103">Visão geral da assincronia</span><span class="sxs-lookup"><span data-stu-id="34b37-103">Async Overview</span></span>

<span data-ttu-id="34b37-104">Não muito tempo atrás, os aplicativos ficavam mais rápidos simplesmente comprando um computador ou servidor mais novo e então essa tendência parou.</span><span class="sxs-lookup"><span data-stu-id="34b37-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="34b37-105">Na verdade, ela foi invertida.</span><span class="sxs-lookup"><span data-stu-id="34b37-105">In fact, it reversed.</span></span> <span data-ttu-id="34b37-106">Surgiram telefones celulares com chips ARM de núcleo único de 1 GHz e as cargas de trabalho do servidor passaram para VMs.</span><span class="sxs-lookup"><span data-stu-id="34b37-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="34b37-107">Os usuários ainda querem uma interface do usuário responsiva e os proprietários de negócios querem servidores que ajustem a escala com seus negócios.</span><span class="sxs-lookup"><span data-stu-id="34b37-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="34b37-108">A transição para celular e nuvem e uma população conectada à Internet de >3B usuários resultaram em um novo conjunto de padrões de software.</span><span class="sxs-lookup"><span data-stu-id="34b37-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

- <span data-ttu-id="34b37-109">Os aplicativos cliente devem estar sempre ativos, sempre conectados e constantemente responsivos à interação do usuário (por exemplo, toque) com classificações altas na loja de aplicativos!</span><span class="sxs-lookup"><span data-stu-id="34b37-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="34b37-110">Os serviços devem lidar com picos de tráfego escalando e reduzindo horizontalmente sem problemas.</span><span class="sxs-lookup"><span data-stu-id="34b37-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="34b37-111">A programação assíncrona é uma técnica chave que torna fácil de lidar com o bloqueio de E/S e operações simultâneas em vários núcleos.</span><span class="sxs-lookup"><span data-stu-id="34b37-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="34b37-112">O .NET fornece a capacidade para que aplicativos e serviços sejam responsivos e elásticos com modelos de programação assíncrona de nível de linguagem fáceis C#de usar no, F#Visual Basic e.</span><span class="sxs-lookup"><span data-stu-id="34b37-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="34b37-113">Por que escrever código assíncrono?</span><span class="sxs-lookup"><span data-stu-id="34b37-113">Why Write Async Code?</span></span>

<span data-ttu-id="34b37-114">Os aplicativos modernos fazem amplo uso de E/S de arquivos e rede.</span><span class="sxs-lookup"><span data-stu-id="34b37-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="34b37-115">As APIs de E/S tradicionalmente bloqueiam por padrão, resultando em experiências de usuário e utilização de hardware ruins, a menos que você deseje aprender e usar padrões desafiadores.</span><span class="sxs-lookup"><span data-stu-id="34b37-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="34b37-116">O modelo de programação assíncrona em nível de linguagem e as APIs assíncronas baseadas em tarefa invertem esse modelo, tornando a execução assíncrona o padrão com poucos novos conceitos para aprender.</span><span class="sxs-lookup"><span data-stu-id="34b37-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="34b37-117">O código assíncrono tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="34b37-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="34b37-118">Lida com mais solicitações de servidor gerando threads para lidar com mais solicitações enquanto espera as solicitações de E/S retornarem.</span><span class="sxs-lookup"><span data-stu-id="34b37-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="34b37-119">Permite que as interfaces do usuário sejam mais responsivas gerando threads para a interação da interface do usuário enquanto espera as solicitações de E/S e fazendo a transição do trabalho de longa execução para outros núcleos de CPU.</span><span class="sxs-lookup"><span data-stu-id="34b37-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="34b37-120">Muitas das APIs do .NET mais novas são assíncronas.</span><span class="sxs-lookup"><span data-stu-id="34b37-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="34b37-121">É fácil escrever código assíncrono no .NET!</span><span class="sxs-lookup"><span data-stu-id="34b37-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="34b37-122">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="34b37-122">What's next?</span></span>

<span data-ttu-id="34b37-123">Para obter mais informações, consulte os comentários no tópico [Assincronia detalhada](async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="34b37-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="34b37-124">O tópico [Padrões de programação assíncrona](asynchronous-programming-patterns/index.md) fornece uma visão geral dos três padrões de programação assíncronos com suporte no .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="34b37-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="34b37-125">[APM (Modelo assíncrono de programação)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (herdado)</span><span class="sxs-lookup"><span data-stu-id="34b37-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="34b37-126">[EAP (Padrão assíncrono baseado em evento)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (herdado)</span><span class="sxs-lookup"><span data-stu-id="34b37-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="34b37-127">[TAP (Padrão assíncrono baseado em tarefa)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recomendado para novos desenvolvimentos)</span><span class="sxs-lookup"><span data-stu-id="34b37-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="34b37-128">Para obter mais informações sobre o modelo de programação baseado em tarefa recomendado, consulte o tópico [Programação assíncrona baseada em tarefas](parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="34b37-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
