---
title: "Registros, imagens e contêineres do Docker"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Registros, imagens e contêineres do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 79dccadfba066c673e8ef7ea5eaf1051a434ff3a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="a940d-104">Registros, imagens e contêineres do Docker</span><span class="sxs-lookup"><span data-stu-id="a940d-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="a940d-105">Ao usar o Docker, um desenvolvedor cria um aplicativo ou serviço e empacota a ele e suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="a940d-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="a940d-106">Uma imagem é uma representação estática do aplicativo ou do serviço e de sua configuração e dependências.</span><span class="sxs-lookup"><span data-stu-id="a940d-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="a940d-107">Para executar o aplicativo ou o serviço, uma instância da imagem do aplicativo é criada para criar um contêiner, que estará em execução no host Docker.</span><span class="sxs-lookup"><span data-stu-id="a940d-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="a940d-108">Inicialmente, os contêineres são testados em um ambiente de desenvolvimento ou em um computador.</span><span class="sxs-lookup"><span data-stu-id="a940d-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="a940d-109">Os desenvolvedores devem armazenar imagens em um Registro, que funciona como uma biblioteca de imagens e é necessário ao implantar em orquestradores de produção.</span><span class="sxs-lookup"><span data-stu-id="a940d-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="a940d-110">O Docker mantém um Registro público por meio do [Hub do Docker](https://hub.docker.com/); outros fornecedores fornecem os Registros para diferentes coleções de imagens.</span><span class="sxs-lookup"><span data-stu-id="a940d-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="a940d-111">Como alternativa, as empresas podem ter um Registro privado local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="a940d-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="a940d-112">A Figura 2-4 mostra como imagens e Registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="a940d-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="a940d-113">Ela também mostra as várias ofertas de Registro dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="a940d-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="a940d-114">**Figura 2-4**.</span><span class="sxs-lookup"><span data-stu-id="a940d-114">**Figure 2-4**.</span></span> <span data-ttu-id="a940d-115">Taxonomia de termos e conceitos do Docker</span><span class="sxs-lookup"><span data-stu-id="a940d-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="a940d-116">Colocar imagens em um Registro permite a você armazenar os bits de aplicativo estáticos e imutáveis, incluindo todas as suas dependências em um nível de estrutura.</span><span class="sxs-lookup"><span data-stu-id="a940d-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="a940d-117">A versão dessas imagens podem ser controladas e elas podem ser implantadas em vários ambientes e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="a940d-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="a940d-118">Registros de imagem privados, hospedados localmente ou na nuvem, são recomendados quando:</span><span class="sxs-lookup"><span data-stu-id="a940d-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="a940d-119">Suas imagens não devem ser compartilhadas publicamente devido à confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="a940d-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="a940d-120">Você deseja ter latência de rede mínima entre suas imagens e o ambiente de implantação escolhido.</span><span class="sxs-lookup"><span data-stu-id="a940d-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="a940d-121">Por exemplo, se seu ambiente de produção for uma nuvem do Azure, você provavelmente desejará armazenar as imagens no Registro de Contêiner do Azure para que a latência de rede seja mínima.</span><span class="sxs-lookup"><span data-stu-id="a940d-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="a940d-122">De maneira semelhante, se seu ambiente de produção for local, tenha um Registro Confiável do Docker local disponível na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="a940d-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a940d-123">[Anterior] (docker-terminology.md) [Próximo] (../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="a940d-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
