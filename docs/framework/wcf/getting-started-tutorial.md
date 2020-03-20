---
title: 'Tutorial: Comece com os aplicativos da Windows Communication Foundation'
description: Esses tutoriais fornecem uma introdução para criar aplicativos WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184116"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="1ec8f-103">Tutorial: Comece com os aplicativos da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1ec8f-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="1ec8f-104">A série a seguir de tutoriais apresenta a experiência de programação da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1ec8f-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="1ec8f-105">Trabalhar através desses tutoriais em ordem lhe dará uma compreensão introdutória das etapas necessárias para criar aplicativos WCF.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="1ec8f-106">Depois de terminar, você terá um serviço WCF em execução e um cliente WCF que chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span>

<span data-ttu-id="1ec8f-107">O tutorial pressupõe que você está usando o Visual Studio como ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="1ec8f-108">Se você estiver usando outro ambiente de desenvolvimento, ignore as instruções específicas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span>

<span data-ttu-id="1ec8f-109">Para obter amostras de aplicativos WCF que você pode baixar e executar, consulte [amostras do Windows Communication Foundation](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="1ec8f-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="1ec8f-110">Para uma introdução às amostras, consulte [A amostra de Início](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1ec8f-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="1ec8f-111">Para obter informações mais detalhadas sobre a criação de serviços e clientes, consulte [programação Básica do WCF](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="1ec8f-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="1ec8f-112">Tutoriais do WCF</span><span class="sxs-lookup"><span data-stu-id="1ec8f-112">WCF tutorials</span></span>

<span data-ttu-id="1ec8f-113">Os três primeiros tutoriais descrevem como definir um contrato de serviço WCF, como implementá-lo e como hospedá-lo.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="1ec8f-114">O serviço que você cria é auto-hospedado dentro de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="1ec8f-115">Você também pode hospedar serviços em Serviços de Informações da Internet (IIS) da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="1ec8f-116">Para obter mais informações, consulte [Como hospedar um serviço WCF no IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="1ec8f-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="1ec8f-117">Embora você use código para configurar o serviço no tutorial, você também pode [configurar serviços dentro de um arquivo de configuração](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="1ec8f-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span>

- [<span data-ttu-id="1ec8f-118">Tutorial: Defina um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="1ec8f-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="1ec8f-119">Você cria um contrato WCF com uma interface definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="1ec8f-120">Este contrato define a funcionalidade que o serviço expõe.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="1ec8f-121">Tutorial: Implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="1ec8f-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="1ec8f-122">Depois de definir um contrato, você deve implementá-lo com uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="1ec8f-123">Tutorial: Hospede e execute um serviço básico</span><span class="sxs-lookup"><span data-stu-id="1ec8f-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="1ec8f-124">Configure um ponto final para o serviço e hospede o serviço em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="1ec8f-125">Para que um serviço se torne ativo, você deve configurá-lo e hospedá-lo em um ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="1ec8f-126">Esse ambiente de tempo de execução cria o serviço e controla seu contexto e vida útil.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="1ec8f-127">Os dois próximos tutoriais descrevem como criar, configurar e usar um aplicativo cliente para chamar as operações que o serviço expõe.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="1ec8f-128">Os serviços publicam metadados que definem as informações que um aplicativo cliente precisa para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="1ec8f-129">O Visual Studio automatiza o processo de acesso a esses metadados e os utiliza para construir o aplicativo cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="1ec8f-130">Se você decidir não usar o Visual Studio, você pode usar a [ferramenta ServiceModel Metadata Utility *(Svcutil.exe)*](servicemodel-metadata-utility-tool-svcutil-exe.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="1ec8f-131">Tutorial: Crie um cliente</span><span class="sxs-lookup"><span data-stu-id="1ec8f-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="1ec8f-132">Recupere metadados para criar um proxy de cliente WCF a partir de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="1ec8f-133">Você recupera metadados usando o Visual Studio para adicionar uma referência de serviço ou pode usar a ferramenta ServiceModel Metadata Utility.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="1ec8f-134">Você especifica o ponto final que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="1ec8f-135">Tutorial: Use um cliente</span><span class="sxs-lookup"><span data-stu-id="1ec8f-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="1ec8f-136">Use o proxy do cliente WCF para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="1ec8f-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="1ec8f-137">Referência</span><span class="sxs-lookup"><span data-stu-id="1ec8f-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="1ec8f-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ec8f-138">See also</span></span>

- [<span data-ttu-id="1ec8f-139">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="1ec8f-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="1ec8f-140">Guia da documentação</span><span class="sxs-lookup"><span data-stu-id="1ec8f-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="1ec8f-141">O que é a Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1ec8f-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="1ec8f-142">Detalhes de recursos do WCF</span><span class="sxs-lookup"><span data-stu-id="1ec8f-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="1ec8f-143">Ciclo de vida da programação básica</span><span class="sxs-lookup"><span data-stu-id="1ec8f-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="1ec8f-144">Construindo clientes</span><span class="sxs-lookup"><span data-stu-id="1ec8f-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="1ec8f-145">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="1ec8f-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="1ec8f-146">Como: Criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="1ec8f-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="1ec8f-147">Como: Acessar serviços com contrato duplex</span><span class="sxs-lookup"><span data-stu-id="1ec8f-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="1ec8f-148">Ferramenta serviceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1ec8f-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1ec8f-149">Como: Usar svcutil.exe para baixar documentos de metadados</span><span class="sxs-lookup"><span data-stu-id="1ec8f-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="1ec8f-150">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="1ec8f-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="1ec8f-151">Usando vinculações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1ec8f-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1ec8f-152">Obtendo amostra de início</span><span class="sxs-lookup"><span data-stu-id="1ec8f-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="1ec8f-153">Amostras da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1ec8f-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="1ec8f-154">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="1ec8f-154">Self-Host</span></span>](samples/self-host.md)
