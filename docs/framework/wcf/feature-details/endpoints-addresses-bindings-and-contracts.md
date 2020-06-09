---
title: 'Pontos de extremidade: endereços, associações e contratos'
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
ms.openlocfilehash: 3ac7f0b165b99a1ed3702628958f7d4c7702f5b1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593510"
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="135e1-102">Pontos de extremidade: endereços, associações e contratos</span><span class="sxs-lookup"><span data-stu-id="135e1-102">Endpoints: Addresses, Bindings, and Contracts</span></span>

<span data-ttu-id="135e1-103">Toda a comunicação com um serviço Windows Communication Foundation (WCF) ocorre por meio dos *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="135e1-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="135e1-104">Os pontos de extremidade fornecem aos clientes acesso à funcionalidade oferecida por um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="135e1-104">Endpoints provide clients access to the functionality offered by a WCF service.</span></span>

<span data-ttu-id="135e1-105">Cada ponto de extremidade consiste em quatro propriedades:</span><span class="sxs-lookup"><span data-stu-id="135e1-105">Each endpoint consists of four properties:</span></span>

- <span data-ttu-id="135e1-106">Um endereço que indica onde o ponto de extremidade pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="135e1-106">An address that indicates where the endpoint can be found.</span></span>

- <span data-ttu-id="135e1-107">Uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="135e1-107">A binding that specifies how a client can communicate with the endpoint.</span></span>

- <span data-ttu-id="135e1-108">Um contrato que identifica as operações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="135e1-108">A contract that identifies the operations available.</span></span>

- <span data-ttu-id="135e1-109">Um conjunto de comportamentos que especificam detalhes de implementação local do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="135e1-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>

<span data-ttu-id="135e1-110">Este tópico aborda essa estrutura de ponto de extremidade e explica como ela é representada no modelo de objeto do WCF.</span><span class="sxs-lookup"><span data-stu-id="135e1-110">This topic discusses this endpoint structure and explains how it is represented in the WCF object model.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="135e1-111">A estrutura de um ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="135e1-111">The Structure of an Endpoint</span></span>

<span data-ttu-id="135e1-112">Cada ponto de extremidade consiste no seguinte:</span><span class="sxs-lookup"><span data-stu-id="135e1-112">Each endpoint consists of the following:</span></span>

- <span data-ttu-id="135e1-113">Endereço: o endereço identifica exclusivamente o ponto de extremidade e informa aos possíveis consumidores do serviço onde ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="135e1-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="135e1-114">Ele é representado no modelo de objeto do WCF pela <xref:System.ServiceModel.EndpointAddress> classe.</span><span class="sxs-lookup"><span data-stu-id="135e1-114">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="135e1-115">Uma <xref:System.ServiceModel.EndpointAddress> classe contém:</span><span class="sxs-lookup"><span data-stu-id="135e1-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>

  - <span data-ttu-id="135e1-116">Uma <xref:System.ServiceModel.EndpointAddress.Uri%2A> propriedade, que representa o endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="135e1-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>

  - <span data-ttu-id="135e1-117">Uma <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriedade, que representa a identidade de segurança do serviço e uma coleção de cabeçalhos de mensagens opcionais.</span><span class="sxs-lookup"><span data-stu-id="135e1-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="135e1-118">Os cabeçalhos de mensagem opcionais são usados para fornecer informações de endereçamento adicionais e mais detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="135e1-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>

  <span data-ttu-id="135e1-119">Para obter mais informações, consulte [especificando um endereço de ponto de extremidade](../specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-119">For more information, see [Specifying an Endpoint Address](../specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="135e1-120">Binding: a Binding especifica como se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="135e1-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="135e1-121">Isso inclui:</span><span class="sxs-lookup"><span data-stu-id="135e1-121">This includes:</span></span>

  - <span data-ttu-id="135e1-122">O protocolo de transporte a ser usado (por exemplo, TCP ou HTTP).</span><span class="sxs-lookup"><span data-stu-id="135e1-122">The transport protocol to use (for example, TCP or HTTP).</span></span>

  - <span data-ttu-id="135e1-123">A codificação a ser usada para as mensagens (por exemplo, texto ou binário).</span><span class="sxs-lookup"><span data-stu-id="135e1-123">The encoding to use for the messages (for example, text or binary).</span></span>

  - <span data-ttu-id="135e1-124">Os requisitos de segurança necessários (por exemplo, segurança de mensagem SSL ou SOAP).</span><span class="sxs-lookup"><span data-stu-id="135e1-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>

  <span data-ttu-id="135e1-125">Para obter mais informações, consulte [visão geral das associações do WCF](../bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-125">For more information, see [WCF Bindings Overview](../bindings-overview.md).</span></span> <span data-ttu-id="135e1-126">Uma associação é representada no modelo de objeto do WCF pela classe base abstrata <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="135e1-126">A binding is represented in the WCF object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="135e1-127">Para a maioria dos cenários, os usuários podem usar uma das associações fornecidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="135e1-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="135e1-128">Para obter mais informações, consulte [associações fornecidas pelo sistema](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-128">For more information, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

- <span data-ttu-id="135e1-129">Contratos: o contrato descreve qual funcionalidade o ponto de extremidade expõe para o cliente.</span><span class="sxs-lookup"><span data-stu-id="135e1-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="135e1-130">Um contrato especifica:</span><span class="sxs-lookup"><span data-stu-id="135e1-130">A contract specifies:</span></span>

  - <span data-ttu-id="135e1-131">Quais operações podem ser chamadas por um cliente.</span><span class="sxs-lookup"><span data-stu-id="135e1-131">What operations can be called by a client.</span></span>

  - <span data-ttu-id="135e1-132">A forma da mensagem.</span><span class="sxs-lookup"><span data-stu-id="135e1-132">The form of the message.</span></span>

  - <span data-ttu-id="135e1-133">O tipo de parâmetros de entrada ou dados necessários para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="135e1-133">The type of input parameters or data required to call the operation.</span></span>

  - <span data-ttu-id="135e1-134">Que tipo de mensagem de processamento ou resposta o cliente pode esperar.</span><span class="sxs-lookup"><span data-stu-id="135e1-134">What type of processing or response message the client can expect.</span></span>

  <span data-ttu-id="135e1-135">Para obter mais informações sobre como definir um contrato, consulte [projetando contratos de serviço](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-135">For more information about defining a contract, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>

- <span data-ttu-id="135e1-136">Comportamentos: você pode usar comportamentos de ponto de extremidade para personalizar o comportamento local do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="135e1-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="135e1-137">Os comportamentos de ponto de extremidade obtêm isso participando do processo de criação de um tempo de execução do WCF.</span><span class="sxs-lookup"><span data-stu-id="135e1-137">Endpoint behaviors achieve this by participating in the process of building a WCF runtime.</span></span> <span data-ttu-id="135e1-138">Um exemplo de um comportamento de ponto de extremidade é a <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> propriedade, que permite especificar um endereço de escuta diferente do SOAP ou do endereço WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="135e1-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> <span data-ttu-id="135e1-139">Para obter mais informações, consulte [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-139">For more information, see [ClientViaBehavior](../diagnostics/wmi/clientviabehavior.md).</span></span>

## <a name="defining-endpoints"></a><span data-ttu-id="135e1-140">Definindo pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="135e1-140">Defining Endpoints</span></span>

<span data-ttu-id="135e1-141">Você pode especificar o ponto de extremidade para um serviço de forma imperativa usando código ou declarativamente por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="135e1-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="135e1-142">Para obter mais informações, consulte [como: criar um ponto de extremidade de serviço em configuração](how-to-create-a-service-endpoint-in-configuration.md) e [como criar um ponto de extremidade de serviço no código](how-to-create-a-service-endpoint-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-142">For more information, see [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="135e1-143">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="135e1-143">In This Section</span></span>

<span data-ttu-id="135e1-144">Esta seção explica a finalidade de associações, pontos de extremidade e endereços; mostra como configurar uma associação e um ponto de extremidade; e demonstra como usar o `ClientVia` comportamento e a `ListenUri` propriedade.</span><span class="sxs-lookup"><span data-stu-id="135e1-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>

<span data-ttu-id="135e1-145">[Atende](endpoint-addresses.md)</span><span class="sxs-lookup"><span data-stu-id="135e1-145">[Addresses](endpoint-addresses.md)</span></span>\
<span data-ttu-id="135e1-146">Descreve como os pontos de extremidade são endereçados no WCF.</span><span class="sxs-lookup"><span data-stu-id="135e1-146">Describes how endpoints are addressed in WCF.</span></span>

<span data-ttu-id="135e1-147">[Associações](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="135e1-147">[Bindings](bindings.md)</span></span>\
<span data-ttu-id="135e1-148">Descreve como as associações são usadas para especificar os detalhes de transporte, codificação e protocolo necessários para que os clientes e serviços se comuniquem entre si.</span><span class="sxs-lookup"><span data-stu-id="135e1-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>

<span data-ttu-id="135e1-149">[Contratos](contracts.md)</span><span class="sxs-lookup"><span data-stu-id="135e1-149">[Contracts](contracts.md)</span></span>\
<span data-ttu-id="135e1-150">Descreve como os contratos definem os métodos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="135e1-150">Describes how contracts define the methods of a service.</span></span>

<span data-ttu-id="135e1-151">[Como criar um ponto de extremidade de serviço na configuração](how-to-create-a-service-endpoint-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="135e1-151">[How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md)</span></span>\
<span data-ttu-id="135e1-152">Descreve como criar um ponto de extremidade de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="135e1-152">Describes how to create a service endpoint in configuration.</span></span>

<span data-ttu-id="135e1-153">[Como criar um ponto de extremidade de serviço no código](how-to-create-a-service-endpoint-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="135e1-153">[How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md)</span></span>\
<span data-ttu-id="135e1-154">Descreve como criar um ponto de extremidade de serviço no código.</span><span class="sxs-lookup"><span data-stu-id="135e1-154">Describes how to create a service endpoint in code.</span></span>

<span data-ttu-id="135e1-155">[Como: usar svcutil. exe para validar o código de serviço compilado](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span><span class="sxs-lookup"><span data-stu-id="135e1-155">[How to: Use Svcutil.exe to Validate Compiled Service Code](how-to-use-svcutil-exe-to-validate-compiled-service-code.md)</span></span>\
<span data-ttu-id="135e1-156">Descreve como detectar erros em implementações de serviço e configurações sem hospedar o serviço usando a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="135e1-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="135e1-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="135e1-157">See also</span></span>

- [<span data-ttu-id="135e1-158">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="135e1-158">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="135e1-159">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="135e1-159">Extending Bindings</span></span>](../extending/extending-bindings.md)
