---
title: "Introdução aos contêineres e ao Docker"
description: "Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 31260dc372f87305ad9d4556673a1cc94e24bfcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="da8ea-104">Introdução aos contêineres e ao Docker</span><span class="sxs-lookup"><span data-stu-id="da8ea-104">Introduction to containers and Docker</span></span>

<span data-ttu-id="da8ea-105">O uso de contêineres é uma abordagem de desenvolvimento de software na qual um aplicativo ou serviço, suas dependências e sua configuração (abstraídos como arquivos de manifesto de implantação) são empacotados juntos como uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="da8ea-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="da8ea-106">Você poderá então testar o aplicativo em contêineres como uma unidade e implantado como uma instância de imagem de contêiner no sistema operacional do host.</span><span class="sxs-lookup"><span data-stu-id="da8ea-106">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="da8ea-107">Assim como o setor logístico usa contêineres padronizados para transportar os bens em navios, trens ou caminhões independentemente da carga que eles contém, os contêineres de software agem como uma unidade de software padrão que pode conter diferentes dependências e códigos.</span><span class="sxs-lookup"><span data-stu-id="da8ea-107">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="da8ea-108">Colocar o software em contêineres possibilita que desenvolvedores e profissionais de TI implantem tais contêineres em diferentes ambientes com pouca ou sem nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="da8ea-108">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="da8ea-109">Os contêineres também isolam os aplicativos uns dos outros em um sistema operacional compartilhado.</span><span class="sxs-lookup"><span data-stu-id="da8ea-109">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="da8ea-110">Os aplicativos em contêineres são executados sobre um host do contêiner que, por sua vez, é executado no sistema operacional (Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="da8ea-110">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="da8ea-111">Dessa forma, os contêineres ocupam uma superfície significativamente menor do que as imagens de VM (máquina virtual).</span><span class="sxs-lookup"><span data-stu-id="da8ea-111">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="da8ea-112">Cada contêiner pode executar um aplicativo Web ou um serviço inteiro, conforme mostrado na Figura 1-1.</span><span class="sxs-lookup"><span data-stu-id="da8ea-112">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="da8ea-113">Figura 1-1: vários contêineres em execução em um host de contêiner</span><span class="sxs-lookup"><span data-stu-id="da8ea-113">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="da8ea-114">Neste exemplo, o Host do Docker é um host de contêiner e App1, App2, Svc 1 e Svc 2 são aplicativos ou serviços em contêineres.</span><span class="sxs-lookup"><span data-stu-id="da8ea-114">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="da8ea-115">Outra vantagem do uso de contêineres é a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="da8ea-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="da8ea-116">É possível expandir rapidamente criando novos contêineres para tarefas de curto prazo.</span><span class="sxs-lookup"><span data-stu-id="da8ea-116">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="da8ea-117">Do ponto de vista do aplicativo, *criar uma instância de uma imagem* (criar um contêiner) é semelhante a criar uma instância de um processo, como um serviço ou aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="da8ea-117">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="da8ea-118">No entanto, para assegurar a confiabilidade, ao executar várias instâncias da mesma imagem em vários servidores host, geralmente é melhor que cada contêiner (instância da imagem) seja executado em um servidor host ou em uma VM diferente em domínios de falha diferentes.</span><span class="sxs-lookup"><span data-stu-id="da8ea-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="da8ea-119">Resumindo, os contêineres oferecem os benefícios de isolamento, portabilidade, agilidade, escalabilidade e controle em todo o fluxo de trabalho do ciclo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da8ea-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="da8ea-120">O benefício mais importante é o isolamento fornecido entre desenvolvimento e operações.</span><span class="sxs-lookup"><span data-stu-id="da8ea-120">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="da8ea-121">[Next] (what-is-docker.md)</span><span class="sxs-lookup"><span data-stu-id="da8ea-121">[Next] (what-is-docker.md)</span></span>
