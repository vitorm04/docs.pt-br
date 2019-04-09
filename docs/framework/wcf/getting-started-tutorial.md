---
title: 'Tutorial: Introdução a aplicativos do Windows Communication Foundation'
description: Esses tutoriais fornece uma introdução para a criação de aplicativos do WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137913"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a><span data-ttu-id="7c031-103">Tutorial: Introdução a aplicativos do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7c031-103">Tutorial: Get started with Windows Communication Foundation applications</span></span>
<span data-ttu-id="7c031-104">A seguinte série de tutoriais apresentam a você para o Windows Communication Foundation (WCF) experiência de programação.</span><span class="sxs-lookup"><span data-stu-id="7c031-104">The following series of tutorials introduce you to the Windows Communication Foundation (WCF) programming experience.</span></span> <span data-ttu-id="7c031-105">Trabalhar com esses tutoriais na ordem lhe dará um entendimento introdutório das etapas necessárias para criar aplicativos do WCF.</span><span class="sxs-lookup"><span data-stu-id="7c031-105">Working through these tutorials in order will give you an introductory understanding of the steps required to create WCF applications.</span></span> <span data-ttu-id="7c031-106">Depois de terminar, você terá um serviço WCF em execução e um cliente do WCF que chama o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c031-106">After you finish, you'll have a running WCF service and a WCF client that calls the service.</span></span> 

<span data-ttu-id="7c031-107">O tutorial presume que você está usando o Visual Studio como ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="7c031-107">The tutorial assumes you're using Visual Studio as the development environment.</span></span> <span data-ttu-id="7c031-108">Se você estiver usando outro ambiente de desenvolvimento, ignore as instruções específicas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7c031-108">If you're using another development environment, ignore the Visual Studio-specific instructions.</span></span> 

<span data-ttu-id="7c031-109">Para aplicativos de WCF de exemplo que você pode baixar e executar, consulte [exemplos do Windows Communication Foundation](samples/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c031-109">For sample WCF applications that you can download and run, see [Windows Communication Foundation samples](samples/index.md).</span></span> <span data-ttu-id="7c031-110">Para obter uma introdução aos exemplos, consulte [exemplo de Introdução](samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7c031-110">For an introduction to the samples, see [Getting started sample](samples/getting-started-sample.md).</span></span>

<span data-ttu-id="7c031-111">Para obter informações mais detalhadas sobre a criação de serviços e clientes, consulte [programação de WCF básica](basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="7c031-111">For more in-depth information about creating services and clients, see [Basic WCF programming](basic-wcf-programming.md).</span></span>

## <a name="wcf-tutorials"></a><span data-ttu-id="7c031-112">Tutoriais do WCF</span><span class="sxs-lookup"><span data-stu-id="7c031-112">WCF tutorials</span></span>

<span data-ttu-id="7c031-113">Os três primeiros tutoriais descrevem como definir um contrato de serviço do WCF, como implementá-lo e como hospedá-lo.</span><span class="sxs-lookup"><span data-stu-id="7c031-113">The first three tutorials describe how to define a WCF service contract, how to implement it, and how to host it.</span></span> <span data-ttu-id="7c031-114">O serviço que você cria é auto-hospedado em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="7c031-114">The service that you create is self-hosted within a console application.</span></span> <span data-ttu-id="7c031-115">Você também pode hospedar serviços no Microsoft Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="7c031-115">You can also host services under Microsoft Internet Information Services (IIS).</span></span> <span data-ttu-id="7c031-116">Para obter mais informações, confira [Como: Hospedar um serviço WCF no IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="7c031-116">For more information, see [How to: Host a WCF Service in IIS](feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span> <span data-ttu-id="7c031-117">Embora você pode usar código para configurar o serviço no tutorial, você também pode [configurar os serviços dentro de um arquivo de configuração](configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="7c031-117">Although you use code to configure the service in the tutorial, you can also [configure services within a configuration file](configuring-services-using-configuration-files.md).</span></span> 

- [<span data-ttu-id="7c031-118">Tutorial: Definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7c031-118">Tutorial: Define a service contract</span></span>](how-to-define-a-wcf-service-contract.md)

    <span data-ttu-id="7c031-119">Você pode criar um contrato do WCF com uma interface definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="7c031-119">You create a WCF contract with a user-defined interface.</span></span> <span data-ttu-id="7c031-120">Este contrato define a funcionalidade que o serviço expõe.</span><span class="sxs-lookup"><span data-stu-id="7c031-120">This contract defines the functionality that the service exposes.</span></span>

- [<span data-ttu-id="7c031-121">Tutorial: Implementar um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="7c031-121">Tutorial: Implement a service contract</span></span>](how-to-implement-a-wcf-contract.md)

    <span data-ttu-id="7c031-122">Depois de definir um contrato, você deve implementá-la com uma classe de serviço.</span><span class="sxs-lookup"><span data-stu-id="7c031-122">After you define a contract, you must implement it with a service class.</span></span>

- [<span data-ttu-id="7c031-123">Tutorial: Hospedar e executar um serviço básico</span><span class="sxs-lookup"><span data-stu-id="7c031-123">Tutorial: Host and run a basic service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)

    <span data-ttu-id="7c031-124">Configurar um ponto de extremidade para o serviço e hospedar o serviço em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="7c031-124">Configure an endpoint for the service and host the service in a console application.</span></span> <span data-ttu-id="7c031-125">Para um serviço se torne ativa, você deve configurá-lo e hospedá-lo em um ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7c031-125">For a service to become active, you must configure it and host it within a run-time environment.</span></span> <span data-ttu-id="7c031-126">Esse ambiente de tempo de execução cria o serviço e controla seu contexto e o tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="7c031-126">This run-time environment creates the service and controls its context and lifetime.</span></span>

<span data-ttu-id="7c031-127">Os próximos dois tutoriais descrevem como criar, configurar e usar um aplicativo cliente para chamar as operações de serviço expõe.</span><span class="sxs-lookup"><span data-stu-id="7c031-127">The next two tutorials describe how to create, configure, and use a client application to call the operations the service exposes.</span></span> <span data-ttu-id="7c031-128">Os serviços publicam metadados que definem as informações que um aplicativo cliente precisa para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c031-128">Services publish metadata that define the information a client application needs to communicate with the service.</span></span> <span data-ttu-id="7c031-129">Visual Studio automatiza o processo de acesso a esses metadados e usa-o para construir o aplicativo cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c031-129">Visual Studio automates the process of accessing this metadata and uses it to construct the client application for the service.</span></span> <span data-ttu-id="7c031-130">Se você decidir não usar o Visual Studio, você pode usar o [ferramenta de utilitário de metadados ServiceModel (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7c031-130">If you decide not to use Visual Studio, you can use the [ServiceModel Metadata Utility tool (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) instead.</span></span>

- [<span data-ttu-id="7c031-131">Tutorial: Criar um cliente</span><span class="sxs-lookup"><span data-stu-id="7c031-131">Tutorial: Create a client</span></span>](how-to-create-a-wcf-client.md)

    <span data-ttu-id="7c031-132">Recupere metadados para a criação de um proxy de cliente WCF de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="7c031-132">Retrieve metadata for creating a WCF client proxy from a WCF service.</span></span> <span data-ttu-id="7c031-133">Recuperar metadados, usando o Visual Studio para adicionar uma referência de serviço ou você pode usar a ferramenta Utilitário de metadados ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="7c031-133">You retrieve metadata by using Visual Studio to add a service reference or you can use the ServiceModel Metadata Utility tool.</span></span> <span data-ttu-id="7c031-134">Especifique o ponto de extremidade que o cliente usa para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c031-134">You specify the endpoint that the client uses to access the service.</span></span>

- [<span data-ttu-id="7c031-135">Tutorial: Usar um cliente</span><span class="sxs-lookup"><span data-stu-id="7c031-135">Tutorial: Use a client</span></span>](how-to-use-a-wcf-client.md)

    <span data-ttu-id="7c031-136">Use o proxy de cliente do WCF para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="7c031-136">Use the WCF client proxy to call the service operations.</span></span>

## <a name="reference"></a><span data-ttu-id="7c031-137">Referência</span><span class="sxs-lookup"><span data-stu-id="7c031-137">Reference</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a><span data-ttu-id="7c031-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c031-138">See also</span></span>

- [<span data-ttu-id="7c031-139">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="7c031-139">Conceptual overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="7c031-140">Guia de documentação</span><span class="sxs-lookup"><span data-stu-id="7c031-140">Guide to the documentation</span></span>](guide-to-the-documentation.md)
- [<span data-ttu-id="7c031-141">O que é o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7c031-141">What is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="7c031-142">Detalhes de recursos do WCF</span><span class="sxs-lookup"><span data-stu-id="7c031-142">WCF feature details</span></span>](feature-details/index.md)
- [<span data-ttu-id="7c031-143">Ciclo de vida de programação básico</span><span class="sxs-lookup"><span data-stu-id="7c031-143">Basic programming lifecycle</span></span>](basic-programming-lifecycle.md)
- [<span data-ttu-id="7c031-144">Compilando clientes</span><span class="sxs-lookup"><span data-stu-id="7c031-144">Building clients</span></span>](building-clients.md)
- [<span data-ttu-id="7c031-145">Programação de WCF básica</span><span class="sxs-lookup"><span data-stu-id="7c031-145">Basic WCF programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="7c031-146">Como: Criar um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="7c031-146">How to: Create a duplex contract</span></span>](feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="7c031-147">Como: Serviços do Access com um contrato duplex</span><span class="sxs-lookup"><span data-stu-id="7c031-147">How to: Access services with a duplex contract</span></span>](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="7c031-148">Ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="7c031-148">ServiceModel Metadata Utility tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="7c031-149">Como: Use Svcutil.exe para baixar documentos de metadados</span><span class="sxs-lookup"><span data-stu-id="7c031-149">How to: Use Svcutil.exe to download metadata documents</span></span>](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [<span data-ttu-id="7c031-150">Como: Publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="7c031-150">How to: Publish metadata for a service using a configuration file</span></span>](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="7c031-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="7c031-151">Using bindings to configure services and clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7c031-152">Exemplo de Introdução</span><span class="sxs-lookup"><span data-stu-id="7c031-152">Getting started sample</span></span>](samples/getting-started-sample.md)
- [<span data-ttu-id="7c031-153">Exemplos do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="7c031-153">Windows Communication Foundation samples</span></span>](samples/index.md)
- [<span data-ttu-id="7c031-154">Self-Host</span><span class="sxs-lookup"><span data-stu-id="7c031-154">Self-Host</span></span>](samples/self-host.md)
