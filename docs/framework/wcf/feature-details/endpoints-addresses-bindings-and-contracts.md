---
title: 'Pontos de extremidade: endereços, associações e contratos'
description: Saiba como toda a comunicação com um serviço WCF ocorre por meio dos pontos de extremidade de serviço, que fornecem aos clientes acesso à funcionalidade oferecida pelo serviço.
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: ce0874bfed716716b6fd1801b35a4266095cd752
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247306"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="ad1e8-103">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="ad1e8-103">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="ad1e8-104">Toda a comunicação com um serviço Windows Communication Foundation (WCF) ocorre por meio dos *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-104">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="ad1e8-105">Os pontos de extremidade fornecem aos clientes acesso à funcionalidade oferecida por um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-105">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="ad1e8-106">Cada ponto de extremidade consiste em quatro propriedades:</span><span class="sxs-lookup"><span data-stu-id="ad1e8-106">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="ad1e8-107">Um endereço que indica onde o ponto de extremidade pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-107">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="ad1e8-108">Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-108">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="ad1e8-109">Um contrato que identifica as operações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-109">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="ad1e8-110">Um conjunto de comportamentos que especificam detalhes de implementação local do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-110">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="ad1e8-111">Este tópico aborda essa estrutura de ponto de extremidade e explica como ela é representada no modelo de objeto do WCF.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-111">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="ad1e8-112">A estrutura de um ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="ad1e8-112">The Structure of an Endpoint</span></span>

<span data-ttu-id="ad1e8-113">Cada ponto de extremidade consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="ad1e8-113">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="ad1e8-114">Endereço: o endereço identifica exclusivamente o ponto de extremidade e informa aos possíveis consumidores do serviço onde ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-114">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="ad1e8-115">Ele é representado no modelo de objeto do WCF pela <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-115">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="ad1e8-116">Uma <xref:System.ServiceModel.EndpointAddress> classe contém:</span><span class="sxs-lookup"><span data-stu-id="ad1e8-116">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="ad1e8-117">Uma <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade, que representa o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-117">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="ad1e8-118">Uma <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade, que representa a identidade de segurança do serviço e uma coleção de cabeçalhos de mensagens opcionais.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-118">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="ad1e8-119">Os cabeçalhos de mensagem opcionais são usados para fornecer informações de endereçamento adicionais e mais detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-119">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="ad1e8-120">Para obter mais informações, consulte [especificando um endereço de ponto de extremidade](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-120">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="ad1e8-121">Binding: a Binding especifica como se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-121">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="ad1e8-122">Isso inclui:</span><span class="sxs-lookup"><span data-stu-id="ad1e8-122">This includes:</span></span>

  - <span data-ttu-id="ad1e8-123">O protocolo de transporte a ser usado (por exemplo, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-123">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="ad1e8-124">A codificação a ser usada para as mensagens (por exemplo, texto ou binário).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-124">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="ad1e8-125">Os requisitos de segurança necessários (por exemplo, segurança de mensagem SSL ou SOAP).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-125">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="ad1e8-126">Para obter mais informações, consulte [visão geral das associações do WCF](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-126">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="ad1e8-127">Uma associação é representada no modelo de objeto do WCF pela classe base abstrata <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="ad1e8-127">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="ad1e8-128">Para a maioria dos cenários, os usuários podem usar uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-128">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="ad1e8-129">Para obter mais informações, consulte [associações fornecidas pelo sistema](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-129">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="ad1e8-130">Contratos: o contrato descreve qual funcionalidade o ponto de extremidade expõe para o cliente.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-130">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="ad1e8-131">Um contrato especifica:</span><span class="sxs-lookup"><span data-stu-id="ad1e8-131">A contract specifies:</span></span>

  - <span data-ttu-id="ad1e8-132">Quais operações podem ser chamadas por um cliente.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-132">What operations can be called by a client.</span></span>

  - <span data-ttu-id="ad1e8-133">A forma da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-133">The form of the message.</span></span>

  - <span data-ttu-id="ad1e8-134">O tipo de parâmetros de entrada ou dados necessários para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-134">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="ad1e8-135">Que tipo de mensagem de processamento ou resposta o cliente pode esperar.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-135">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="ad1e8-136">Para obter mais informações sobre como definir um contrato, consulte [projetando contratos de serviço](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-136">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="ad1e8-137">Comportamentos: você pode usar comportamentos de ponto de extremidade para personalizar o comportamento local do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-137">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="ad1e8-138">Os comportamentos de ponto de extremidade obtêm isso participando do processo de criação de um tempo de execução do WCF.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-138">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="ad1e8-139">Um exemplo de um comportamento de ponto de extremidade é a <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> propriedade, que permite especificar um endereço de escuta diferente do SOAP ou do endereço WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-139">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="ad1e8-140">Para obter mais informações, consulte [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-140">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="ad1e8-141">Definindo pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="ad1e8-141">Defining Endpoints</span></span>

<span data-ttu-id="ad1e8-142">Você pode especificar o ponto de extremidade para um serviço de forma imperativa usando código ou declarativamente por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-142">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="ad1e8-143">Para obter mais informações, consulte [como: criar um ponto de extremidade de serviço em configuração](how-to-create-a-service-endpoint-in-configuration.md) e [como criar um ponto de extremidade de serviço no código](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-143">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ad1e8-144">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ad1e8-144">In This Section</span></span>

<span data-ttu-id="ad1e8-145">Esta seção explica a finalidade de associações, pontos de extremidade e endereços; mostra como configurar uma associação e um ponto de extremidade; e demonstra como usar o `ClientVia` comportamento e a `ListenUri` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-145">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="ad1e8-146">[Atende](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="ad1e8-146">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="ad1e8-147">Descreve como os pontos de extremidade são endereçados no WCF.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-147">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="ad1e8-148">[Associações](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ad1e8-148">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="ad1e8-149">Descreve como as associações são usadas para especificar os detalhes de transporte, codificação e protocolo necessários para que os clientes e serviços se comuniquem entre si.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-149">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="ad1e8-150">[Contratos](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="ad1e8-150">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="ad1e8-151">Descreve como os contratos definem os métodos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-151">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="ad1e8-152">[Como criar um ponto de extremidade de serviço na configuração](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="ad1e8-152">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="ad1e8-153">Descreve como criar um ponto de extremidade de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-153">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="ad1e8-154">[Como criar um ponto de extremidade de serviço no código](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="ad1e8-154">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="ad1e8-155">Descreve como criar um ponto de extremidade de serviço no código.</span><span class="sxs-lookup"><span data-stu-id="ad1e8-155">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="ad1e8-156">[Como: usar Svcutil.exe para validar o código de serviço compilado](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="ad1e8-156">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="ad1e8-157">Descreve como detectar erros em implementações de serviço e configurações sem hospedar o serviço usando a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ad1e8-157">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad1e8-158">Veja também</span><span class="sxs-lookup"><span data-stu-id="ad1e8-158">See also</span></span>

- [<span data-ttu-id="ad1e8-159">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="ad1e8-159">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="ad1e8-160">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ad1e8-160">Extending Bindings</span></span>](../extending/extending-bindings.md)
