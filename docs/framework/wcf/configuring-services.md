---
title: Configurando serviços
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 7718edaefbad18afa11b3e3680fac39da585a610
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-services"></a><span data-ttu-id="b537d-102">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="b537d-102">Configuring Services</span></span>
<span data-ttu-id="b537d-103">Depois que você tiver criado e implementado o contrato de serviço, você está pronto para configurar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b537d-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="b537d-104">Isso é onde você pode definir e personalizar como o serviço é exposto aos clientes, incluindo a especificação do endereço onde ele pode ser encontrado, o transporte e a codificação de mensagens usa para enviar e receber mensagens e o tipo de segurança requer.</span><span class="sxs-lookup"><span data-stu-id="b537d-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="b537d-105">Configuração conforme usado aqui inclui todas as formas imperativa no código ou usando um arquivo de configuração, no qual você pode definir e personalizar os vários aspectos de um serviço, como especificando seus endereços de ponto de extremidade, os transportes usados e seus esquemas de segurança.</span><span class="sxs-lookup"><span data-stu-id="b537d-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="b537d-106">Na prática, a configuração de gravação é uma grande parte da programação de aplicativos do WCF.</span><span class="sxs-lookup"><span data-stu-id="b537d-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b537d-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b537d-107">In This Section</span></span>  
 [<span data-ttu-id="b537d-108">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="b537d-108">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 <span data-ttu-id="b537d-109">Começando com [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], o WCF é fornecido com um novo modelo de configuração padrão que simplifica a requisitos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="b537d-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="b537d-110">Se você não fornecer qualquer configuração do WCF para um serviço específico, o tempo de execução configura automaticamente o serviço com comportamentos, associações e pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="b537d-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="b537d-111">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b537d-111">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 <span data-ttu-id="b537d-112">Um serviço do Windows Communication Foundation (WCF) é configurável usando o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] tecnologia de configuração.</span><span class="sxs-lookup"><span data-stu-id="b537d-112">A Windows Communication Foundation (WCF) service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="b537d-113">Mais comumente, os elementos XML são adicionados ao arquivo Web. config para um site de serviços de informações da Internet (IIS) que hospeda um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="b537d-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="b537d-114">Os elementos permitem alterar detalhes, como os endereços de ponto de extremidade (os endereços reais usados para se comunicar com o serviço) em uma base por máquina.</span><span class="sxs-lookup"><span data-stu-id="b537d-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="b537d-115">Associações</span><span class="sxs-lookup"><span data-stu-id="b537d-115">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 <span data-ttu-id="b537d-116">Além disso, o WCF inclui várias configurações comuns fornecidos pelo sistema na forma de associações que permitem que você selecionar rapidamente os recursos mais básicos como um serviço e um cliente se comunicam, como os transportes, segurança e mensagem codificações usadas.</span><span class="sxs-lookup"><span data-stu-id="b537d-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="b537d-117">Pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="b537d-117">Endpoints</span></span>](../../../docs/framework/wcf/endpoints.md)  
 <span data-ttu-id="b537d-118">Toda a comunicação com um serviço WCF ocorre por meio de *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="b537d-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="b537d-119">Pontos de extremidade contêm o contrato, as informações de configuração que são especificadas nas associações e os endereços que indicam onde encontrar o serviço ou onde obter informações sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="b537d-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="b537d-120">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="b537d-120">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 <span data-ttu-id="b537d-121">Usando o WCF e existente mecanismos de segurança, você pode implementar a confidencialidade, integridade, autenticação e autorização em qualquer serviço.</span><span class="sxs-lookup"><span data-stu-id="b537d-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="b537d-122">Você também pode fazer auditoria de segurança êxitos e falhas.</span><span class="sxs-lookup"><span data-stu-id="b537d-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="b537d-123">Criando serviços interoperáveis de perfil básico do WS-I 1.1</span><span class="sxs-lookup"><span data-stu-id="b537d-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="b537d-124">Os requisitos para implantar um serviço que é interoperável com serviços e clientes em qualquer plataforma ou sistema operacional descritos em WS-I Basic Profile 1.1 especificação.</span><span class="sxs-lookup"><span data-stu-id="b537d-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b537d-125">Referência</span><span class="sxs-lookup"><span data-stu-id="b537d-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="b537d-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b537d-126">Related Sections</span></span>  
 [<span data-ttu-id="b537d-127">Ciclo de vida de programação básica</span><span class="sxs-lookup"><span data-stu-id="b537d-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="b537d-128">Serviços de design e implantação</span><span class="sxs-lookup"><span data-stu-id="b537d-128">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [<span data-ttu-id="b537d-129">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="b537d-129">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
  
 [<span data-ttu-id="b537d-130">Compilando clientes</span><span class="sxs-lookup"><span data-stu-id="b537d-130">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
  
 [<span data-ttu-id="b537d-131">Introdução à extensibilidade</span><span class="sxs-lookup"><span data-stu-id="b537d-131">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [<span data-ttu-id="b537d-132">Administração e diagnósticos</span><span class="sxs-lookup"><span data-stu-id="b537d-132">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="b537d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b537d-133">See Also</span></span>  
 [<span data-ttu-id="b537d-134">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="b537d-134">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="b537d-135">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="b537d-135">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="b537d-136">Detalhes de recursos do WCF</span><span class="sxs-lookup"><span data-stu-id="b537d-136">WCF Feature Details</span></span>](../../../docs/framework/wcf/feature-details/index.md)
