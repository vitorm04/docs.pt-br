---
title: "Registros, imagens e contêineres do docker"
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b115b25d8ae335aafbe41bac0d694170be7e3c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="882eb-104">Registros, imagens e contêineres do docker</span><span class="sxs-lookup"><span data-stu-id="882eb-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="882eb-105">Ao usar o Docker, você cria um aplicativo ou serviço e pacote ele e suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="882eb-105">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="882eb-106">Uma imagem é uma representação estática do aplicativo ou serviço e a configuração e as dependências.</span><span class="sxs-lookup"><span data-stu-id="882eb-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="882eb-107">Para executar o aplicativo ou serviço, a imagem do aplicativo é instanciada para criar um contêiner, que serão executados no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="882eb-107">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="882eb-108">Inicialmente, contêineres são testados em um ambiente de desenvolvimento ou de um computador.</span><span class="sxs-lookup"><span data-stu-id="882eb-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="882eb-109">Você pode armazenar imagens em um registro, que atua como uma biblioteca de imagens.</span><span class="sxs-lookup"><span data-stu-id="882eb-109">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="882eb-110">Ao implantar o orchestrators de produção, é necessário um registro.</span><span class="sxs-lookup"><span data-stu-id="882eb-110">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="882eb-111">Docker mantém um registro público via [Docker Hub](https://hub.docker.com/); outros fornecedores fornecem os registros para diferentes coleções de imagens.</span><span class="sxs-lookup"><span data-stu-id="882eb-111">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="882eb-112">Como alternativa, as empresas podem ter um registro privado no local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="882eb-112">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="882eb-113">Figura 1-4 mostra como imagens e registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="882eb-113">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="882eb-114">Ele também mostra as várias ofertas de registro de fornecedores.</span><span class="sxs-lookup"><span data-stu-id="882eb-114">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="882eb-115">Figura 1-4: taxonomia Docker termos e conceitos</span><span class="sxs-lookup"><span data-stu-id="882eb-115">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="882eb-116">Ao colocar imagens em um registro, você pode armazenar bits de aplicativo estático e imutável, incluindo todas as suas dependências, em um nível de estrutura.</span><span class="sxs-lookup"><span data-stu-id="882eb-116">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="882eb-117">Você pode versão e implantar imagens em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="882eb-117">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="882eb-118">Registros de imagem privada, hospedado no local ou na nuvem, são recomendados para as seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="882eb-118">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="882eb-119">As imagens não devem ser compartilhadas publicamente devido a confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="882eb-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="882eb-120">Você deseja ter a latência de rede mínima entre as imagens e o ambiente de implantação escolhida.</span><span class="sxs-lookup"><span data-stu-id="882eb-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="882eb-121">Por exemplo, se seu ambiente de produção é o Azure, você provavelmente desejará armazenar as imagens no registro de contêiner do Azure para que a latência de rede será mínima.</span><span class="sxs-lookup"><span data-stu-id="882eb-121">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="882eb-122">De maneira semelhante, se seu ambiente de produção for local, convém ter um local registro confiável do Docker disponíveis na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="882eb-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="882eb-123">[Anterior] (docker-terminology.md) [Avançar] (Docker-aplicativo-ciclo de vida/index.md)</span><span class="sxs-lookup"><span data-stu-id="882eb-123">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
