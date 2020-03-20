---
title: Migrando de .NET Remoting para o WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183958"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="f868f-102">Migrando de .NET Remoting para o WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="f868f-103">Este artigo descreve como migrar um aplicativo que usa .NET Remoting para usar o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f868f-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f868f-104">Ele compara conceitos semelhantes entre esses produtos e, em seguida, descreve como realizar vários cenários de Remoting comuns no WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="f868f-105">.NET Remoting é um produto legado suportado apenas para compatibilidade retrógrada.</span><span class="sxs-lookup"><span data-stu-id="f868f-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="f868f-106">Ele não é seguro em ambientes de confiança mista porque não pode manter os níveis de confiança separados entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="f868f-107">Por exemplo, você nunca deve expor um ponto final .NET Remoting à Internet ou a clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="f868f-108">Recomendamos que os aplicativos de Remoting existentes sejam migrados para tecnologias mais novas e seguras.</span><span class="sxs-lookup"><span data-stu-id="f868f-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="f868f-109">Se o design do aplicativo usa apenas HTTP e é RESTful, recomendamos ASP.NET API da Web.</span><span class="sxs-lookup"><span data-stu-id="f868f-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="f868f-110">Para obter mais informações, consulte ASP.NET API web.</span><span class="sxs-lookup"><span data-stu-id="f868f-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="f868f-111">Se o aplicativo for baseado em SOAP ou exigir protocolos não-Http, como o TCP, recomendamos o WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="f868f-112">Comparando .NET Remoting com WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="f868f-113">Esta seção compara os blocos básicos de construção do .NET Remoting com seus equivalentes WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="f868f-114">Usaremos esses blocos de construção mais tarde para criar alguns cenários comuns de servidor de clientes no WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-114">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="f868f-115">O gráfico a seguir resume as principais semelhanças e diferenças entre .NET Remoting e WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-115">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="f868f-116">Comunicação remota .NET</span><span class="sxs-lookup"><span data-stu-id="f868f-116">.NET Remoting</span></span>|<span data-ttu-id="f868f-117">WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-117">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="f868f-118">Tipo de servidor</span><span class="sxs-lookup"><span data-stu-id="f868f-118">Server type</span></span>|<span data-ttu-id="f868f-119">Marechal de SubclasseByRefObject</span><span class="sxs-lookup"><span data-stu-id="f868f-119">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="f868f-120">Marcar com atributo [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="f868f-120">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="f868f-121">Operações de serviço</span><span class="sxs-lookup"><span data-stu-id="f868f-121">Service operations</span></span>|<span data-ttu-id="f868f-122">Métodos públicos sobre o tipo de servidor</span><span class="sxs-lookup"><span data-stu-id="f868f-122">Public methods on server type</span></span>|<span data-ttu-id="f868f-123">Marcar com atributo [OperaçãoContrato]</span><span class="sxs-lookup"><span data-stu-id="f868f-123">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="f868f-124">Serialização</span><span class="sxs-lookup"><span data-stu-id="f868f-124">Serialization</span></span>|<span data-ttu-id="f868f-125">ISerializable ou [Serializable]</span><span class="sxs-lookup"><span data-stu-id="f868f-125">ISerializable or [Serializable]</span></span>|<span data-ttu-id="f868f-126">DataContractSerializer ou XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f868f-126">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="f868f-127">Objetos passaram</span><span class="sxs-lookup"><span data-stu-id="f868f-127">Objects passed</span></span>|<span data-ttu-id="f868f-128">Por valor ou por referência</span><span class="sxs-lookup"><span data-stu-id="f868f-128">By-value or by-reference</span></span>|<span data-ttu-id="f868f-129">Apenas por valor</span><span class="sxs-lookup"><span data-stu-id="f868f-129">By-value only</span></span>|  
|<span data-ttu-id="f868f-130">Erros/exceções</span><span class="sxs-lookup"><span data-stu-id="f868f-130">Errors/exceptions</span></span>|<span data-ttu-id="f868f-131">Qualquer exceção serializável</span><span class="sxs-lookup"><span data-stu-id="f868f-131">Any serializable exception</span></span>|<span data-ttu-id="f868f-132">>\<de detalhes do contrato de falha</span><span class="sxs-lookup"><span data-stu-id="f868f-132">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="f868f-133">Objetos proxy do cliente</span><span class="sxs-lookup"><span data-stu-id="f868f-133">Client proxy objects</span></span>|<span data-ttu-id="f868f-134">Proxies transparentes fortemente digitados são criados automaticamente a partir de MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="f868f-134">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="f868f-135">Proxies fortemente digitados são gerados\<sob demanda usando o ChannelFactory TChannel></span><span class="sxs-lookup"><span data-stu-id="f868f-135">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="f868f-136">Plataforma necessária</span><span class="sxs-lookup"><span data-stu-id="f868f-136">Platform required</span></span>|<span data-ttu-id="f868f-137">Tanto o cliente quanto o servidor devem usar o Sistema Operacional Microsoft e o .NET</span><span class="sxs-lookup"><span data-stu-id="f868f-137">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="f868f-138">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="f868f-138">Cross-platform</span></span>|  
|<span data-ttu-id="f868f-139">Formato da mensagem</span><span class="sxs-lookup"><span data-stu-id="f868f-139">Message format</span></span>|<span data-ttu-id="f868f-140">Privado</span><span class="sxs-lookup"><span data-stu-id="f868f-140">Private</span></span>|<span data-ttu-id="f868f-141">Padrões da indústria (SOAP, WS-\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="f868f-141">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="f868f-142">Comparação de implementação do servidor</span><span class="sxs-lookup"><span data-stu-id="f868f-142">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="f868f-143">Criando um servidor em .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f868f-143">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="f868f-144">.NET Remoting tipos de servidor devem derivar do MarshalByRefObject e definir métodos que o cliente pode chamar, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f868f-144">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="f868f-145">Os métodos públicos desse tipo de servidor tornam-se o contrato público disponível aos clientes.</span><span class="sxs-lookup"><span data-stu-id="f868f-145">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="f868f-146">Não há separação entre a interface pública do servidor e sua implementação – um tipo lida com ambos.</span><span class="sxs-lookup"><span data-stu-id="f868f-146">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="f868f-147">Uma vez definido o tipo de servidor, ele pode ser disponibilizado aos clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-147">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),
    "RemotingServer",
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="f868f-148">Existem muitas maneiras de disponibilizar o tipo Remoting como servidor, inclusive usando arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="f868f-148">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="f868f-149">Este é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="f868f-149">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="f868f-150">Criando um servidor no WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-150">Creating a Server in WCF</span></span>  
 <span data-ttu-id="f868f-151">A etapa equivalente no WCF envolve a criação de dois tipos : o "contrato de serviço" público e a implementação concreta.</span><span class="sxs-lookup"><span data-stu-id="f868f-151">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="f868f-152">O primeiro é declarado como uma interface marcada com [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="f868f-152">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="f868f-153">Os métodos disponíveis para os clientes são marcados com [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="f868f-153">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="f868f-154">A implementação do servidor é definida em uma classe de concreto separada, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-154">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="f868f-155">Uma vez definidos esses tipos, o servidor WCF pode ser disponibilizado aos clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-155">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="f868f-156">TCP é usado em ambos os exemplos para mantê-los o mais semelhante possível.</span><span class="sxs-lookup"><span data-stu-id="f868f-156">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="f868f-157">Consulte o cenário de passo-a-passo mais tarde neste tópico, por exemplo, usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="f868f-157">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="f868f-158">Existem muitas maneiras de configurar e hospedar serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-158">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="f868f-159">Este é apenas um exemplo, conhecido como "auto-hospedado".</span><span class="sxs-lookup"><span data-stu-id="f868f-159">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="f868f-160">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="f868f-160">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="f868f-161">Como definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="f868f-161">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="f868f-162">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f868f-162">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="f868f-163">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="f868f-163">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="f868f-164">Comparação de implementação do cliente</span><span class="sxs-lookup"><span data-stu-id="f868f-164">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="f868f-165">Criando um Cliente em .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f868f-165">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="f868f-166">Uma vez que um objeto de servidor .NET Remoting tenha sido disponibilizado, ele pode ser consumido pelos clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-166">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="f868f-167">A instância RemotingServer retornada do Activator.GetObject() é conhecida como "proxy transparente".</span><span class="sxs-lookup"><span data-stu-id="f868f-167">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="f868f-168">Ele implementa a API pública para o tipo RemotingServer no cliente, mas todos os métodos chamam o objeto do servidor em execução em um processo ou máquina diferente.</span><span class="sxs-lookup"><span data-stu-id="f868f-168">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="f868f-169">Criando um cliente no WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-169">Creating a Client in WCF</span></span>  
 <span data-ttu-id="f868f-170">A etapa equivalente no WCF envolve o uso de uma fábrica de canais para criar o proxy explicitamente.</span><span class="sxs-lookup"><span data-stu-id="f868f-170">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="f868f-171">Assim como Remoting, o objeto proxy pode ser usado para invocar operações no servidor, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-171">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="f868f-172">Este exemplo mostra a programação no nível do canal porque é mais semelhante ao exemplo de Remoting.</span><span class="sxs-lookup"><span data-stu-id="f868f-172">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="f868f-173">Também está disponível a abordagem **Add Service Reference** no Visual Studio que gera código para simplificar a programação do cliente.</span><span class="sxs-lookup"><span data-stu-id="f868f-173">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="f868f-174">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="f868f-174">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="f868f-175">Programação de nível de canal do cliente</span><span class="sxs-lookup"><span data-stu-id="f868f-175">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="f868f-176">Como adicionar, atualizar ou remover uma referência de serviço</span><span class="sxs-lookup"><span data-stu-id="f868f-176">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="f868f-177">Uso de serialização</span><span class="sxs-lookup"><span data-stu-id="f868f-177">Serialization Usage</span></span>  
 <span data-ttu-id="f868f-178">Tanto o .NET Remoting quanto o WCF usam serialização para enviar objetos entre cliente e servidor, mas eles diferem destas maneiras importantes:</span><span class="sxs-lookup"><span data-stu-id="f868f-178">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="f868f-179">Eles usam serializadores e convenções diferentes para indicar o que serializar.</span><span class="sxs-lookup"><span data-stu-id="f868f-179">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="f868f-180">.NET Remoting suporta serialização "por referência" que permite que o método ou o acesso à propriedade em um nível execute o código no outro nível, que está além dos limites de segurança.</span><span class="sxs-lookup"><span data-stu-id="f868f-180">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="f868f-181">Esse recurso expõe vulnerabilidades de segurança e é uma das principais razões pelas quais os pontos finais de Remoting nunca devem ser expostos a clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-181">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="f868f-182">A serialização usada por Remoting é opt-out (exclua explicitamente o que não serializar) e a serialização do WCF é opt-in (marca explicitamente quais membros serializar).</span><span class="sxs-lookup"><span data-stu-id="f868f-182">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="f868f-183">Serialização em .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f868f-183">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="f868f-184">.NET Remoting suporta duas maneiras de serializar e desserializar objetos entre o cliente e o servidor:</span><span class="sxs-lookup"><span data-stu-id="f868f-184">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="f868f-185">*Por valor* – os valores do objeto são serializados através dos limites de nível, e uma nova instância desse objeto é criada no outro nível.</span><span class="sxs-lookup"><span data-stu-id="f868f-185">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="f868f-186">Quaisquer chamadas para métodos ou propriedades dessa nova instância são executadas apenas localmente e não afetam o objeto ou nível original.</span><span class="sxs-lookup"><span data-stu-id="f868f-186">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="f868f-187">*Por referência* – uma "referência de objeto" especial é serializada através dos limites de nível.</span><span class="sxs-lookup"><span data-stu-id="f868f-187">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="f868f-188">Quando um nível interage com métodos ou propriedades desse objeto, ele se comunica de volta ao objeto original no nível original.</span><span class="sxs-lookup"><span data-stu-id="f868f-188">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="f868f-189">Objetos de referência podem fluir em qualquer direção – servidor para cliente ou cliente para servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-189">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="f868f-190">Os tipos de valor por valor em Remoting são marcados com o atributo [Serializable] ou implementam ISerializable, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-190">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="f868f-191">Os tipos de referência derivam da classe MarshalByRefObject, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-191">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="f868f-192">É extremamente importante entender as implicações dos objetos de referência de Remoting.</span><span class="sxs-lookup"><span data-stu-id="f868f-192">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="f868f-193">Se o nível (cliente ou servidor) enviar um objeto de referência para o outro nível, todas as chamadas do método são executadas de volta no nível que possui o objeto.</span><span class="sxs-lookup"><span data-stu-id="f868f-193">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="f868f-194">Por exemplo, os métodos de chamada de cliente em um objeto de referência retornado pelo servidor executarão o código no servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-194">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="f868f-195">Da mesma forma, um método de chamada de servidor em um objeto de referência fornecido pelo cliente executará o código de volta no cliente.</span><span class="sxs-lookup"><span data-stu-id="f868f-195">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="f868f-196">Por essa razão, o uso do .NET Remoting é recomendado apenas em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-196">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="f868f-197">Expor um ponto final público .NET Remoting a clientes não confiáveis tornará um servidor Remoting vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="f868f-197">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="f868f-198">Serialização no WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-198">Serialization in WCF</span></span>  
 <span data-ttu-id="f868f-199">O WCF suporta apenas a serialização por valor.</span><span class="sxs-lookup"><span data-stu-id="f868f-199">WCF supports only by-value serialization.</span></span> <span data-ttu-id="f868f-200">A maneira mais comum de definir um tipo de troca entre cliente e servidor é como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f868f-200">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="f868f-201">O atributo [DataContract] identifica esse tipo como aquele que pode ser serializado e desserializado entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-201">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="f868f-202">O atributo [DataMember] identifica as propriedades ou campos individuais para serializar.</span><span class="sxs-lookup"><span data-stu-id="f868f-202">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="f868f-203">Quando o WCF envia um objeto entre os níveis, ele serializa apenas os valores e cria uma nova instância do objeto no outro nível.</span><span class="sxs-lookup"><span data-stu-id="f868f-203">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="f868f-204">Quaisquer interações com os valores do objeto ocorrem apenas localmente – elas não se comunicam com o outro nível da maneira que os objetos de referência .NET Remoting fazem.</span><span class="sxs-lookup"><span data-stu-id="f868f-204">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="f868f-205">Para obter mais informações, consulte [Serialização e Desserialização](./feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="f868f-205">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="f868f-206">Recursos de manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="f868f-206">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="f868f-207">Exceções em .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f868f-207">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="f868f-208">As exceções lançadas por um servidor Remoting são serializadas, enviadas ao cliente e jogadas localmente no cliente como qualquer outra exceção.</span><span class="sxs-lookup"><span data-stu-id="f868f-208">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="f868f-209">Exceções personalizadas podem ser criadas subclassificando o tipo Exceção e marcando-a com [Serializable].</span><span class="sxs-lookup"><span data-stu-id="f868f-209">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="f868f-210">A maioria das exceções de quadro já estão marcadas dessa forma, permitindo que a maioria seja lançada pelo servidor, serializada e relançada no cliente.</span><span class="sxs-lookup"><span data-stu-id="f868f-210">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="f868f-211">Embora este design seja conveniente durante o desenvolvimento, as informações do lado do servidor podem ser inadvertidamente divulgadas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="f868f-211">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="f868f-212">Esta é uma das muitas razões pelas quais remoting deve ser usado apenas em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-212">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="f868f-213">Exceções e Falhas no WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-213">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="f868f-214">O WCF não permite que tipos de exceção arbitrária sejam devolvidos do servidor para o cliente porque isso pode levar à divulgação inadvertida de informações.</span><span class="sxs-lookup"><span data-stu-id="f868f-214">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="f868f-215">Se uma operação de serviço lança uma exceção inesperada, isso faz com que uma falha exceção de propósito geral seja lançada sobre o cliente.</span><span class="sxs-lookup"><span data-stu-id="f868f-215">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="f868f-216">Esta exceção não carrega nenhuma informação por que ou onde o problema ocorreu, e para algumas aplicações isso é suficiente.</span><span class="sxs-lookup"><span data-stu-id="f868f-216">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="f868f-217">Aplicativos que precisam comunicar informações de erro mais ricas ao cliente fazem isso definindo um contrato de falha.</span><span class="sxs-lookup"><span data-stu-id="f868f-217">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="f868f-218">Para fazer isso, primeiro crie um tipo [DataContract] para transportar as informações de falha.</span><span class="sxs-lookup"><span data-stu-id="f868f-218">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="f868f-219">Especifique o contrato de falha a ser usado para cada operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f868f-219">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="f868f-220">O servidor relata condições de erro lançando uma FalhaExceto.</span><span class="sxs-lookup"><span data-stu-id="f868f-220">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 <span data-ttu-id="f868f-221">E sempre que o cliente faz uma solicitação ao servidor, ele pode pegar falhas como exceções normais.</span><span class="sxs-lookup"><span data-stu-id="f868f-221">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 <span data-ttu-id="f868f-222">Para obter mais informações <xref:System.ServiceModel.FaultException>sobre contratos de falha, consulte .</span><span class="sxs-lookup"><span data-stu-id="f868f-222">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="f868f-223">Considerações de segurança</span><span class="sxs-lookup"><span data-stu-id="f868f-223">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="f868f-224">Segurança em .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="f868f-224">Security in .NET Remoting</span></span>  
 <span data-ttu-id="f868f-225">Alguns canais .NET Remoting suportam recursos de segurança, como autenticação e criptografia na camada de canal (IPC e TCP).</span><span class="sxs-lookup"><span data-stu-id="f868f-225">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="f868f-226">O canal HTTP conta com o IIS (Internet Information Services, serviços de informação à Internet) tanto para autenticação quanto para criptografia.</span><span class="sxs-lookup"><span data-stu-id="f868f-226">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="f868f-227">Apesar desse suporte, você deve considerar .NET Remoting um protocolo de comunicação inseguro e usá-lo apenas em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-227">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="f868f-228">Nunca exponha um ponto final de Remoting público à Internet ou clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-228">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="f868f-229">Segurança no WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-229">Security in WCF</span></span>  
 <span data-ttu-id="f868f-230">O WCF foi projetado com a segurança em mente, em parte para abordar os tipos de vulnerabilidades encontradas no .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="f868f-230">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="f868f-231">O WCF oferece segurança tanto no nível de transporte quanto de mensagem, e oferece muitas opções de autenticação, autorização, criptografia e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f868f-231">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="f868f-232">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="f868f-232">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="f868f-233">Segurança</span><span class="sxs-lookup"><span data-stu-id="f868f-233">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="f868f-234">Orientação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="f868f-234">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="f868f-235">Migrando para wcf</span><span class="sxs-lookup"><span data-stu-id="f868f-235">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="f868f-236">Por que migrar de Remoting para WCF?</span><span class="sxs-lookup"><span data-stu-id="f868f-236">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="f868f-237">**.NET Remoting é um produto legado.**</span><span class="sxs-lookup"><span data-stu-id="f868f-237">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="f868f-238">Como descrito em [.NET Remoting,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)é considerado um produto legado e não é recomendado para novos desenvolvimentos.</span><span class="sxs-lookup"><span data-stu-id="f868f-238">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="f868f-239">O WCF ou ASP.NET API da Web são recomendados para aplicativos novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="f868f-239">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="f868f-240">**O WCF usa padrões multiplataforma.**</span><span class="sxs-lookup"><span data-stu-id="f868f-240">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="f868f-241">O WCF foi projetado com a interoperabilidade multiplataforma em mente e suporta muitos padrões do setor (SOAP, WS-Security, WS-Trust, etc.).</span><span class="sxs-lookup"><span data-stu-id="f868f-241">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="f868f-242">Um serviço WCF pode interoperar com clientes em execução em sistemas operacionais diferentes do Windows.</span><span class="sxs-lookup"><span data-stu-id="f868f-242">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="f868f-243">Remoting foi projetado principalmente para ambientes onde os aplicativos de servidor e cliente são executados usando o .NET Framework em um sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="f868f-243">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="f868f-244">**A WCF tem segurança embutida.**</span><span class="sxs-lookup"><span data-stu-id="f868f-244">**WCF has built-in security.**</span></span> <span data-ttu-id="f868f-245">O WCF foi projetado com a segurança em mente e oferece muitas opções de autenticação, segurança de nível de transporte, segurança de nível de mensagem, etc. Remoting foi projetado para facilitar a interoperação de aplicativos, mas não foi projetado para ser seguro em ambientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-245">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="f868f-246">O WCF foi projetado para funcionar em ambientes confiáveis e não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-246">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="f868f-247">Recomendações de migração</span><span class="sxs-lookup"><span data-stu-id="f868f-247">Migration Recommendations</span></span>  
 <span data-ttu-id="f868f-248">A seguir estão as etapas recomendadas para migrar de .NET Remoting para WCF:</span><span class="sxs-lookup"><span data-stu-id="f868f-248">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="f868f-249">**Crie o contrato de serviço.**</span><span class="sxs-lookup"><span data-stu-id="f868f-249">**Create the service contract.**</span></span> <span data-ttu-id="f868f-250">Defina os tipos de interface de serviço e marque-os com o atributo [ServiceContract]. Marque todos os métodos que os clientes poderão ligar com [OperaçãoContrato].</span><span class="sxs-lookup"><span data-stu-id="f868f-250">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="f868f-251">**Crie o contrato de dados.**</span><span class="sxs-lookup"><span data-stu-id="f868f-251">**Create the data contract.**</span></span> <span data-ttu-id="f868f-252">Defina os tipos de dados que serão trocados entre servidor e cliente e marque-os com o atributo [DataContract].</span><span class="sxs-lookup"><span data-stu-id="f868f-252">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="f868f-253">Marque todos os campos e propriedades que o cliente poderá usar com [DataMember].</span><span class="sxs-lookup"><span data-stu-id="f868f-253">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="f868f-254">**Crie o contrato de falha (opcional).**</span><span class="sxs-lookup"><span data-stu-id="f868f-254">**Create the fault contract (optional).**</span></span> <span data-ttu-id="f868f-255">Crie os tipos que serão trocados entre servidor e cliente quando os erros forem encontrados.</span><span class="sxs-lookup"><span data-stu-id="f868f-255">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="f868f-256">Marque esses tipos com [DataContract] e [DataMember] para torná-los serializáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-256">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="f868f-257">Para todas as operações de serviço que você marcou com [OperaçãoContrato], também marque-as com [Contrato de falha] para indicar quais erros eles podem retornar.</span><span class="sxs-lookup"><span data-stu-id="f868f-257">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="f868f-258">**Configure e hospede o serviço.**</span><span class="sxs-lookup"><span data-stu-id="f868f-258">**Configure and host the service.**</span></span> <span data-ttu-id="f868f-259">Uma vez que o contrato de serviço tenha sido criado, o próximo passo é configurar uma vinculação para expor o serviço em um ponto final.</span><span class="sxs-lookup"><span data-stu-id="f868f-259">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="f868f-260">Para obter mais informações, consulte [Endpoints: Endereços, Vinculações e Contratos](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="f868f-260">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="f868f-261">Uma vez que um aplicativo Remoting tenha sido migrado para o WCF, ainda é importante remover dependências do .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="f868f-261">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="f868f-262">Isso garante que quaisquer vulnerabilidades remoting sejam removidas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f868f-262">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="f868f-263">Estas etapas incluem as seguintes:</span><span class="sxs-lookup"><span data-stu-id="f868f-263">These steps include the following:</span></span>  
  
- <span data-ttu-id="f868f-264">**Descontinuar o uso do MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="f868f-264">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="f868f-265">O tipo MarshalByRefObject existe apenas para Remoting e não é usado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-265">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="f868f-266">Todos os tipos de aplicativos que subclasse MarshalByRefObject devem ser removidos ou alterados.</span><span class="sxs-lookup"><span data-stu-id="f868f-266">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="f868f-267">**Descontinuar o uso de [Serializable] e ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="f868f-267">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="f868f-268">O atributo [Serializable] e a interface ISerializable foram originalmente projetados para serializar tipos em ambientes confiáveis, e eles são usados por Remoting.</span><span class="sxs-lookup"><span data-stu-id="f868f-268">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="f868f-269">A serialização do WCF depende de tipos que estão sendo marcados com [DataContract] e [DataMember].</span><span class="sxs-lookup"><span data-stu-id="f868f-269">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="f868f-270">Os tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não para usar ISerializable ou [Serializable].</span><span class="sxs-lookup"><span data-stu-id="f868f-270">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="f868f-271">Cenários de migração</span><span class="sxs-lookup"><span data-stu-id="f868f-271">Migration Scenarios</span></span>  
 <span data-ttu-id="f868f-272">Agora vamos ver como realizar os seguintes cenários comuns de Remoting no WCF:</span><span class="sxs-lookup"><span data-stu-id="f868f-272">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="f868f-273">O servidor retorna um objeto por valor para o cliente</span><span class="sxs-lookup"><span data-stu-id="f868f-273">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="f868f-274">O servidor retorna um objeto por referência ao cliente</span><span class="sxs-lookup"><span data-stu-id="f868f-274">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="f868f-275">O cliente envia um objeto por valor para o servidor</span><span class="sxs-lookup"><span data-stu-id="f868f-275">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f868f-276">O envio de uma referência de objeto do cliente para o servidor não é permitido no WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-276">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="f868f-277">Ao ler esses cenários, assuma que nossas interfaces de linha de base para .NET Remoting se parecem com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f868f-277">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="f868f-278">A implementação do .NET Remoting não é importante aqui porque queremos ilustrar apenas como usar o WCF para implementar funcionalidades equivalentes.</span><span class="sxs-lookup"><span data-stu-id="f868f-278">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="f868f-279">Cenário 1: O serviço retorna um objeto por valor</span><span class="sxs-lookup"><span data-stu-id="f868f-279">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="f868f-280">Esse cenário demonstra um servidor devolvendo um objeto ao cliente por valor.</span><span class="sxs-lookup"><span data-stu-id="f868f-280">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="f868f-281">O WCF sempre retorna objetos do servidor por valor, então as etapas a seguir simplesmente descrevem como construir um serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="f868f-281">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="f868f-282">Comece definindo uma interface pública para o serviço WCF e marque-a com o atributo [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="f868f-282">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="f868f-283">Usamos [OperationContract] para identificar os métodos do lado do servidor que nosso cliente chamará.</span><span class="sxs-lookup"><span data-stu-id="f868f-283">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. <span data-ttu-id="f868f-284">O próximo passo é criar o contrato de dados para este serviço.</span><span class="sxs-lookup"><span data-stu-id="f868f-284">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="f868f-285">Fazemos isso criando classes (não interfaces) marcadas com o atributo [DataContract].</span><span class="sxs-lookup"><span data-stu-id="f868f-285">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="f868f-286">As propriedades individuais ou campos que queremos visíveis para cliente e servidor são marcados com [DataMember].</span><span class="sxs-lookup"><span data-stu-id="f868f-286">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="f868f-287">Se quisermos que tipos derivados sejam permitidos, devemos usar o atributo [KnownType] para identificá-los.</span><span class="sxs-lookup"><span data-stu-id="f868f-287">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="f868f-288">Os únicos tipos que o WCF permitirá ser serializado ou desserializado para este serviço são aqueles na interface de serviço e esses "tipos conhecidos".</span><span class="sxs-lookup"><span data-stu-id="f868f-288">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="f868f-289">A tentativa de trocar qualquer outro tipo que não esteja nesta lista será rejeitada.</span><span class="sxs-lookup"><span data-stu-id="f868f-289">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. <span data-ttu-id="f868f-290">Em seguida, fornecemos a implementação para a interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="f868f-290">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. <span data-ttu-id="f868f-291">Para executar o serviço WCF, precisamos declarar um ponto final que exponha essa interface de serviço em uma URL específica usando uma vinculação WCF específica.</span><span class="sxs-lookup"><span data-stu-id="f868f-291">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="f868f-292">Isso é normalmente feito adicionando as seguintes seções ao arquivo web.config do projeto servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-292">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. <span data-ttu-id="f868f-293">O serviço WCF pode então ser iniciado com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="f868f-293">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="f868f-294">Quando este ServiceHost é iniciado, ele usa o arquivo Web.config para estabelecer o contrato, vinculação e ponto final adequados.</span><span class="sxs-lookup"><span data-stu-id="f868f-294">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="f868f-295">Para obter mais informações sobre arquivos de configuração, consulte [Configuração de serviços usando arquivos de configuração](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="f868f-295">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="f868f-296">Este estilo de iniciar o servidor é conhecido como auto-hospedagem.</span><span class="sxs-lookup"><span data-stu-id="f868f-296">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="f868f-297">Para saber mais sobre outras opções para hospedar serviços WCF, consulte [Serviços de hospedagem](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="f868f-297">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="f868f-298">O aplicativo.config do projeto cliente deve declarar informações vinculativas correspondentes para o ponto final do serviço.</span><span class="sxs-lookup"><span data-stu-id="f868f-298">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="f868f-299">A maneira mais fácil de fazer isso no Visual Studio é usar **o Add Service Reference**, que atualizará automaticamente o arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="f868f-299">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="f868f-300">Alternativamente, essas mesmas alterações podem ser adicionadas manualmente.</span><span class="sxs-lookup"><span data-stu-id="f868f-300">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="f868f-301">Para obter mais informações sobre como usar **o Add Service Reference,** consulte [Como: Adicionar, Atualizar ou Remover uma Referência de Serviço](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="f868f-301">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="f868f-302">Agora podemos chamar o serviço WCF do cliente.</span><span class="sxs-lookup"><span data-stu-id="f868f-302">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="f868f-303">Fazemos isso criando uma fábrica de canais para esse serviço, pedindo-lhe um canal, e ligando diretamente para o método que queremos naquele canal.</span><span class="sxs-lookup"><span data-stu-id="f868f-303">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="f868f-304">Podemos fazer isso porque o canal implementa a interface do serviço e lida com a lógica de solicitação/resposta subjacente para nós.</span><span class="sxs-lookup"><span data-stu-id="f868f-304">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="f868f-305">O valor de devolução dessa chamada de método é a cópia desserializada da resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-305">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="f868f-306">Os objetos devolvidos pelo WCF do servidor para o cliente são sempre por valor.</span><span class="sxs-lookup"><span data-stu-id="f868f-306">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="f868f-307">Os objetos são cópias desserializadas dos dados enviados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-307">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="f868f-308">O cliente pode chamar métodos nessas cópias locais sem qualquer perigo de invocar o código do servidor através de retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="f868f-308">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="f868f-309">Cenário 2: Servidor retorna um objeto por referência</span><span class="sxs-lookup"><span data-stu-id="f868f-309">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="f868f-310">Esse cenário demonstra o servidor fornecendo um objeto ao cliente por referência.</span><span class="sxs-lookup"><span data-stu-id="f868f-310">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="f868f-311">Em .NET Remoting, isso é tratado automaticamente para qualquer tipo derivado de MarshalByRefObject, que é serializado por referência.</span><span class="sxs-lookup"><span data-stu-id="f868f-311">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="f868f-312">Um exemplo desse cenário é permitir que vários clientes tenham objetos independentes do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-312">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="f868f-313">Como mencionado anteriormente, objetos retornados por um serviço WCF são sempre por valor, portanto não há equivalente direto de um objeto de <xref:System.ServiceModel.EndpointAddress10> referência, mas é possível alcançar algo semelhante à semântica de referência usando um objeto.</span><span class="sxs-lookup"><span data-stu-id="f868f-313">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="f868f-314">Este é um objeto por valor serializável que pode ser usado pelo cliente para obter um objeto de referência por sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-314">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="f868f-315">Isso permite o cenário de ter vários clientes com objetos independentes do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-315">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="f868f-316">Primeiro, precisamos definir um contrato de serviço wcf que corresponda ao objeto em si.</span><span class="sxs-lookup"><span data-stu-id="f868f-316">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > <span data-ttu-id="f868f-317">Observe que o objeto de sessão está marcado com [ServiceContract], tornando-o uma interface de serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="f868f-317">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="f868f-318">A configuração da propriedade SessionMode indica que será um serviço de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-318">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="f868f-319">No WCF, uma sessão é uma maneira de correlacionar várias mensagens enviadas entre dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="f868f-319">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="f868f-320">Isso significa que, depois que um cliente obtiver uma conexão para esse serviço, uma sessão será estabelecida entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-320">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="f868f-321">O cliente usará uma única instância exclusiva do objeto do lado do servidor para todas as interações dele nessa única sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-321">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="f868f-322">Em seguida, precisamos fornecer a implementação desta interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="f868f-322">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="f868f-323">Ao denotá-lo com [ServiceBehavior] e definir o InstanceContextMode, dizemos ao WCF que queremos usar uma instância única desse tipo para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-323">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. <span data-ttu-id="f868f-324">Agora precisamos de uma maneira de obter uma instância deste objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-324">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="f868f-325">Fazemos isso criando outra interface de serviço WCF que retorna um objeto EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="f868f-325">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="f868f-326">Esta é uma forma serializável de um ponto final que o cliente pode usar para criar o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-326">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="f868f-327">E implementamos este serviço WCF:</span><span class="sxs-lookup"><span data-stu-id="f868f-327">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =
               new ChannelFactory<ISessionBoundObject>("sessionbound");  

           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="f868f-328">Essa implementação mantém uma fábrica de canais única para criar objetos de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-328">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="f868f-329">Quando getInstanceAddress() é chamado, ele cria um canal e cria um objeto EndpointAddress10 que efetivamente aponta para o endereço remoto associado a este canal.</span><span class="sxs-lookup"><span data-stu-id="f868f-329">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="f868f-330">EndpointAddress10 é simplesmente um tipo de dados que pode ser devolvido ao cliente por valor.</span><span class="sxs-lookup"><span data-stu-id="f868f-330">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="f868f-331">Precisamos modificar o arquivo de configuração do servidor fazendo as duas seguintes coisas, conforme mostrado no exemplo abaixo:</span><span class="sxs-lookup"><span data-stu-id="f868f-331">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="f868f-332">Declare \<uma seção de> cliente que descreva o ponto final para o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-332">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="f868f-333">Isso é necessário porque o servidor também atua como cliente nessa situação.</span><span class="sxs-lookup"><span data-stu-id="f868f-333">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="f868f-334">Declare pontos finais para o objeto de fábrica e sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-334">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="f868f-335">Isso é necessário para permitir que o cliente se comunique com os pontos finais do serviço para adquirir o EndpointAddress10 e criar o canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-335">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="f868f-336">E então podemos iniciar esses serviços:</span><span class="sxs-lookup"><span data-stu-id="f868f-336">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="f868f-337">Configuramos o cliente declarando esses mesmos pontos finais no arquivo app.config do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f868f-337">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. <span data-ttu-id="f868f-338">Para criar e usar este objeto de sessão, o cliente deve fazer as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="f868f-338">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="f868f-339">Crie um canal para o serviço ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="f868f-339">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="f868f-340">Use esse canal para invocar esse serviço para obter um EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="f868f-340">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="f868f-341">Use o EndpointAddress10 para criar um canal para obter um objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="f868f-341">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="f868f-342">Interaja com o objeto de sessão para demonstrar que ele permanece a mesma instância em várias chamadas.</span><span class="sxs-lookup"><span data-stu-id="f868f-342">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="f868f-343">O WCF sempre retorna objetos por valor, mas é possível suportar o equivalente à semântica por referência através do uso do EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="f868f-343">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="f868f-344">Isso permite que o cliente solicite uma instância de serviço WCF em sessão, após a qual ele pode interagir com ele como qualquer outro serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-344">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="f868f-345">Cenário 3: O cliente envia ao servidor uma instância de valor por valor</span><span class="sxs-lookup"><span data-stu-id="f868f-345">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="f868f-346">Esse cenário demonstra o cliente enviando uma instância de objeto não primitivo para o servidor por valor.</span><span class="sxs-lookup"><span data-stu-id="f868f-346">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="f868f-347">Como o WCF envia apenas objetos por valor, esse cenário demonstra o uso normal do WCF.</span><span class="sxs-lookup"><span data-stu-id="f868f-347">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="f868f-348">Use o mesmo Serviço WCF do Cenário 1.</span><span class="sxs-lookup"><span data-stu-id="f868f-348">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="f868f-349">Use o cliente para criar um novo objeto por valor (Cliente), crie um canal para se comunicar com o serviço ICustomerService e envie o objeto para ele.</span><span class="sxs-lookup"><span data-stu-id="f868f-349">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {
   FirstName = "Bob",
   LastName = "Jones",
   CustomerId = 43,
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     <span data-ttu-id="f868f-350">O objeto do cliente será serializado e enviado para o servidor, onde é desserializado em uma nova cópia desse objeto.</span><span class="sxs-lookup"><span data-stu-id="f868f-350">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f868f-351">Este código também ilustra o envio de um tipo derivado (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="f868f-351">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="f868f-352">A interface de serviço espera um objeto cliente, mas o atributo [KnownType] na classe Cliente indicado PremiumCustomer também foi permitido.</span><span class="sxs-lookup"><span data-stu-id="f868f-352">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="f868f-353">O WCF falhará em qualquer tentativa de serializar ou desserializar qualquer outro tipo através desta interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="f868f-353">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="f868f-354">As trocas normais de dados do WCF são por valor.</span><span class="sxs-lookup"><span data-stu-id="f868f-354">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="f868f-355">Isso garante que a invocação de métodos em um desses objetos de dados seja executada apenas localmente – ele não invocará código no outro nível.</span><span class="sxs-lookup"><span data-stu-id="f868f-355">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="f868f-356">Embora seja possível conseguir algo como objetos de referência retornados *do* servidor, não é possível que um cliente passe um objeto de referência *para* o servidor.</span><span class="sxs-lookup"><span data-stu-id="f868f-356">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="f868f-357">Um cenário que requer uma conversa de ida e volta entre o cliente e o servidor pode ser obtido no WCF usando um serviço duplex.</span><span class="sxs-lookup"><span data-stu-id="f868f-357">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="f868f-358">Para obter mais informações, consulte [Serviços Duplex](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="f868f-358">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="f868f-359">Resumo</span><span class="sxs-lookup"><span data-stu-id="f868f-359">Summary</span></span>  
 <span data-ttu-id="f868f-360">.NET Remoting é uma estrutura de comunicação destinada a ser usada apenas em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f868f-360">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="f868f-361">É um produto legado e suportado apenas para compatibilidade retrógrada.</span><span class="sxs-lookup"><span data-stu-id="f868f-361">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="f868f-362">Ele não deve ser usado para construir novas aplicações.</span><span class="sxs-lookup"><span data-stu-id="f868f-362">It should not be used to build new applications.</span></span> <span data-ttu-id="f868f-363">Por outro lado, o WCF foi projetado com a segurança em mente e é recomendado para aplicativos novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="f868f-363">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="f868f-364">A Microsoft recomenda que os aplicativos remoting existentes sejam migrados para usar o WCF ou ASP.NET API da Web.</span><span class="sxs-lookup"><span data-stu-id="f868f-364">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
