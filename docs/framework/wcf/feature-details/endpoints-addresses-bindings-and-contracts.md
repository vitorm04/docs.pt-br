---
title: 'Pontos de extremidade: endereços, associações e contratos'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3e78e7cf0c5acde53d7ee23294fd52134414e860
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856527"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="59bcc-102">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="59bcc-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="59bcc-103">Toda a comunicação com um serviço do Windows Communication Foundation (WCF) ocorre por meio de *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="59bcc-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="59bcc-104">Pontos de extremidade de fornecem aos clientes acesso à funcionalidade oferecida por um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="59bcc-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>  
  
 <span data-ttu-id="59bcc-105">Cada ponto de extremidade consiste em quatro propriedades:</span><span class="sxs-lookup"><span data-stu-id="59bcc-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="59bcc-106">Um endereço que indica onde o ponto de extremidade pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="59bcc-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="59bcc-107">Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="59bcc-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="59bcc-108">Um contrato que identifica as operações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="59bcc-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="59bcc-109">Um conjunto de comportamentos que especifique os detalhes de implementação local do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="59bcc-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="59bcc-110">Este tópico discute a estrutura de ponto de extremidade e explica como ele é representado no modelo de objeto do WCF.</span><span class="sxs-lookup"><span data-stu-id="59bcc-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="59bcc-111">A estrutura de um ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="59bcc-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="59bcc-112">Cada ponto de extremidade consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="59bcc-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="59bcc-113">Endereço: O endereço identifica o ponto de extremidade exclusivamente e informa o potencial de consumidores do serviço em que ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="59bcc-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="59bcc-114">Ele é representado no modelo de objeto WCF pelo <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="59bcc-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="59bcc-115">Um <xref:System.ServiceModel.EndpointAddress> classe contém:</span><span class="sxs-lookup"><span data-stu-id="59bcc-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="59bcc-116">Um <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade, que representa o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="59bcc-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="59bcc-117">Um <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade, que representa a identidade de segurança do serviço e uma coleção de cabeçalhos de mensagem opcional.</span><span class="sxs-lookup"><span data-stu-id="59bcc-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="59bcc-118">Os cabeçalhos de mensagem opcional são usados para fornecer mais e obter informações de endereçamento para identificar ou interagir com o ponto de extremidade mais detalhadas.</span><span class="sxs-lookup"><span data-stu-id="59bcc-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     <span data-ttu-id="59bcc-119">Para obter mais informações, consulte [especificação de um endereço de ponto de extremidade](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-119">For more information, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="59bcc-120">Associação: A associação especifica como se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="59bcc-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="59bcc-121">Isso inclui:</span><span class="sxs-lookup"><span data-stu-id="59bcc-121">This includes:</span></span>  
  
    -   <span data-ttu-id="59bcc-122">O protocolo de transporte a ser usado (por exemplo, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="59bcc-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="59bcc-123">A codificação a ser usada para as mensagens (por exemplo, texto ou binário).</span><span class="sxs-lookup"><span data-stu-id="59bcc-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="59bcc-124">Os requisitos de segurança necessárias (por exemplo, SSL ou SOAP segurança de mensagem).</span><span class="sxs-lookup"><span data-stu-id="59bcc-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     <span data-ttu-id="59bcc-125">Para obter mais informações, consulte [visão geral de associações do WCF](../../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-125">For more information, see [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="59bcc-126">Uma associação é representada no modelo de objeto WCF pela classe base abstrata <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="59bcc-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="59bcc-127">Na maioria dos cenários, os usuários podem usar uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="59bcc-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="59bcc-128">Para obter mais informações, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="59bcc-129">Contratos: O contrato descreve qual funcionalidade que o ponto de extremidade expõe para o cliente.</span><span class="sxs-lookup"><span data-stu-id="59bcc-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="59bcc-130">Especifica um contrato:</span><span class="sxs-lookup"><span data-stu-id="59bcc-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="59bcc-131">As operações que podem ser chamadas por um cliente.</span><span class="sxs-lookup"><span data-stu-id="59bcc-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="59bcc-132">O formato da mensagem.</span><span class="sxs-lookup"><span data-stu-id="59bcc-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="59bcc-133">O tipo de parâmetros de entrada ou os dados necessários para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="59bcc-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="59bcc-134">Que tipo de mensagem de resposta ou processamento, o cliente pode esperar.</span><span class="sxs-lookup"><span data-stu-id="59bcc-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="59bcc-135">Para obter mais informações sobre como definir um contrato, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="59bcc-136">Comportamentos: Você pode usar comportamentos de ponto de extremidade para personalizar o comportamento local do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="59bcc-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="59bcc-137">Comportamentos de ponto de extremidade feito participantes no processo de criação de um WCFruntime.</span><span class="sxs-lookup"><span data-stu-id="59bcc-137">Endpoint behaviors achieve this by participating in the process of building a WCFruntime.</span></span> <span data-ttu-id="59bcc-138">Um exemplo de um comportamento de ponto de extremidade é o <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> propriedade, que permite que você especifique um endereço de escutando diferente que o endereço SOAP ou a descrição de linguagem WSDL (Web Services).</span><span class="sxs-lookup"><span data-stu-id="59bcc-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="59bcc-139">Para obter mais informações, consulte [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-139">For more information, see [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="59bcc-140">Definir pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="59bcc-140">Defining Endpoints</span></span>  
 <span data-ttu-id="59bcc-141">Você pode especificar o ponto de extremidade para um serviço usando código imperativa, ou declarativamente por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="59bcc-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="59bcc-142">Para obter mais informações, confira [Como: Criar um ponto de extremidade de serviço na configuração](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) e [como: Criar um ponto de extremidade de serviço no código](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-142">For more information, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59bcc-143">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="59bcc-143">In This Section</span></span>  
 <span data-ttu-id="59bcc-144">Esta seção explica a finalidade de associações, os pontos de extremidade e endereços; mostra como configurar uma associação e um ponto de extremidade; e demonstra como usar o `ClientVia` comportamento e `ListenUri` propriedade.</span><span class="sxs-lookup"><span data-stu-id="59bcc-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="59bcc-145">Endereços</span><span class="sxs-lookup"><span data-stu-id="59bcc-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="59bcc-146">Descreve como os pontos de extremidade são endereçados no WCF.</span><span class="sxs-lookup"><span data-stu-id="59bcc-146">Describes how endpoints are addressed in WCF.</span></span>  
  
 [<span data-ttu-id="59bcc-147">Associações</span><span class="sxs-lookup"><span data-stu-id="59bcc-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="59bcc-148">Descreve como vinculações são usadas para especificar o transporte, codificação e detalhes do protocolo necessárias para clientes e serviços para se comunicar entre si.</span><span class="sxs-lookup"><span data-stu-id="59bcc-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="59bcc-149">Contratos</span><span class="sxs-lookup"><span data-stu-id="59bcc-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="59bcc-150">Descreve como os contratos definem os métodos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="59bcc-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="59bcc-151">Como: Criar um ponto de extremidade de serviço na configuração</span><span class="sxs-lookup"><span data-stu-id="59bcc-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="59bcc-152">Descreve como criar um ponto de extremidade de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="59bcc-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="59bcc-153">Como: Criar um ponto de extremidade de serviço no código</span><span class="sxs-lookup"><span data-stu-id="59bcc-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="59bcc-154">Descreve como criar um ponto de extremidade de serviço no código.</span><span class="sxs-lookup"><span data-stu-id="59bcc-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="59bcc-155">Como: Use Svcutil.exe para validar o código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="59bcc-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="59bcc-156">Descreve como detectar erros em implementações de serviço e as configurações sem hospedar o serviço usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="59bcc-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59bcc-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59bcc-157">See also</span></span>

- [<span data-ttu-id="59bcc-158">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="59bcc-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="59bcc-159">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="59bcc-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
