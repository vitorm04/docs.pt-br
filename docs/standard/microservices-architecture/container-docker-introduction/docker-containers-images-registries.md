---
title: Registros, imagens e contêineres do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Registros, imagens e contêineres do Docker
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639901"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="17864-103">Registros, imagens e contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="17864-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="17864-104">Ao usar o Docker, um desenvolvedor cria um aplicativo ou serviço e empacota a ele e suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="17864-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="17864-105">Uma imagem é uma representação estática do aplicativo ou do serviço e de sua configuração e dependências.</span><span class="sxs-lookup"><span data-stu-id="17864-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="17864-106">Para executar o aplicativo ou o serviço, uma instância da imagem do aplicativo é criada para criar um contêiner, que estará em execução no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="17864-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="17864-107">Inicialmente, os contêineres são testados em um ambiente de desenvolvimento ou em um computador.</span><span class="sxs-lookup"><span data-stu-id="17864-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="17864-108">Os desenvolvedores devem armazenar imagens em um Registro, que funciona como uma biblioteca de imagens e é necessário ao implantar em orquestradores de produção.</span><span class="sxs-lookup"><span data-stu-id="17864-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="17864-109">O Docker mantém um Registro público por meio do [Hub do Docker](https://hub.docker.com/); outros fornecedores fornecem os Registros para diferentes coleções de imagens, incluindo [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="17864-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="17864-110">Como alternativa, as empresas podem ter um Registro privado local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="17864-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="17864-111">A Figura 2-4 mostra como imagens e Registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="17864-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="17864-112">Ela também mostra as várias ofertas de Registro dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="17864-112">It also shows the multiple registry offerings from vendors.</span></span>

![Taxonomia básica no Docker: o Registro é como uma estante de livros em que as imagens são armazenadas e ficam disponíveis para serem retiradas para a criação de contêineres para executar os serviços ou aplicativos Web.](./media/image5.PNG)

<span data-ttu-id="17864-117">**Figura 2-4**.</span><span class="sxs-lookup"><span data-stu-id="17864-117">**Figure 2-4**.</span></span> <span data-ttu-id="17864-118">Taxonomia de termos e conceitos do Docker</span><span class="sxs-lookup"><span data-stu-id="17864-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="17864-119">Colocar imagens em um Registro permite a você armazenar os bits de aplicativo estáticos e imutáveis, incluindo todas as suas dependências em um nível de estrutura.</span><span class="sxs-lookup"><span data-stu-id="17864-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="17864-120">A versão dessas imagens podem ser controladas e elas podem ser implantadas em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="17864-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="17864-121">Registros de imagem privados, hospedados localmente ou na nuvem, são recomendados quando:</span><span class="sxs-lookup"><span data-stu-id="17864-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="17864-122">Suas imagens não devem ser compartilhadas publicamente devido à confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="17864-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="17864-123">Você deseja ter latência de rede mínima entre suas imagens e o ambiente de implantação escolhido.</span><span class="sxs-lookup"><span data-stu-id="17864-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="17864-124">Por exemplo, se o ambiente de produção for uma nuvem do Azure, você provavelmente desejará armazenar as imagens no [Registro de Contêiner do Azure](https://azure.microsoft.com/services/container-registry/) para que a latência de rede seja mínima.</span><span class="sxs-lookup"><span data-stu-id="17864-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="17864-125">De maneira semelhante, se seu ambiente de produção for local, tenha um Registro Confiável do Docker local disponível na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="17864-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="17864-126">[Anterior](docker-terminology.md)
>[Próximo](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="17864-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
