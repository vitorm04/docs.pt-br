---
title: Suplementos e extensibilidade
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d288d321063512f91ad94b417bb1a6bf38c9ef9
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="dd21a-102">Suplementos e extensibilidade</span><span class="sxs-lookup"><span data-stu-id="dd21a-102">Add-ins and Extensibility</span></span>
<a name="top"></a><span data-ttu-id="dd21a-103">Os suplementos fornecem recursos estendidos ou serviços para um aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="dd21a-104">O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece um modelo de programação que os desenvolvedores podem usar para desenvolver os complementos e ativá-los em seus aplicativos de host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="dd21a-105">O modelo realiza isso criando um pipeline de comunicação entre o host e o suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="dd21a-106">O modelo é implementado usando os tipos no <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, e <xref:System.AddIn.Contract> namespaces.</span><span class="sxs-lookup"><span data-stu-id="dd21a-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="dd21a-107">Esta visão geral contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="dd21a-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="dd21a-108">Modelo de suplemento</span><span class="sxs-lookup"><span data-stu-id="dd21a-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="dd21a-109">Fazer distinção entre Hosts e suplementos</span><span class="sxs-lookup"><span data-stu-id="dd21a-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="dd21a-110">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="dd21a-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="dd21a-111">Referência</span><span class="sxs-lookup"><span data-stu-id="dd21a-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="dd21a-112">Você pode encontrar exemplos adicionais de código e prévias de tecnologia de cliente de ferramentas para construção suplemento pipelines no [site gerenciado extensibilidade e suplemento do Framework no CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="dd21a-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="dd21a-113">Modelo de suplemento</span><span class="sxs-lookup"><span data-stu-id="dd21a-113">Add-in Model</span></span>  
 <span data-ttu-id="dd21a-114">O modelo de suplemento consiste em uma série de segmentos que compõem o pipeline de suplementos (também conhecido como o pipeline de comunicação), que é responsável por toda a comunicação entre o suplemento e o host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="dd21a-115">O pipeline é um modelo de comunicação simétrico de segmentos que trocar dados entre um suplemento e seu host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="dd21a-116">Desenvolver esses segmentos entre o host e o suplemento fornece isolamento do suplemento e as camadas necessárias de abstração que oferecem suporte a controle de versão.</span><span class="sxs-lookup"><span data-stu-id="dd21a-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="dd21a-117">A ilustração a seguir mostra o pipeline.</span><span class="sxs-lookup"><span data-stu-id="dd21a-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="dd21a-118">![Adicionar &#45; no modelo de pipeline. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="dd21a-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="dd21a-119">Pipeline de suplemento</span><span class="sxs-lookup"><span data-stu-id="dd21a-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="dd21a-120">Os assemblies para esses segmentos não são necessários para estar no mesmo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd21a-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="dd21a-121">Você pode carregar um suplemento em seu próprio domínio de aplicativo nova, em um domínio de aplicativo existente ou até mesmo para o domínio de aplicativo do host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="dd21a-122">Você pode carregar vários suplementos no mesmo domínio do aplicativo, que permite que os suplementos compartilhar recursos e contextos de segurança.</span><span class="sxs-lookup"><span data-stu-id="dd21a-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="dd21a-123">Modelo de suplemento dá suporte a e recomenda um limite opcional entre o host e o suplemento, que é chamado o limite de isolamento (também conhecido como um limite de comunicação remota).</span><span class="sxs-lookup"><span data-stu-id="dd21a-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="dd21a-124">Esse limite pode ser um limite de domínio ou de processo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd21a-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="dd21a-125">O segmento de contrato no meio do pipeline é carregado no domínio do aplicativo do host e domínio de aplicativo do suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="dd21a-126">O contrato define os métodos virtuais que o host e o uso de adicionar a troca de tipos entre si.</span><span class="sxs-lookup"><span data-stu-id="dd21a-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="dd21a-127">Para passar o limite de isolamento, os tipos devem ser contratos ou tipos serializáveis.</span><span class="sxs-lookup"><span data-stu-id="dd21a-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="dd21a-128">Tipos não contratos ou tipos serializáveis devem ser convertidos para contratos por segmentos de adaptador no pipeline.</span><span class="sxs-lookup"><span data-stu-id="dd21a-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="dd21a-129">Os segmentos de modo de exibição do pipeline são classes base abstratas ou interfaces que fornecem o host e o suplemento com uma exibição dos métodos que compartilham, conforme definido pelo contrato.</span><span class="sxs-lookup"><span data-stu-id="dd21a-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="dd21a-130">Para obter mais informações sobre o desenvolvimento de segmentos de pipeline, consulte [desenvolvimento de Pipeline](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="dd21a-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="dd21a-131">As seções a seguir descrevem os recursos do modelo de suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="dd21a-132">Controle de versão independente</span><span class="sxs-lookup"><span data-stu-id="dd21a-132">Independent Versioning</span></span>  
 <span data-ttu-id="dd21a-133">O modelo de suplemento permite que hosts e suplementos para versão independentemente.</span><span class="sxs-lookup"><span data-stu-id="dd21a-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="dd21a-134">Como resultado, o modelo de suplemento permite os seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="dd21a-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="dd21a-135">Criar um adaptador que permite que um host usar um suplemento criado para uma versão anterior do host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="dd21a-136">Criar um adaptador que permite que um host usar um suplemento criado para uma versão posterior do host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="dd21a-137">Criação de um adaptador que permite que um host usar os suplementos criados para um host diferente.</span><span class="sxs-lookup"><span data-stu-id="dd21a-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="dd21a-138">Detecção e ativação</span><span class="sxs-lookup"><span data-stu-id="dd21a-138">Discovery and Activation</span></span>  
 <span data-ttu-id="dd21a-139">Você pode ativar um suplemento usando um token de uma coleção que representa os suplementos encontrados em um armazenamento de informações.</span><span class="sxs-lookup"><span data-stu-id="dd21a-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="dd21a-140">Complementos são encontrados por meio de pesquisa para o tipo que define a exibição do host do suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="dd21a-141">Você também pode encontrar um add-in específico pelo tipo que define o suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="dd21a-142">O armazenamento de informações consiste em dois arquivos de cache: o repositório de pipeline e o repositório de suplementos.</span><span class="sxs-lookup"><span data-stu-id="dd21a-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="dd21a-143">Para obter informações sobre como atualizar e recompilar o armazenamento de informações, consulte [suplemento descoberta](http://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="dd21a-143">For information about updating and rebuilding the information store, see [Add-in Discovery](http://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="dd21a-144">Para obter informações sobre como ativar suplementos, consulte [suplemento ativação](http://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) e [como: ativar suplementos com segurança e isolamento diferentes](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="dd21a-144">For information about activating add-ins, see [Add-in Activation](http://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="dd21a-145">Níveis de isolamento e processos externos</span><span class="sxs-lookup"><span data-stu-id="dd21a-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="dd21a-146">O modelo dá suporte a vários níveis de isolamento entre um suplemento e seu host ou suplementos. A partir de menos isolado, esses níveis são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="dd21a-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="dd21a-147">O suplemento é executado no mesmo domínio do aplicativo como o host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="dd21a-148">Isso não é recomendado porque você perderá o isolamento e recursos de descarregamento que você obtém ao usar diferentes domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd21a-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="dd21a-149">Vários suplementos são carregados no mesmo domínio do aplicativo que é diferente do domínio de aplicativo usado pelo host.</span><span class="sxs-lookup"><span data-stu-id="dd21a-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="dd21a-150">Cada suplemento é carregado exclusivamente em seu próprio domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd21a-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="dd21a-151">Este é o nível mais comuns de isolamento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="dd21a-152">Vários suplementos são carregados no mesmo domínio do aplicativo em um processo externo.</span><span class="sxs-lookup"><span data-stu-id="dd21a-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="dd21a-153">Cada suplemento é carregado exclusivamente em seu próprio domínio de aplicativo em um processo externo.</span><span class="sxs-lookup"><span data-stu-id="dd21a-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="dd21a-154">Esse é o cenário mais isolado.</span><span class="sxs-lookup"><span data-stu-id="dd21a-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="dd21a-155">Para obter mais informações sobre o uso de processos externos, consulte [como: ativar suplementos com segurança e isolamento diferentes](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="dd21a-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="dd21a-156">Gerenciamento do tempo de vida</span><span class="sxs-lookup"><span data-stu-id="dd21a-156">Lifetime Management</span></span>  
 <span data-ttu-id="dd21a-157">Porque o modelo de suplemento ultrapassa os limites de domínio e o processo do aplicativo, a coleta de lixo por si só não é suficiente para liberar e recuperar os objetos.</span><span class="sxs-lookup"><span data-stu-id="dd21a-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="dd21a-158">O modelo fornece um mecanismo de gerenciamento do ciclo de vida que usa tokens e contagem de referência e geralmente não requer programação adicional.</span><span class="sxs-lookup"><span data-stu-id="dd21a-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="dd21a-159">Para obter mais informações, consulte [gerenciamento de vida útil](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="dd21a-159">For more information, see [Lifetime Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="dd21a-160">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="dd21a-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="dd21a-161">Fazer distinção entre Hosts e suplementos</span><span class="sxs-lookup"><span data-stu-id="dd21a-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="dd21a-162">A diferença entre um suplemento e um host é simplesmente que o host é o que ativa o suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="dd21a-163">O host pode ter mais de dois, como um aplicativo de processamento de texto e seu verificadores ortográficos; ou o host pode ser o menor dos dois, como um cliente de mensagens instantâneo que incorpora um reprodutor de mídia.</span><span class="sxs-lookup"><span data-stu-id="dd21a-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="dd21a-164">O modelo dá suporte a suplementos em cenários de cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="dd21a-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="dd21a-165">Exemplos de suplementos do servidor incluem suplementos que fornecem os servidores de email com a verificação de vírus, filtros de spam e proteção de IP.</span><span class="sxs-lookup"><span data-stu-id="dd21a-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="dd21a-166">Cliente suplemento exemplos suplementos de referência para processadores de texto, recursos especializados para programas gráficos e jogos e verificação de vírus de clientes de email local.</span><span class="sxs-lookup"><span data-stu-id="dd21a-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local email clients.</span></span>  
  
 [<span data-ttu-id="dd21a-167">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="dd21a-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="dd21a-168">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="dd21a-168">Related Topics</span></span>  
  
|<span data-ttu-id="dd21a-169">Título</span><span class="sxs-lookup"><span data-stu-id="dd21a-169">Title</span></span>|<span data-ttu-id="dd21a-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="dd21a-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dd21a-171">Desenvolvimento de pipeline</span><span class="sxs-lookup"><span data-stu-id="dd21a-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="dd21a-172">Descreve o canal de comunicação de segmentos do aplicativo host para o suplemento.</span><span class="sxs-lookup"><span data-stu-id="dd21a-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="dd21a-173">Fornece exemplos de código nos tópicos de instruções passo a passo que descrevem como construir o pipeline e como implantar segmentos para o pipeline em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd21a-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="dd21a-174">Domínios do aplicativo e assemblies</span><span class="sxs-lookup"><span data-stu-id="dd21a-174">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="dd21a-175">Descreve a relação entre os domínios de aplicativo, que fornecem um limite de isolamento de segurança, confiabilidade e controle de versão e assemblies.</span><span class="sxs-lookup"><span data-stu-id="dd21a-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="dd21a-176">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="dd21a-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="dd21a-177">Referência</span><span class="sxs-lookup"><span data-stu-id="dd21a-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="dd21a-178">Voltar ao início</span><span class="sxs-lookup"><span data-stu-id="dd21a-178">Back to top</span></span>](#top)