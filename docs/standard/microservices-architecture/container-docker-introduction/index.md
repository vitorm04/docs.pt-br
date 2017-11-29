---
title: "Introdução aos contêineres e ao Docker"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Introdução aos contêineres e ao Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: bb9466129287b0f10ace3c6d1129fb94b7a443e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="4b589-104">Introdução aos contêineres e ao Docker</span><span class="sxs-lookup"><span data-stu-id="4b589-104">Introduction to Containers and Docker</span></span>

<span data-ttu-id="4b589-105">O uso de contêineres é uma abordagem de desenvolvimento de software na qual um aplicativo ou serviço, suas dependências e sua configuração (abstraídos como arquivos de manifesto de implantação) são empacotados juntos como uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="4b589-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="4b589-106">O aplicativo em contêineres pode ser testado como uma unidade e implantado como uma instância de imagem de contêiner no SO (sistema operacional) do host.</span><span class="sxs-lookup"><span data-stu-id="4b589-106">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="4b589-107">Assim como os contêineres de remessa permitem que as mercadorias sejam transportadas por navio, trem ou caminhão, independentemente da carga que contenham, os contêineres de software agem como uma unidade de software padrão que pode conter diferentes dependências e códigos.</span><span class="sxs-lookup"><span data-stu-id="4b589-107">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="4b589-108">Inserir o software em contêineres dessa maneira permite que desenvolvedores e profissionais de TI os implantem em diferentes ambientes com pouca ou sem nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="4b589-108">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="4b589-109">Os contêineres também isolam os aplicativos uns dos outros em um sistema operacional compartilhado.</span><span class="sxs-lookup"><span data-stu-id="4b589-109">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="4b589-110">Os aplicativos em contêineres são executados com base em um host do contêiner que por sua vez é executado no sistema operacional (Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="4b589-110">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="4b589-111">Os contêineres, portanto, ocupam um espaço significativamente menor do que as imagens de VM (máquina virtual).</span><span class="sxs-lookup"><span data-stu-id="4b589-111">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="4b589-112">Cada contêiner pode executar um aplicativo Web ou um serviço inteiro, conforme é mostrado na Figura 2-1.</span><span class="sxs-lookup"><span data-stu-id="4b589-112">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="4b589-113">Neste exemplo, o host do Docker é um host de contêiner e App1, App2, Svc 1 e Svc 2 são aplicativos ou serviços em contêineres.</span><span class="sxs-lookup"><span data-stu-id="4b589-113">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![](./media/image1.png)

<span data-ttu-id="4b589-114">**Figura 2-1**.</span><span class="sxs-lookup"><span data-stu-id="4b589-114">**Figure 2-1**.</span></span> <span data-ttu-id="4b589-115">Vários contêineres em execução em um host de contêiner</span><span class="sxs-lookup"><span data-stu-id="4b589-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="4b589-116">Outro benefício do uso de contêineres é a escalabilidade.</span><span class="sxs-lookup"><span data-stu-id="4b589-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="4b589-117">Você pode aumentar rapidamente, criando novos contêineres para tarefas de curto prazo.</span><span class="sxs-lookup"><span data-stu-id="4b589-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="4b589-118">Do ponto de vista do aplicativo, criar uma instância de uma imagem (criar um contêiner) é semelhante a criar uma instância de um processo, como um serviço ou aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="4b589-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="4b589-119">No entanto, para assegurar a confiabilidade, ao executar várias instâncias da mesma imagem em vários servidores host, geralmente é melhor que cada contêiner (instância da imagem) seja executado em um servidor host ou em uma VM diferente em domínios de falha diferentes.</span><span class="sxs-lookup"><span data-stu-id="4b589-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="4b589-120">Resumindo, os contêineres oferecem os benefícios de portabilidade, agilidade, escalabilidade, controle e isolamento em todo o fluxo de trabalho do ciclo de vida do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4b589-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="4b589-121">O benefício mais importante é o isolamento fornecido entre desenvolvimento e operações.</span><span class="sxs-lookup"><span data-stu-id="4b589-121">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4b589-122">[Previous] (../index.md) [Next] (docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="4b589-122">[Previous] (../index.md) [Next] (docker-defined.md)</span></span>
