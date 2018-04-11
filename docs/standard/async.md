---
title: Visão geral da assincronia
description: Saiba como a programação assíncrona é uma técnica chave que torna fácil lidar com o bloqueio de E/S e operações simultâneas em vários núcleos.
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2dddc21dfb124fe97c397a156743981a67e4037
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="async-overview"></a><span data-ttu-id="8cb2b-104">Visão geral da assincronia</span><span class="sxs-lookup"><span data-stu-id="8cb2b-104">Async Overview</span></span>

<span data-ttu-id="8cb2b-105">Não muito tempo atrás, os aplicativos ficavam mais rápidos simplesmente comprando um computador ou servidor mais novo e então essa tendência parou.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="8cb2b-106">Na verdade, ela foi invertida.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-106">In fact, it reversed.</span></span> <span data-ttu-id="8cb2b-107">Surgiram telefones celulares com chips ARM de núcleo único de 1 GHz e as cargas de trabalho do servidor passaram para VMs.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="8cb2b-108">Os usuários ainda querem uma interface do usuário responsiva e os proprietários de negócios querem servidores que ajustem a escala com seus negócios.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="8cb2b-109">A transição para celular e nuvem e uma população conectada à Internet de >3B usuários resultaram em um novo conjunto de padrões de software.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="8cb2b-110">Os aplicativos cliente devem estar sempre ativos, sempre conectados e constantemente responsivos à interação do usuário (por exemplo, toque) com classificações altas na loja de aplicativos!</span><span class="sxs-lookup"><span data-stu-id="8cb2b-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="8cb2b-111">Os serviços devem lidar com picos de tráfego escalando e reduzindo horizontalmente sem problemas.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="8cb2b-112">A programação assíncrona é uma técnica chave que torna fácil de lidar com o bloqueio de E/S e operações simultâneas em vários núcleos.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="8cb2b-113">O .NET fornece a capacidade para os aplicativos e serviços serem responsivos e elásticos com modelos de programação assíncrona fáceis de usar e em nível de linguagem em C#, VB e F#.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="8cb2b-114">Por que escrever código assíncrono?</span><span class="sxs-lookup"><span data-stu-id="8cb2b-114">Why Write Async Code?</span></span>

<span data-ttu-id="8cb2b-115">Os aplicativos modernos fazem amplo uso de E/S de arquivos e rede.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="8cb2b-116">As APIs de E/S tradicionalmente bloqueiam por padrão, resultando em experiências de usuário e utilização de hardware ruins, a menos que você deseje aprender e usar padrões desafiadores.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="8cb2b-117">O modelo de programação assíncrona em nível de linguagem e as APIs assíncronas baseadas em tarefa invertem esse modelo, tornando a execução assíncrona o padrão com poucos novos conceitos para aprender.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="8cb2b-118">O código assíncrono tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="8cb2b-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="8cb2b-119">Lida com mais solicitações de servidor gerando threads para lidar com mais solicitações enquanto espera as solicitações de E/S retornarem.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="8cb2b-120">Permite que as interfaces do usuário sejam mais responsivas gerando threads para a interação da interface do usuário enquanto espera as solicitações de E/S e fazendo a transição do trabalho de longa execução para outros núcleos de CPU.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="8cb2b-121">Muitas das APIs do .NET mais novas são assíncronas.</span><span class="sxs-lookup"><span data-stu-id="8cb2b-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="8cb2b-122">É fácil escrever código assíncrono no .NET!</span><span class="sxs-lookup"><span data-stu-id="8cb2b-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="8cb2b-123">O que vem a seguir?</span><span class="sxs-lookup"><span data-stu-id="8cb2b-123">What's next?</span></span>

<span data-ttu-id="8cb2b-124">Para aprofundar em conceitos de assincronia e programação, consulte [Assincronia detalhada](async-in-depth.md) e [Programação assíncrona baseada em tarefa](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="8cb2b-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>
