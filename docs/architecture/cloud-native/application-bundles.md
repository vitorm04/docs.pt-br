---
title: Pacotes de aplicativos nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Pacotes de aplicativos nativos de nuvem
ms.date: 05/13/2020
ms.openlocfilehash: fc6ee96078650dccd2ebeb3e65a0a00c4e05ecdb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614338"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="5d779-103">Pacotes de aplicativos nativos de nuvem</span><span class="sxs-lookup"><span data-stu-id="5d779-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="5d779-104">Uma importante propriedade dos aplicativos nativos de nuvem é que eles aproveitam os recursos da nuvem para acelerar o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5d779-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="5d779-105">Esse design geralmente significa que um aplicativo completo usa diferentes tipos de tecnologias.</span><span class="sxs-lookup"><span data-stu-id="5d779-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="5d779-106">Os aplicativos podem ser enviados em contêineres do Docker, alguns serviços podem usar Azure Functions, enquanto outras partes podem ser executadas diretamente em máquinas virtuais alocadas em servidores de grande metal com aceleração de GPU de hardware.</span><span class="sxs-lookup"><span data-stu-id="5d779-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="5d779-107">Dois aplicativos nativos de nuvem são os mesmos, portanto, é difícil fornecer um único mecanismo para enviá-los.</span><span class="sxs-lookup"><span data-stu-id="5d779-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="5d779-108">Os contêineres do Docker podem ser executados em kubernetes usando um gráfico Helm para implantação.</span><span class="sxs-lookup"><span data-stu-id="5d779-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="5d779-109">O Azure Functions pode ser alocado usando modelos Terraform.</span><span class="sxs-lookup"><span data-stu-id="5d779-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="5d779-110">Por fim, as máquinas virtuais podem ser alocadas usando Terraform, mas são criadas usando Ansible.</span><span class="sxs-lookup"><span data-stu-id="5d779-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="5d779-111">Essa é uma bagunça de tecnologias e não há como empacotá-las juntas em um pacote razoável.</span><span class="sxs-lookup"><span data-stu-id="5d779-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="5d779-112">Até agora.</span><span class="sxs-lookup"><span data-stu-id="5d779-112">Until now.</span></span>

<span data-ttu-id="5d779-113">Os pacotes de aplicativos nativos de nuvem (CNABs) são um esforço conjunto por várias empresas que se envolvem com a Comunidade, como Microsoft, Docker e HashiCorp, para desenvolver uma especificação para empacotar aplicativos distribuídos.</span><span class="sxs-lookup"><span data-stu-id="5d779-113">Cloud Native Application Bundles (CNABs) are a joint effort by a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="5d779-114">O esforço foi anunciado em dezembro de 2018, portanto, ainda há um pouco de trabalho a ser feito para expor o esforço para a comunidade maior.</span><span class="sxs-lookup"><span data-stu-id="5d779-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="5d779-115">No entanto, já existe uma [especificação aberta](https://github.com/deislabs/cnab-spec) e uma implementação de referência conhecida como [duffle](https://duffle.sh/).</span><span class="sxs-lookup"><span data-stu-id="5d779-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="5d779-116">Essa ferramenta, que foi escrita em go, é um esforço conjunto entre o Docker e a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5d779-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="5d779-117">O CNABs pode conter diferentes tipos de tecnologias de instalação.</span><span class="sxs-lookup"><span data-stu-id="5d779-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="5d779-118">Isso permite que itens como gráficos Helm, modelos de Terraform e guias estratégicos Ansible coexistam no mesmo pacote.</span><span class="sxs-lookup"><span data-stu-id="5d779-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="5d779-119">Uma vez criados, os pacotes são independentes e portáteis; Eles podem ser instalados de um Pen stick.</span><span class="sxs-lookup"><span data-stu-id="5d779-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="5d779-120">Os pacotes são assinados criptograficamente para garantir que eles se originem da parte que afirma.</span><span class="sxs-lookup"><span data-stu-id="5d779-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="5d779-121">O núcleo de um CNAB é um arquivo chamado `bundle.json` .</span><span class="sxs-lookup"><span data-stu-id="5d779-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="5d779-122">Esse arquivo define o conteúdo do pacote, seja Terraform ou imagens ou qualquer outra coisa.</span><span class="sxs-lookup"><span data-stu-id="5d779-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="5d779-123">A Figura 11-9 define um CNAB que invoca alguns Terraform.</span><span class="sxs-lookup"><span data-stu-id="5d779-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="5d779-124">Observe, no entanto, que ela realmente define uma imagem de invocação que é usada para invocar o Terraform.</span><span class="sxs-lookup"><span data-stu-id="5d779-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="5d779-125">Quando empacotado, o arquivo do Docker localizado no diretório *CNAB* é incorporado a uma imagem do Docker, que será incluída no pacote.</span><span class="sxs-lookup"><span data-stu-id="5d779-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="5d779-126">Ter o Terraform instalado dentro de um contêiner do Docker no grupo significa que os usuários não precisam ter o Terraform instalado em seu computador para executar o agrupamento.</span><span class="sxs-lookup"><span data-stu-id="5d779-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

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

<span data-ttu-id="5d779-127">**Figura 10-18** -um arquivo Terraform de exemplo</span><span class="sxs-lookup"><span data-stu-id="5d779-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="5d779-128">O `bundle.json` também define um conjunto de parâmetros que são passados para o Terraform.</span><span class="sxs-lookup"><span data-stu-id="5d779-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="5d779-129">A parametrização do pacote permite a instalação em uma variedade de ambientes diferentes.</span><span class="sxs-lookup"><span data-stu-id="5d779-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="5d779-130">O formato CNAB também é flexível, permitindo que ele seja usado em qualquer nuvem.</span><span class="sxs-lookup"><span data-stu-id="5d779-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="5d779-131">Ele pode até ser usado em soluções locais, como [OpenStack](https://www.openstack.org/).</span><span class="sxs-lookup"><span data-stu-id="5d779-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="5d779-132">Decisões DevOpss</span><span class="sxs-lookup"><span data-stu-id="5d779-132">DevOps Decisions</span></span>

<span data-ttu-id="5d779-133">Há tantas ferramentas incríveis no DevOps de espaço em dia e até mesmo livros e artigos fantásticos sobre como obter sucesso.</span><span class="sxs-lookup"><span data-stu-id="5d779-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="5d779-134">Um livro favorito para começar a usar o DevOps Journey é [o projeto Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), que segue a transformação de uma empresa fictícia da NoOps para a DevOps.</span><span class="sxs-lookup"><span data-stu-id="5d779-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="5d779-135">Uma coisa é para determinados: o DevOps não é mais um "bom para ter" ao implantar aplicativos complexos e nativos de nuvem.</span><span class="sxs-lookup"><span data-stu-id="5d779-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="5d779-136">É um requisito e deve ser planejado e reoriginado no início de qualquer projeto.</span><span class="sxs-lookup"><span data-stu-id="5d779-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="5d779-137">Referências</span><span class="sxs-lookup"><span data-stu-id="5d779-137">References</span></span>

- [<span data-ttu-id="5d779-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="5d779-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="5d779-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="5d779-139">Azure Resource Manager</span></span>](https://azure.microsoft.com/documentation/articles/resource-group-overview/)
- [<span data-ttu-id="5d779-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="5d779-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="5d779-141">CLI do Azure</span><span class="sxs-lookup"><span data-stu-id="5d779-141">Azure CLI</span></span>](https://docs.microsoft.com/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="5d779-142">[Anterior](infrastructure-as-code.md) 
> [Avançar](summary.md)</span><span class="sxs-lookup"><span data-stu-id="5d779-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
