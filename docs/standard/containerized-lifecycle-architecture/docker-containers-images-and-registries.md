---
title: Registros, imagens e contêineres do Docker
description: Saiba o importante papel geral desempenhado pelos registros no modo como o Docker implanta aplicativos.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641344"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="98f52-103">Registros, imagens e contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="98f52-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="98f52-104">Ao usar o Docker, você cria um aplicativo ou serviço e empacota a ele e suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="98f52-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="98f52-105">Uma imagem é uma representação estática do aplicativo ou do serviço e de sua configuração e dependências.</span><span class="sxs-lookup"><span data-stu-id="98f52-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="98f52-106">Para executar o aplicativo ou o serviço, uma instância da imagem do aplicativo é criada para criar um contêiner, que estará em execução no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="98f52-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="98f52-107">Inicialmente, os contêineres são testados em um ambiente de desenvolvimento ou em um computador.</span><span class="sxs-lookup"><span data-stu-id="98f52-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="98f52-108">Você armazena imagens em um registro que atua como uma biblioteca de imagens.</span><span class="sxs-lookup"><span data-stu-id="98f52-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="98f52-109">É necessário um registro ao implantar em orquestradores de produção.</span><span class="sxs-lookup"><span data-stu-id="98f52-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="98f52-110">O Docker mantém um Registro público por meio do [Hub do Docker](https://hub.docker.com/); outros fornecedores fornecem os Registros para diferentes coleções de imagens, incluindo [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="98f52-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="98f52-111">Como alternativa, as empresas podem ter um Registro privado local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="98f52-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="98f52-112">A Figura 1-4 mostra como imagens e registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="98f52-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="98f52-113">Ela também mostra as várias ofertas de Registro dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="98f52-113">It also shows the multiple registry offerings from vendors.</span></span>

![Taxonomia básica no Docker: o Registro é como uma estante de livros em que as imagens são armazenadas e ficam disponíveis para serem retiradas para a criação de contêineres para executar os serviços ou aplicativos Web.](./media/image4.png)

<span data-ttu-id="98f52-118">**Figura 1-4**.</span><span class="sxs-lookup"><span data-stu-id="98f52-118">**Figure 1-4**.</span></span> <span data-ttu-id="98f52-119">Taxonomia de termos e conceitos do Docker</span><span class="sxs-lookup"><span data-stu-id="98f52-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="98f52-120">Colocar imagens em um registro permite armazenar os bits de aplicativo estáticos e imutáveis, incluindo todas as suas dependências em um nível de estrutura.</span><span class="sxs-lookup"><span data-stu-id="98f52-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="98f52-121">A versão dessas imagens pode ser controlada e elas podem ser implantadas em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="98f52-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="98f52-122">Registros de imagem privados, hospedados localmente ou na nuvem, são recomendados quando:</span><span class="sxs-lookup"><span data-stu-id="98f52-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="98f52-123">Suas imagens não devem ser compartilhadas publicamente devido à confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="98f52-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="98f52-124">Você deseja ter latência de rede mínima entre suas imagens e o ambiente de implantação escolhido.</span><span class="sxs-lookup"><span data-stu-id="98f52-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="98f52-125">Por exemplo, se o ambiente de produção for o Azure, você provavelmente desejará armazenar as imagens no [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/) para que a latência de rede seja mínima.</span><span class="sxs-lookup"><span data-stu-id="98f52-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="98f52-126">De maneira semelhante, se seu ambiente de produção for local, tenha um Registro Confiável do Docker local disponível na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="98f52-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="98f52-127">[Anterior](docker-terminology.md)
>[Próximo](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="98f52-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
