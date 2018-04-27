---
title: Registros, imagens e contêineres do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8ba0cd3323467e07a33ffd4083e390d57fdce7ff
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="57690-103">Registros, imagens e contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="57690-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="57690-104">Ao usar o Docker, você cria um aplicativo ou serviço e pacote ele e suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="57690-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="57690-105">Uma imagem é uma representação estática do aplicativo ou do serviço e de sua configuração e dependências.</span><span class="sxs-lookup"><span data-stu-id="57690-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="57690-106">Para executar o aplicativo ou serviço, a imagem do aplicativo é instanciada para criar um contêiner, que serão executados no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="57690-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="57690-107">Inicialmente, os contêineres são testados em um ambiente de desenvolvimento ou em um computador.</span><span class="sxs-lookup"><span data-stu-id="57690-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="57690-108">Você pode armazenar imagens em um registro, que atua como uma biblioteca de imagens.</span><span class="sxs-lookup"><span data-stu-id="57690-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="57690-109">Ao implantar o orchestrators de produção, é necessário um registro.</span><span class="sxs-lookup"><span data-stu-id="57690-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="57690-110">O Docker mantém um Registro público por meio do [Hub do Docker](https://hub.docker.com/); outros fornecedores fornecem os Registros para diferentes coleções de imagens.</span><span class="sxs-lookup"><span data-stu-id="57690-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="57690-111">Como alternativa, as empresas podem ter um Registro privado local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="57690-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="57690-112">Figura 1-4 mostra como imagens e registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="57690-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="57690-113">Ela também mostra as várias ofertas de Registro dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="57690-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="57690-114">Figura 1-4: taxonomia Docker termos e conceitos</span><span class="sxs-lookup"><span data-stu-id="57690-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="57690-115">Ao colocar imagens em um registro, você pode armazenar bits de aplicativo estático e imutável, incluindo todas as suas dependências, em um nível de estrutura.</span><span class="sxs-lookup"><span data-stu-id="57690-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="57690-116">Você pode versão e implantar imagens em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="57690-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="57690-117">Registros de imagem privada, hospedado no local ou na nuvem, são recomendados para as seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="57690-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="57690-118">Suas imagens não devem ser compartilhadas publicamente devido à confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="57690-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="57690-119">Você deseja ter latência de rede mínima entre suas imagens e o ambiente de implantação escolhido.</span><span class="sxs-lookup"><span data-stu-id="57690-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="57690-120">Por exemplo, se seu ambiente de produção é o Azure, você provavelmente desejará armazenar as imagens no registro de contêiner do Azure para que a latência de rede será mínima.</span><span class="sxs-lookup"><span data-stu-id="57690-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="57690-121">De maneira semelhante, se seu ambiente de produção for local, tenha um Registro Confiável do Docker local disponível na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="57690-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="57690-122">[Anterior] (docker-terminology.md) [Avançar] (Docker-aplicativo-ciclo de vida/index.md)</span><span class="sxs-lookup"><span data-stu-id="57690-122">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
