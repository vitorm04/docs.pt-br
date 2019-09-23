---
title: Pacotes de aplicativos nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Pacotes de aplicativos nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 0c67035af08d3c337ff027f3742e1ce8a83f8d0f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183710"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="12a68-103">Pacotes de aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="12a68-103">Cloud Native Application Bundles</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="12a68-104">Uma importante propriedade dos aplicativos nativos de nuvem é que eles aproveitam as propriedades da nuvem para acelerar o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="12a68-104">A key property of cloud-native applications is that they leverage the properties of the cloud to speed up development.</span></span> <span data-ttu-id="12a68-105">Isso geralmente significa que um aplicativo completo usa diferentes tipos de tecnologias.</span><span class="sxs-lookup"><span data-stu-id="12a68-105">This often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="12a68-106">Os aplicativos podem ser enviados em contêineres do Docker, alguns serviços podem usar Azure Functions enquanto outras partes podem ser executadas diretamente em máquinas virtuais alocadas em servidores de metal grandes com aceleração de GPU de hardware.</span><span class="sxs-lookup"><span data-stu-id="12a68-106">Applications may be shipped in Docker containers, some services may use Azure Functions while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="12a68-107">Dois aplicativos nativos de nuvem são os mesmos, portanto, é difícil fornecer um único mecanismo para enviá-los.</span><span class="sxs-lookup"><span data-stu-id="12a68-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="12a68-108">Os contêineres do Docker podem ser executados em kubernetes usando um gráfico Helm para implantação.</span><span class="sxs-lookup"><span data-stu-id="12a68-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="12a68-109">O Azure Functions pode ser alocado usando modelos Terraform.</span><span class="sxs-lookup"><span data-stu-id="12a68-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="12a68-110">Por fim, as máquinas virtuais podem ser alocadas usando Terraform, mas são criadas usando Ansible.</span><span class="sxs-lookup"><span data-stu-id="12a68-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="12a68-111">Essa é uma bagunça de tecnologias e não há como empacotá-las juntas em um pacote razoável.</span><span class="sxs-lookup"><span data-stu-id="12a68-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="12a68-112">Até agora.</span><span class="sxs-lookup"><span data-stu-id="12a68-112">Until now.</span></span>

<span data-ttu-id="12a68-113">Os pacotes de aplicativos nativos de nuvem (CNABs) são um esforço conjunto de várias empresas que se envolvem com a Comunidade, como Microsoft, Docker e HashiCorp, para desenvolver uma especificação para empacotar aplicativos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="12a68-113">Cloud Native Application Bundles (CNABs) are a joint effort of a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="12a68-114">O esforço foi anunciado em dezembro de 2018, portanto, ainda há um pouco de trabalho a ser feito para expor o esforço para a comunidade maior.</span><span class="sxs-lookup"><span data-stu-id="12a68-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="12a68-115">No entanto, já existe uma [especificação aberta](https://github.com/deislabs/cnab-spec) e uma implementação de referência conhecida como [duffle](https://duffle.sh/).</span><span class="sxs-lookup"><span data-stu-id="12a68-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="12a68-116">Essa ferramenta, que foi escrita em go, é um esforço conjunto entre o Docker e a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="12a68-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="12a68-117">O CNABs pode conter diferentes tipos de tecnologias de instalação.</span><span class="sxs-lookup"><span data-stu-id="12a68-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="12a68-118">Isso permite que itens como gráficos Helm, modelos de Terraform e guias estratégicos Ansible coexistam no mesmo pacote.</span><span class="sxs-lookup"><span data-stu-id="12a68-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="12a68-119">Uma vez criados, os pacotes são independentes e portáteis; Eles podem ser instalados de um Pen stick.</span><span class="sxs-lookup"><span data-stu-id="12a68-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="12a68-120">Os pacotes são assinados criptograficamente para garantir que eles se originem da parte que afirma.</span><span class="sxs-lookup"><span data-stu-id="12a68-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="12a68-121">O núcleo de um CNAB é um arquivo chamado `bundle.json`.</span><span class="sxs-lookup"><span data-stu-id="12a68-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="12a68-122">Esse arquivo define o conteúdo do pacote, seja Terraform ou imagens ou qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="12a68-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="12a68-123">A Figura 11-9 define um CNAB que invoca alguns Terraform.</span><span class="sxs-lookup"><span data-stu-id="12a68-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="12a68-124">Observe, no entanto, que ela realmente define uma imagem de invocação que é usada para invocar o Terraform.</span><span class="sxs-lookup"><span data-stu-id="12a68-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="12a68-125">Quando empacotado, o arquivo do Docker localizado no diretório *CNAB* é incorporado a uma imagem do Docker, que será incluída no pacote.</span><span class="sxs-lookup"><span data-stu-id="12a68-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="12a68-126">Ter o Terraform instalado dentro de um contêiner do Docker no grupo significa que os usuários não precisam ter o Terraform instalado em seu computador para executar o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="12a68-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

<span data-ttu-id="12a68-127">**Figura 11-13** -um arquivo Terraform de exemplo</span><span class="sxs-lookup"><span data-stu-id="12a68-127">**Figure 11-13** - An example Terraform file</span></span>

<span data-ttu-id="12a68-128">O `bundle.json` também define um conjunto de parâmetros que são passados para o Terraform.</span><span class="sxs-lookup"><span data-stu-id="12a68-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="12a68-129">A parametrização do pacote permite a instalação em uma variedade de ambientes diferentes.</span><span class="sxs-lookup"><span data-stu-id="12a68-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="12a68-130">O formato CNAB também é flexível, permitindo que ele seja usado em qualquer nuvem.</span><span class="sxs-lookup"><span data-stu-id="12a68-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="12a68-131">Ele pode até ser usado em soluções locais, como [OpenStack](https://www.openstack.org/).</span><span class="sxs-lookup"><span data-stu-id="12a68-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="12a68-132">Decisões DevOpss</span><span class="sxs-lookup"><span data-stu-id="12a68-132">DevOps Decisions</span></span>

<span data-ttu-id="12a68-133">Há tantas ferramentas incríveis no DevOps de espaço em dia e até mesmo livros e artigos fantásticos sobre como obter sucesso.</span><span class="sxs-lookup"><span data-stu-id="12a68-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="12a68-134">Um livro favorito para começar a usar o DevOps Journey é [o projeto Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), que segue a transformação de uma empresa fictícia da NoOps para a DevOps.</span><span class="sxs-lookup"><span data-stu-id="12a68-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="12a68-135">Uma coisa é para determinados: A DevOps não é mais uma "boa para ter" ao implantar aplicativos complexos de nuvem nativos.</span><span class="sxs-lookup"><span data-stu-id="12a68-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="12a68-136">É um requisito e deve ser planejado e reoriginado no início de qualquer projeto.</span><span class="sxs-lookup"><span data-stu-id="12a68-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="12a68-137">Anterior</span><span class="sxs-lookup"><span data-stu-id="12a68-137">Previous</span></span>](infrastructure-as-code.md)
