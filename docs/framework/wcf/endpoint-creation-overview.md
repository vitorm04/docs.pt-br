---
title: Visão geral de criação de ponto de extremidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 0b0c22737e9407ebe2cb56c15fb7ff75d16b50a4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040303"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="fc285-102">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="fc285-102">Endpoint Creation Overview</span></span>

<span data-ttu-id="fc285-103">Toda a comunicação com um serviço Windows Communication Foundation (WCF) ocorre por meio dos *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="fc285-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="fc285-104">Os pontos de extremidade fornecem aos clientes acesso à funcionalidade oferecida por um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="fc285-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="fc285-105">Esta seção descreve a estrutura de um ponto de extremidade e destaca como definir um ponto de extremidade na configuração e no código.</span><span class="sxs-lookup"><span data-stu-id="fc285-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>

## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="fc285-106">A estrutura de um ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="fc285-106">The Structure of an Endpoint</span></span>

<span data-ttu-id="fc285-107">Cada ponto de extremidade contém um endereço que indica onde encontrar o ponto de extremidade, uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade e um contrato que identifica os métodos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fc285-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>

- <span data-ttu-id="fc285-108">**Endereço**.</span><span class="sxs-lookup"><span data-stu-id="fc285-108">**Address**.</span></span> <span data-ttu-id="fc285-109">O endereço identifica exclusivamente o ponto de extremidade e informa aos possíveis consumidores onde o serviço está localizado.</span><span class="sxs-lookup"><span data-stu-id="fc285-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="fc285-110">Ele é representado no modelo de objeto do WCF pelo <xref:System.ServiceModel.EndpointAddress> endereço, que contém um URI (Uniform Resource Identifier) e propriedades de endereço que incluem uma identidade, alguns elementos WSDL (Web Services Description Language) e uma coleção de opcional conector.</span><span class="sxs-lookup"><span data-stu-id="fc285-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="fc285-111">Os cabeçalhos opcionais fornecem informações adicionais de endereçamento detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fc285-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="fc285-112">Para obter mais informações, consulte [especificando um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>

- <span data-ttu-id="fc285-113">**Associação**.</span><span class="sxs-lookup"><span data-stu-id="fc285-113">**Binding**.</span></span> <span data-ttu-id="fc285-114">A associação especifica como se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fc285-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="fc285-115">A associação especifica como o ponto de extremidade se comunica com o mundo, incluindo qual protocolo de transporte deve ser usado (por exemplo, TCP ou HTTP), que codificação usar para as mensagens (por exemplo, texto ou binário) e quais requisitos de segurança são necessários (para exemplo, protocolo SSL [SSL] ou segurança de mensagem SOAP).</span><span class="sxs-lookup"><span data-stu-id="fc285-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="fc285-116">Para obter mais informações, consulte [usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>

- <span data-ttu-id="fc285-117">**Contrato de serviço**.</span><span class="sxs-lookup"><span data-stu-id="fc285-117">**Service contract**.</span></span> <span data-ttu-id="fc285-118">O contrato de serviço descreve qual funcionalidade o ponto de extremidade expõe para o cliente.</span><span class="sxs-lookup"><span data-stu-id="fc285-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="fc285-119">Um contrato especifica as operações que um cliente pode chamar, a forma da mensagem e o tipo de parâmetros de entrada ou dados necessários para chamar a operação e o tipo de mensagem de processamento ou resposta que o cliente pode esperar.</span><span class="sxs-lookup"><span data-stu-id="fc285-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="fc285-120">Três tipos básicos de contratos correspondem aos padrões de troca de mensagens básicos (MEPs): datagrama (unidirecional), solicitação/resposta e duplex (bidirecional).</span><span class="sxs-lookup"><span data-stu-id="fc285-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="fc285-121">O contrato de serviço também pode empregar dados e contratos de mensagem para exigir tipos de dados e formatos de mensagem específicos ao serem acessados.</span><span class="sxs-lookup"><span data-stu-id="fc285-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="fc285-122">Para obter mais informações sobre como definir um contrato de serviço, consulte [projetando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="fc285-123">Observe que um cliente também pode ser solicitado a implementar um contrato definido pelo serviço, chamado de contrato de retorno de chamada, para receber mensagens do serviço em um MEP duplex.</span><span class="sxs-lookup"><span data-stu-id="fc285-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="fc285-124">Para obter mais informações, consulte [duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>

<span data-ttu-id="fc285-125">O ponto de extremidade de um serviço pode ser especificado de forma imperativa usando código ou declarativamente por meio de configuração.</span><span class="sxs-lookup"><span data-stu-id="fc285-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="fc285-126">Se nenhum ponto de extremidade for especificado, o tempo de execução fornecerá pontos de extremidade padrão adicionando um ponto de extremidades padrão para cada endereço base para cada contrato de serviço implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="fc285-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="fc285-127">A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="fc285-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="fc285-128">Em geral, é mais prático definir pontos de extremidade de serviço usando a configuração em vez de código.</span><span class="sxs-lookup"><span data-stu-id="fc285-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="fc285-129">Manter a ligação e as informações de endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar e reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc285-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>

> [!NOTE]
> <span data-ttu-id="fc285-130">Ao adicionar um ponto de extremidade de serviço que executa a representação, você deve usar <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> um dos métodos <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> ou o método para carregar corretamente o contrato em <xref:System.ServiceModel.Description.ServiceDescription> um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="fc285-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>

## <a name="defining-endpoints-in-code"></a><span data-ttu-id="fc285-131">Definindo pontos de extremidade no código</span><span class="sxs-lookup"><span data-stu-id="fc285-131">Defining Endpoints in Code</span></span>

<span data-ttu-id="fc285-132">O exemplo a seguir ilustra como especificar um ponto de extremidade no código com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fc285-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>

- <span data-ttu-id="fc285-133">Defina um contrato para um `IEcho` tipo de serviço que aceite o nome de uma pessoa e o eco com a \<resposta "Olá, >!".</span><span class="sxs-lookup"><span data-stu-id="fc285-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>

- <span data-ttu-id="fc285-134">Implemente `Echo` um serviço do tipo definido `IEcho` pelo contrato.</span><span class="sxs-lookup"><span data-stu-id="fc285-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>

- <span data-ttu-id="fc285-135">Especifique um endereço de ponto `http://localhost:8000/Echo` de extremidade para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fc285-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>

- <span data-ttu-id="fc285-136">Configure o `Echo` serviço usando uma <xref:System.ServiceModel.WSHttpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="fc285-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Use a predefined WSHttpBinding to configure the service.
          WSHttpBinding binding = new WSHttpBinding();

          // Add the endpoint for this service to the service host.
          serviceHost.AddServiceEndpoint(
             typeof(IEcho),
             binding,
             echoUri
           );

          // Open the service host to run it.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Create a ServiceHost for the Echo service.
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)

' Use a predefined WSHttpBinding to configure the service.
Dim binding As New WSHttpBinding()

' Add the endpoint for this service to the service host.
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)

' Open the service host to run it.
serviceHost.Open()
```

> [!NOTE]
> <span data-ttu-id="fc285-137">O host de serviço é criado com um endereço base e, em seguida, o restante do endereço, relativo ao endereço base, é especificado como parte de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="fc285-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="fc285-138">Esse particionamento do endereço permite que vários pontos de extremidade sejam definidos mais convenientemente para os serviços em um host.</span><span class="sxs-lookup"><span data-stu-id="fc285-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>

> [!NOTE]
> <span data-ttu-id="fc285-139">As propriedades <xref:System.ServiceModel.Description.ServiceDescription> do no aplicativo de serviço não devem ser modificadas subsequentemente para <xref:System.ServiceModel.ServiceHostBase>o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método em.</span><span class="sxs-lookup"><span data-stu-id="fc285-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="fc285-140">Alguns <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Membros, como a propriedade e os `AddServiceEndpoint` métodos em <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, geram uma exceção, caso tenham sido modificados após esse ponto.</span><span class="sxs-lookup"><span data-stu-id="fc285-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="fc285-141">Outros permitem que você os modifique, mas o resultado é indefinido.</span><span class="sxs-lookup"><span data-stu-id="fc285-141">Others permit you to modify them, but the result is undefined.</span></span>
>
> <span data-ttu-id="fc285-142">Da mesma forma, no cliente <xref:System.ServiceModel.Description.ServiceEndpoint> , os valores não devem ser modificados após <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> a chamada <xref:System.ServiceModel.ChannelFactory>para no.</span><span class="sxs-lookup"><span data-stu-id="fc285-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="fc285-143">A <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade gera uma exceção se modificada após esse ponto.</span><span class="sxs-lookup"><span data-stu-id="fc285-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="fc285-144">Os outros valores de descrição do cliente podem ser modificados sem erros, mas o resultado é indefinido.</span><span class="sxs-lookup"><span data-stu-id="fc285-144">The other client description values can be modified without error, but the result is undefined.</span></span>
>
> <span data-ttu-id="fc285-145">Seja para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc285-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>

## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="fc285-146">Definindo pontos de extremidade na configuração</span><span class="sxs-lookup"><span data-stu-id="fc285-146">Defining Endpoints in Configuration</span></span>

<span data-ttu-id="fc285-147">Ao criar um aplicativo, muitas vezes você desejará adiar decisões para o administrador que está implantando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc285-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="fc285-148">Por exemplo, geralmente não há como saber com antecedência o que será um endereço de serviço (URI).</span><span class="sxs-lookup"><span data-stu-id="fc285-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="fc285-149">Em vez de embutir em código um endereço, é preferível permitir que um administrador faça isso depois de criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="fc285-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="fc285-150">Essa flexibilidade é realizada por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="fc285-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="fc285-151">Para obter detalhes, consulte Configurando [Serviços](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fc285-152">`[,`Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com a `/config:`opção filename*filename* `]` para criar arquivos de configuração rapidamente.</span><span class="sxs-lookup"><span data-stu-id="fc285-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>

## <a name="using-default-endpoints"></a><span data-ttu-id="fc285-153">Usando pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="fc285-153">Using Default Endpoints</span></span>

<span data-ttu-id="fc285-154">Se nenhum ponto de extremidade for especificado no código ou na configuração, o tempo de execução fornecerá os pontos de extremidade padrão adicionando um ponto de extremidades padrão para cada endereço base para cada contrato de serviço implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="fc285-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="fc285-155">O endereço base pode ser especificado no código ou na configuração, e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.ICommunicationObject.Open> é chamado <xref:System.ServiceModel.ServiceHost>no.</span><span class="sxs-lookup"><span data-stu-id="fc285-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="fc285-156">Este exemplo é o mesmo exemplo da seção anterior, mas como nenhum ponto de extremidade é especificado, os pontos de extremidade padrão são adicionados.</span><span class="sxs-lookup"><span data-stu-id="fc285-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
   {
      public string Hello(string name)
      {
         return "Hello" + name + "!";
      }
      public static void Main ()
      {
          //Specify the base address for Echo service.
          Uri echoUri = new Uri("http://localhost:8000/");

          //Create a ServiceHost for the Echo service.
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);

          // Open the service host to run it. Default endpoints
          // are added when the service is opened.
          serviceHost.Open();
     }
  }
}
```

```vb
' Define the contract for the IEcho service
    <ServiceContract()> _
    Public Interface IEcho
        <OperationContract()> _
        Function Hello(ByVal name As String) As String
    End Interface

' Create an Echo service that implements IEcho contract
    Public Class Echo
        Implements IEcho
        Public Function Hello(ByVal name As String) As String _
 Implements ICalculator.Hello
            Dim result As String = "Hello" + name + "!"
            Return result
        End Function

' Specify the base address for Echo service.
Dim echoUri As Uri = New Uri("http://localhost:8000/")

' Open the service host to run it. Default endpoints
' are added when the service is opened.
serviceHost.Open()
```

 <span data-ttu-id="fc285-157">Se os pontos de extremidade forem fornecidos explicitamente, os pontos de extremidade padrão ainda poderão ser adicionados chamando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> no antes <xref:System.ServiceModel.ServiceHost> de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc285-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="fc285-158">Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fc285-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc285-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc285-159">See also</span></span>

- [<span data-ttu-id="fc285-160">Implementando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="fc285-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
