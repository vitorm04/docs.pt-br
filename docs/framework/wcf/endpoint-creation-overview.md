---
title: Visão geral de criação de ponto de extremidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: b72c3959b2a42c6a5abc8ef31975d5bdb9ce220e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086837"
---
# <a name="endpoint-creation-overview"></a><span data-ttu-id="b24dd-102">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b24dd-102">Endpoint Creation Overview</span></span>
<span data-ttu-id="b24dd-103">Toda a comunicação com um serviço do Windows Communication Foundation (WCF) ocorre por meio de *pontos de extremidade* do serviço.</span><span class="sxs-lookup"><span data-stu-id="b24dd-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="b24dd-104">Pontos de extremidade fornecem os clientes acessem a funcionalidade que oferece um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="b24dd-104">Endpoints provide the clients access to the functionality that a WCF service offers.</span></span> <span data-ttu-id="b24dd-105">Esta seção descreve a estrutura de um ponto de extremidade e descreve como definir um ponto de extremidade na configuração e no código.</span><span class="sxs-lookup"><span data-stu-id="b24dd-105">This section describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="b24dd-106">A estrutura de um ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="b24dd-106">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="b24dd-107">Cada ponto de extremidade contém um endereço que indica onde encontrar o ponto de extremidade, uma associação que especifica como um cliente pode se comunicar com o ponto de extremidade e um contrato que identifica os métodos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b24dd-107">Each endpoint contains an address that indicates where to find the endpoint, a binding that specifies how a client can communicate with the endpoint, and a contract that identifies the methods available.</span></span>  
  
-   <span data-ttu-id="b24dd-108">**Endereço**.</span><span class="sxs-lookup"><span data-stu-id="b24dd-108">**Address**.</span></span> <span data-ttu-id="b24dd-109">O endereço identifica o ponto de extremidade exclusivamente e informa à consumidores em potencial em que o serviço está localizado.</span><span class="sxs-lookup"><span data-stu-id="b24dd-109">The address uniquely identifies the endpoint and tells potential consumers where the service is located.</span></span> <span data-ttu-id="b24dd-110">Ele é representado no modelo de objeto WCF pelo <xref:System.ServiceModel.EndpointAddress> endereço, que contém um identificador de recurso uniforme (URI) e as propriedades de endereço que incluem uma identidade, alguns elementos de descrição linguagem WSDL (Web Services) e uma coleção de opcional cabeçalhos.</span><span class="sxs-lookup"><span data-stu-id="b24dd-110">It is represented in the WCF object model by the <xref:System.ServiceModel.EndpointAddress> address, which contains a Uniform Resource Identifier (URI) and address properties that include an identity, some Web Services Description Language (WSDL) elements, and a collection of optional headers.</span></span> <span data-ttu-id="b24dd-111">Os cabeçalhos opcionais fornecem informações adicionais de endereçamento detalhadas para identificar ou interagir com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b24dd-111">The optional headers provide additional detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="b24dd-112">Para obter mais informações, consulte [especificação de um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="b24dd-112">For more information, see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="b24dd-113">**Associação**.</span><span class="sxs-lookup"><span data-stu-id="b24dd-113">**Binding**.</span></span> <span data-ttu-id="b24dd-114">A associação especifica como se comunicar com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b24dd-114">The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="b24dd-115">A associação especifica como o ponto de extremidade se comunica com o mundo, incluindo qual protocolo de transporte usar (por exemplo, TCP ou HTTP), codificação a ser usada para as mensagens (por exemplo, texto ou binário), e quais requisitos de segurança são necessários (para exemplo, Secure Sockets Layer [SSL] ou segurança de mensagem SOAP).</span><span class="sxs-lookup"><span data-stu-id="b24dd-115">The binding specifies how the endpoint communicates with the world, including which transport protocol to use (for example, TCP or HTTP), which encoding to use for the messages (for example, text or binary), and which security requirements are necessary (for example, Secure Sockets Layer [SSL] or SOAP message security).</span></span> <span data-ttu-id="b24dd-116">Para obter mais informações, consulte [usando associações para configurar os serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b24dd-116">For more information, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
-   <span data-ttu-id="b24dd-117">**Contrato de serviço**.</span><span class="sxs-lookup"><span data-stu-id="b24dd-117">**Service contract**.</span></span> <span data-ttu-id="b24dd-118">O contrato de serviço descreve qual funcionalidade que o ponto de extremidade expõe para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b24dd-118">The service contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="b24dd-119">Um contrato especifica as operações que um cliente pode chamar, o formulário da mensagem e o tipo de dados necessários para chamar a operação e o tipo de processamento ou o cliente pode esperar de mensagem de resposta ou parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="b24dd-119">A contract specifies the operations that a client can call, the form of the message and the type of input parameters or data required to call the operation, and the kind of processing or response message the client can expect.</span></span> <span data-ttu-id="b24dd-120">Três tipos básicos de contratos correspondem aos padrões de troca de mensagens básicas (MEPs): datagrama (unidirecional), solicitação/resposta e duplex (bidirecional).</span><span class="sxs-lookup"><span data-stu-id="b24dd-120">Three basic types of contracts correspond to basic message exchange patterns (MEPs): datagram (one-way), request/reply, and duplex (bidirectional).</span></span> <span data-ttu-id="b24dd-121">O contrato de serviço também pode empregar os contratos de dados e a mensagem em exigem tipos de dados específicos e formatos de mensagem quando acessados.</span><span class="sxs-lookup"><span data-stu-id="b24dd-121">The service contract can also employ data and message contracts to require specific data types and message formats when being accessed.</span></span> <span data-ttu-id="b24dd-122">Para obter mais informações sobre como definir um contrato de serviço, consulte [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b24dd-122">For more information about how to define a service contract, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span> <span data-ttu-id="b24dd-123">Observe que um cliente também pode ser necessário para implementar um contrato de serviço definido, chamado de um contrato de retorno de chamada, receber mensagens do serviço em um MEP duplex.</span><span class="sxs-lookup"><span data-stu-id="b24dd-123">Note that a client may also be required to implement a service-defined contract, called a callback contract, to receive messages from the service in a duplex MEP.</span></span> <span data-ttu-id="b24dd-124">Para obter mais informações, consulte [serviços Duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24dd-124">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="b24dd-125">O ponto de extremidade para um serviço pode ser especificado imperativamente por meio de código ou declarativamente por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="b24dd-125">The endpoint for a service can be specified either imperatively by using code or declaratively through configuration.</span></span> <span data-ttu-id="b24dd-126">Se nenhum ponto de extremidade forem especificados, em seguida, o tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão para cada endereço base para cada contrato de serviço implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="b24dd-126">If no endpoints are specified then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="b24dd-127">Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="b24dd-127">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="b24dd-128">Em geral, é mais prático definir pontos de extremidade de serviço usando a configuração em vez de código.</span><span class="sxs-lookup"><span data-stu-id="b24dd-128">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="b24dd-129">Informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar e reimplantar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24dd-129">Keeping the binding and addressing information out of the code allows them to change without having to recompile and redeploy the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b24dd-130">Ao adicionar um ponto de extremidade de serviço que executa representação, você deve usar um dos <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> métodos ou o <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> método para carregar corretamente o contrato em um novo <xref:System.ServiceModel.Description.ServiceDescription> objeto.</span><span class="sxs-lookup"><span data-stu-id="b24dd-130">When adding a service endpoint that performs impersonation, you must either use one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods or the <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> method to properly load the contract into a new <xref:System.ServiceModel.Description.ServiceDescription> object.</span></span>  
  
## <a name="defining-endpoints-in-code"></a><span data-ttu-id="b24dd-131">Definir pontos de extremidade no código</span><span class="sxs-lookup"><span data-stu-id="b24dd-131">Defining Endpoints in Code</span></span>  
 <span data-ttu-id="b24dd-132">O exemplo a seguir ilustra como especificar um ponto de extremidade no código com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b24dd-132">The following example illustrates how to specify an endpoint in code with the following:</span></span>  
  
-   <span data-ttu-id="b24dd-133">Definir um contrato para um `IEcho` tipo de serviço que aceita o nome e o eco com a resposta de alguém "Hello \<nome >!".</span><span class="sxs-lookup"><span data-stu-id="b24dd-133">Define a contract for an `IEcho` type of service that accepts someone's name and echo with the response "Hello \<name>!".</span></span>  
  
-   <span data-ttu-id="b24dd-134">Implementar uma `Echo` serviço do tipo definido pelo `IEcho` contrato.</span><span class="sxs-lookup"><span data-stu-id="b24dd-134">Implement an `Echo` service of the type defined by the `IEcho` contract.</span></span>  
  
-   <span data-ttu-id="b24dd-135">Especifique um endereço de ponto de extremidade de `http://localhost:8000/Echo` para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b24dd-135">Specify an endpoint address of `http://localhost:8000/Echo` for the service.</span></span>  
  
-   <span data-ttu-id="b24dd-136">Configurar o `Echo` usando um <xref:System.ServiceModel.WSHttpBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="b24dd-136">Configure the `Echo` service using a <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
```csharp  
Namespace Echo  
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
>  <span data-ttu-id="b24dd-137">O host de serviço é criado com um endereço básico e, em seguida, o restante do endereço, relativo ao endereço base, é especificado como parte de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b24dd-137">The service host is created with a base address and then the rest of the address, relative to the base address, is specified as part of an endpoint.</span></span> <span data-ttu-id="b24dd-138">Esse particionamento do endereço permite que vários pontos de extremidade seja definido de forma mais conveniente para os serviços em um host.</span><span class="sxs-lookup"><span data-stu-id="b24dd-138">This partitioning of the address allows multiple endpoints to be defined more conveniently for services at a host.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b24dd-139">Propriedades de <xref:System.ServiceModel.Description.ServiceDescription> no serviço de aplicativo não deve ser modificado subsequente para o <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> método em <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="b24dd-139">Properties of <xref:System.ServiceModel.Description.ServiceDescription> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method on <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="b24dd-140">Alguns membros, como o <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade e o `AddServiceEndpoint` métodos <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.ServiceHost>, lançar uma exceção se modificado além daquele ponto.</span><span class="sxs-lookup"><span data-stu-id="b24dd-140">Some members, such as the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost>, throw an exception if modified past that point.</span></span> <span data-ttu-id="b24dd-141">Outros permitem que você modificá-los, mas o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="b24dd-141">Others permit you to modify them, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="b24dd-142">Da mesma forma, no cliente a <xref:System.ServiceModel.Description.ServiceEndpoint> valores não devem ser modificados após a chamada para <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sobre o <xref:System.ServiceModel.ChannelFactory>.</span><span class="sxs-lookup"><span data-stu-id="b24dd-142">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory>.</span></span> <span data-ttu-id="b24dd-143">O <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade gera uma exceção se modificado após esse ponto.</span><span class="sxs-lookup"><span data-stu-id="b24dd-143">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property throws an exception if modified past that point.</span></span> <span data-ttu-id="b24dd-144">Os outros valores de descrição de cliente podem ser modificados sem erro, mas o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="b24dd-144">The other client description values can be modified without error, but the result is undefined.</span></span>  
>   
>  <span data-ttu-id="b24dd-145">Se para o serviço ou cliente, é recomendável que você modifique a descrição antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="b24dd-145">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span>  
  
## <a name="defining-endpoints-in-configuration"></a><span data-ttu-id="b24dd-146">Definir pontos de extremidade na configuração</span><span class="sxs-lookup"><span data-stu-id="b24dd-146">Defining Endpoints in Configuration</span></span>  
 <span data-ttu-id="b24dd-147">Ao criar um aplicativo, você geralmente deseja adiar as decisões para o administrador que está implantando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24dd-147">When creating an application, you often want to defer decisions to the administrator who is deploying the application.</span></span> <span data-ttu-id="b24dd-148">Por exemplo, há muitas vezes não há como saber antecipadamente que um serviço (um URI) de endereços será.</span><span class="sxs-lookup"><span data-stu-id="b24dd-148">For example, there is often no way of knowing in advance what a service address (a URI) will be.</span></span> <span data-ttu-id="b24dd-149">Em vez de embutir um endereço, é preferível para permitir que um administrador para fazer isso depois de criar um serviço.</span><span class="sxs-lookup"><span data-stu-id="b24dd-149">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="b24dd-150">Essa flexibilidade é realizada por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="b24dd-150">This flexibility is accomplished through configuration.</span></span> <span data-ttu-id="b24dd-151">Para obter detalhes, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24dd-151">For details, see [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b24dd-152">Use o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) com o `/config:` *filename*`[,`*filename* `]` alternar para Crie rapidamente arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b24dd-152">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config:`*filename*`[,`*filename*`]` switch to quickly create configuration files.</span></span>  
  
## <a name="using-default-endpoints"></a><span data-ttu-id="b24dd-153">Usando pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="b24dd-153">Using Default Endpoints</span></span>  
 <span data-ttu-id="b24dd-154">Se nenhum ponto de extremidade forem especificados no código ou na configuração, em seguida, o tempo de execução fornece pontos de extremidade padrão com a adição de um ponto de extremidade padrão para cada endereço base para cada contrato de serviço implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="b24dd-154">If no endpoints are specified in code or in configuration then the runtime provides default endpoints by adding one default endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="b24dd-155">O endereço base pode ser especificado no código ou na configuração e os pontos de extremidade padrão são adicionados quando <xref:System.ServiceModel.ICommunicationObject.Open> é chamado de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b24dd-155">The base address can be specified in code or in configuration, and the default endpoints are added when <xref:System.ServiceModel.ICommunicationObject.Open> is called on the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b24dd-156">Este exemplo é o mesmo exemplo da seção anterior, mas uma vez que nenhum ponto de extremidade forem especificados, os pontos de extremidade padrão são adicionados.</span><span class="sxs-lookup"><span data-stu-id="b24dd-156">This example is the same example from the previous section, but since no endpoints are specified, the default endpoints are added.</span></span>  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
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
  
 <span data-ttu-id="b24dd-157">Se os pontos de extremidade forem fornecidos explicitamente, os pontos de extremidade padrão ainda podem ser adicionados chamando <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> sobre o <xref:System.ServiceModel.ServiceHost> antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span><span class="sxs-lookup"><span data-stu-id="b24dd-157">If endpoints are explicitly provided, the default endpoints can still be added by calling <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> on the <xref:System.ServiceModel.ServiceHost> before calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.</span></span> <span data-ttu-id="b24dd-158">Para obter mais informações sobre pontos de extremidade padrão, consulte [configuração simplificado](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b24dd-158">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24dd-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b24dd-159">See Also</span></span>  
 [<span data-ttu-id="b24dd-160">Implementando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="b24dd-160">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
