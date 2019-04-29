---
title: Registros, imagens e contêineres do Docker
description: Saiba o papel importante que registros desempenham gerais na maneira como Docker de implantação de aplicativos.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e69490734a03cf58bf8534bc9e31110a11d44c58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795312"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="01b21-103">Registros, imagens e contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="01b21-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="01b21-104">Ao usar o Docker, você cria um aplicativo ou serviço e o empacota com suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="01b21-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="01b21-105">Uma imagem é uma representação estática do aplicativo ou do serviço e de sua configuração e dependências.</span><span class="sxs-lookup"><span data-stu-id="01b21-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="01b21-106">Para executar o aplicativo ou o serviço, uma instância da imagem do aplicativo é criada para criar um contêiner, que estará em execução no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="01b21-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="01b21-107">Inicialmente, os contêineres são testados em um ambiente de desenvolvimento ou em um computador.</span><span class="sxs-lookup"><span data-stu-id="01b21-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="01b21-108">Armazenar imagens em um registro, que atua como uma biblioteca de imagens.</span><span class="sxs-lookup"><span data-stu-id="01b21-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="01b21-109">Você precisa de um registro ao implantar em orquestradores de produção.</span><span class="sxs-lookup"><span data-stu-id="01b21-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="01b21-110">O Docker mantém um Registro público por meio do [Hub do Docker](https://hub.docker.com/); outros fornecedores fornecem os Registros para diferentes coleções de imagens, incluindo [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="01b21-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="01b21-111">Como alternativa, as empresas podem ter um Registro privado local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="01b21-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="01b21-112">Figura 1-4 mostra como imagens e registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="01b21-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="01b21-113">Ela também mostra as várias ofertas de Registro dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="01b21-113">It also shows the multiple registry offerings from vendors.</span></span>

![Taxonomia básica no Docker: O registro é como um para sua estante onde as imagens são armazenados e disponíveis para serem retirados para a criação de contêineres para executar serviços ou aplicativos web.](./media/image4.png)

<span data-ttu-id="01b21-118">**Figura 1-4**.</span><span class="sxs-lookup"><span data-stu-id="01b21-118">**Figure 1-4**.</span></span> <span data-ttu-id="01b21-119">Taxonomia de termos e conceitos do Docker</span><span class="sxs-lookup"><span data-stu-id="01b21-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="01b21-120">Ao colocar imagens em um registro, você pode armazenar os bits de aplicativo estáticos e imutáveis, incluindo todas as suas dependências, em um nível de framework.</span><span class="sxs-lookup"><span data-stu-id="01b21-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="01b21-121">Você pode a versão e implantar imagens em vários ambientes, em seguida e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="01b21-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="01b21-122">Registros de imagem privados, hospedados localmente ou na nuvem, são recomendados quando:</span><span class="sxs-lookup"><span data-stu-id="01b21-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="01b21-123">Suas imagens não devem ser compartilhadas publicamente devido à confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="01b21-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="01b21-124">Você deseja ter latência de rede mínima entre suas imagens e o ambiente de implantação escolhido.</span><span class="sxs-lookup"><span data-stu-id="01b21-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="01b21-125">Por exemplo, se seu ambiente de produção é o Azure, você provavelmente desejará armazenar as imagens no [registro de contêiner do Azure](https://azure.microsoft.com/services/container-registry/) para que a latência de rede é mínima.</span><span class="sxs-lookup"><span data-stu-id="01b21-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="01b21-126">De maneira semelhante, se seu ambiente de produção for local, tenha um Registro Confiável do Docker local disponível na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="01b21-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="01b21-127">[Anterior](docker-terminology.md)
>[Próximo](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="01b21-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
