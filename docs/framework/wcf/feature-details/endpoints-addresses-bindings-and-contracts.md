---
title: "Pontos de extremidade: endereços, associações e contratos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c0b13ee48ed729d89f4b4b506e3608abe7e82b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="68691-102">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="68691-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="68691-103">Toda a comunicação com um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço ocorre por meio de *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="68691-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="68691-104">Pontos de extremidade de fornecem aos clientes acesso para a funcionalidade oferecida por um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="68691-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="68691-105">Cada ponto de extremidade consiste em quatro propriedades:</span><span class="sxs-lookup"><span data-stu-id="68691-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="68691-106">Um endereço que indica onde o ponto de extremidade pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="68691-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="68691-107">Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="68691-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="68691-108">Um contrato que identifica as operações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="68691-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="68691-109">Um conjunto de comportamentos que especifique os detalhes de implementação de local do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="68691-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="68691-110">Este tópico aborda essa estrutura de ponto de extremidade e explica como ele é representado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de objeto.</span><span class="sxs-lookup"><span data-stu-id="68691-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="68691-111">A estrutura de um ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="68691-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="68691-112">Cada ponto de extremidade consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="68691-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="68691-113">Endereço: O endereço identifica exclusivamente o ponto de extremidade e informa o potencial de consumidores do serviço onde ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="68691-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="68691-114">Ele é representado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de objeto, o <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="68691-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="68691-115">Um <xref:System.ServiceModel.EndpointAddress> classe contém:</span><span class="sxs-lookup"><span data-stu-id="68691-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="68691-116">Um <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade, que representa o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="68691-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="68691-117">Um <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade, que representa a identidade de segurança do serviço e uma coleção de cabeçalhos de mensagem opcional.</span><span class="sxs-lookup"><span data-stu-id="68691-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="68691-118">Os cabeçalhos de mensagem opcional são usados para fornecer mais e obter mais informações de endereçamento para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="68691-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="68691-119">[Especificando um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="68691-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="68691-120">Vinculação: A associação especifica como se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="68691-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="68691-121">Isso inclui:</span><span class="sxs-lookup"><span data-stu-id="68691-121">This includes:</span></span>  
  
    -   <span data-ttu-id="68691-122">O protocolo de transporte a ser usado (por exemplo, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="68691-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="68691-123">A codificação a ser usada para as mensagens (por exemplo, texto ou binário).</span><span class="sxs-lookup"><span data-stu-id="68691-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="68691-124">Os requisitos de segurança necessários (por exemplo, SSL ou SOAP segurança de mensagem).</span><span class="sxs-lookup"><span data-stu-id="68691-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="68691-125">[Visão geral de associações do WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="68691-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="68691-126">Uma associação é representada no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de objeto pela classe base abstrata <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="68691-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="68691-127">Na maioria dos cenários, os usuários podem usar uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="68691-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="68691-128">Para obter mais informações, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="68691-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="68691-129">Contratos: O contrato descreve qual funcionalidade expõe o ponto de extremidade para o cliente.</span><span class="sxs-lookup"><span data-stu-id="68691-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="68691-130">Especifica um contrato:</span><span class="sxs-lookup"><span data-stu-id="68691-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="68691-131">As operações que podem ser chamadas por um cliente.</span><span class="sxs-lookup"><span data-stu-id="68691-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="68691-132">O formato da mensagem.</span><span class="sxs-lookup"><span data-stu-id="68691-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="68691-133">O tipo de dados necessários para chamar a operação ou parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="68691-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="68691-134">Que tipo de mensagem de resposta ou processamento em que o cliente pode esperar.</span><span class="sxs-lookup"><span data-stu-id="68691-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="68691-135">Para obter mais informações sobre como definir um contrato, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="68691-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="68691-136">Comportamentos: Você pode usar os comportamentos de ponto de extremidade para personalizar o comportamento local do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="68691-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="68691-137">Comportamentos de ponto de extremidade alcançar isso participando no processo de criação um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="68691-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="68691-138">Um exemplo de um comportamento de ponto de extremidade é o <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> propriedade, que permite que você especifique um endereço de escutando diferente que o endereço SOAP ou WSDL Web Services Description Language ().</span><span class="sxs-lookup"><span data-stu-id="68691-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="68691-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="68691-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="68691-140">Definir pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="68691-140">Defining Endpoints</span></span>  
 <span data-ttu-id="68691-141">Você pode especificar o ponto de extremidade para um serviço usando código imperativa ou declarativamente por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="68691-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="68691-142">[Como: criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) e [como: criar um ponto de extremidade de serviço em código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="68691-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68691-143">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="68691-143">In This Section</span></span>  
 <span data-ttu-id="68691-144">Esta seção explica a finalidade de associações, pontos de extremidade e endereços; mostra como configurar uma associação e um ponto de extremidade; e demonstra como usar o `ClientVia` comportamento e `ListenUri` propriedade.</span><span class="sxs-lookup"><span data-stu-id="68691-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="68691-145">Endereços</span><span class="sxs-lookup"><span data-stu-id="68691-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="68691-146">Descreve como os pontos de extremidade são resolvidos em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68691-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="68691-147">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="68691-147">[Bindings](../../../../docs/framework/wcf/feature-details/bindings.md)</span></span>  
 <span data-ttu-id="68691-148">Descreve como as associações são usadas para especificar o transporte, a codificação e detalhes de protocolo necessárias para clientes e serviços para se comunicar entre si.</span><span class="sxs-lookup"><span data-stu-id="68691-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="68691-149">Contratos</span><span class="sxs-lookup"><span data-stu-id="68691-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="68691-150">Descreve como os contratos definem os métodos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="68691-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="68691-151">Como: criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="68691-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="68691-152">Descreve como criar um ponto de extremidade de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="68691-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="68691-153">Como: criar um ponto de extremidade de serviço em código</span><span class="sxs-lookup"><span data-stu-id="68691-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="68691-154">Descreve como criar um ponto de extremidade de serviço em código.</span><span class="sxs-lookup"><span data-stu-id="68691-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="68691-155">Como: usar o Svcutil.exe para validar o código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="68691-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="68691-156">Descreve como detectar erros nas configurações e implementações de serviço sem hospedar o serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="68691-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68691-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68691-157">See Also</span></span>  
 <span data-ttu-id="68691-158">[Configuring Services](../../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)</span><span class="sxs-lookup"><span data-stu-id="68691-158">[Configuring Services](../../../../docs/framework/wcf/configuring-services.md)</span></span>  
 [<span data-ttu-id="68691-159">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="68691-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
