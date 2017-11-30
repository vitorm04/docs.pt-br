---
title: "Registros, imagens e contêineres do docker"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Registros, imagens e contêineres do docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="22af6-104">Registros, imagens e contêineres do docker</span><span class="sxs-lookup"><span data-stu-id="22af6-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="22af6-105">Ao usar o Docker, um desenvolvedor cria um aplicativo ou serviço e pacotes-lo e suas dependências em uma imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="22af6-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="22af6-106">Uma imagem é uma representação estática do aplicativo ou serviço e a configuração e as dependências.</span><span class="sxs-lookup"><span data-stu-id="22af6-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="22af6-107">Para executar o aplicativo ou serviço, a imagem do aplicativo é instanciada para criar um contêiner, que serão executados no host do Docker.</span><span class="sxs-lookup"><span data-stu-id="22af6-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="22af6-108">Inicialmente, contêineres são testados em um ambiente de desenvolvimento ou de um computador.</span><span class="sxs-lookup"><span data-stu-id="22af6-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="22af6-109">Os desenvolvedores devem armazenar imagens em um registro, que atua como uma biblioteca de imagens e é necessário ao implantar o orchestrators de produção.</span><span class="sxs-lookup"><span data-stu-id="22af6-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="22af6-110">Docker mantém um registro público via [Docker Hub](https://hub.docker.com/); outros fornecedores fornecem os registros para diferentes coleções de imagens.</span><span class="sxs-lookup"><span data-stu-id="22af6-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="22af6-111">Como alternativa, as empresas podem ter um registro privado no local para suas próprias imagens do Docker.</span><span class="sxs-lookup"><span data-stu-id="22af6-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="22af6-112">Figura 2-4 mostra como imagens e registros no Docker se relacionam com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="22af6-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="22af6-113">Ele também mostra as várias ofertas de registro de fornecedores.</span><span class="sxs-lookup"><span data-stu-id="22af6-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="22af6-114">**Figura 2-4**.</span><span class="sxs-lookup"><span data-stu-id="22af6-114">**Figure 2-4**.</span></span> <span data-ttu-id="22af6-115">Taxonomia Docker termos e conceitos</span><span class="sxs-lookup"><span data-stu-id="22af6-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="22af6-116">Colocar imagens em um registro permite que você armazene os bits de aplicativo estático e imutável, incluindo todas as suas dependências em um nível de estrutura.</span><span class="sxs-lookup"><span data-stu-id="22af6-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="22af6-117">Essas imagens podem ser implantado em vários ambientes e com controle de versão e, portanto, fornecem uma unidade de implantação consistente.</span><span class="sxs-lookup"><span data-stu-id="22af6-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="22af6-118">Registros de imagem privada hospedada no local ou na nuvem, são recomendados quando:</span><span class="sxs-lookup"><span data-stu-id="22af6-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="22af6-119">As imagens não devem ser compartilhadas publicamente devido a confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="22af6-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="22af6-120">Você deseja ter a latência de rede mínima entre as imagens e o ambiente de implantação escolhida.</span><span class="sxs-lookup"><span data-stu-id="22af6-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="22af6-121">Por exemplo, se seu ambiente de produção é uma nuvem do Azure, você provavelmente desejará armazenar as imagens no registro de contêiner do Azure para que a latência de rede será mínima.</span><span class="sxs-lookup"><span data-stu-id="22af6-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="22af6-122">De maneira semelhante, se seu ambiente de produção for local, convém ter um local registro confiável do Docker disponíveis na mesma rede local.</span><span class="sxs-lookup"><span data-stu-id="22af6-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="22af6-123">[Anterior] (docker-terminology.md) [Avançar] (... /NET-Core-NET-Framework-Containers/index.MD)</span><span class="sxs-lookup"><span data-stu-id="22af6-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
