---
title: Migrando de .NET Remoting para o WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c42255a14a23cb50f3fe8be434efab4af7361daa
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045862"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="a8aaf-102">Migrando de .NET Remoting para o WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="a8aaf-103">Este artigo descreve como migrar um aplicativo que usa a comunicação remota do .NET para usar o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a8aaf-104">Ele compara conceitos semelhantes entre esses produtos e descreve como realizar vários cenários comuns de comunicação remota no WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="a8aaf-105">O .NET Remoting é um produto herdado que tem suporte apenas para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="a8aaf-106">Ele não é seguro entre ambientes de confiança mista porque não pode manter os níveis de confiança separados entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="a8aaf-107">Por exemplo, você nunca deve expor um ponto de extremidade de comunicação remota do .NET à Internet ou a clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="a8aaf-108">Recomendamos que os aplicativos de comunicação remota existentes sejam migrados para tecnologias mais novas e mais seguras.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="a8aaf-109">Se o design do aplicativo usar apenas HTTP e for RESTful, recomendamos ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="a8aaf-110">Para obter mais informações, consulte ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="a8aaf-111">Se o aplicativo for baseado em SOAP ou exigir protocolos não http, como TCP, recomendamos o WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="a8aaf-112">Comparando o .NET Remoting com o WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="a8aaf-113">Esta seção compara os blocos de construção básicos da comunicação remota do .NET com seus equivalentes do WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="a8aaf-114">Usaremos esses blocos de construção posteriormente para criar alguns cenários comuns de cliente-servidor no WCF. O gráfico a seguir resume as principais semelhanças e diferenças entre o .NET Remoting e o WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="a8aaf-115">Comunicação remota .NET</span><span class="sxs-lookup"><span data-stu-id="a8aaf-115">.NET Remoting</span></span>|<span data-ttu-id="a8aaf-116">WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="a8aaf-117">Tipo de servidor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-117">Server type</span></span>|<span data-ttu-id="a8aaf-118">MarshalByRefObject de subclasse</span><span class="sxs-lookup"><span data-stu-id="a8aaf-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="a8aaf-119">Marcar com atributo [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="a8aaf-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="a8aaf-120">Operações de serviço</span><span class="sxs-lookup"><span data-stu-id="a8aaf-120">Service operations</span></span>|<span data-ttu-id="a8aaf-121">Métodos públicos no tipo de servidor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-121">Public methods on server type</span></span>|<span data-ttu-id="a8aaf-122">Marcar com atributo [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="a8aaf-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="a8aaf-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="a8aaf-123">Serialization</span></span>|<span data-ttu-id="a8aaf-124">ISerializable ou [Serializable]</span><span class="sxs-lookup"><span data-stu-id="a8aaf-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="a8aaf-125">DataContractSerializer ou XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="a8aaf-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="a8aaf-126">Objetos aprovados</span><span class="sxs-lookup"><span data-stu-id="a8aaf-126">Objects passed</span></span>|<span data-ttu-id="a8aaf-127">Por valor ou por referência</span><span class="sxs-lookup"><span data-stu-id="a8aaf-127">By-value or by-reference</span></span>|<span data-ttu-id="a8aaf-128">Somente por valor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-128">By-value only</span></span>|  
|<span data-ttu-id="a8aaf-129">Erros/exceções</span><span class="sxs-lookup"><span data-stu-id="a8aaf-129">Errors/exceptions</span></span>|<span data-ttu-id="a8aaf-130">Qualquer exceção serializável</span><span class="sxs-lookup"><span data-stu-id="a8aaf-130">Any serializable exception</span></span>|<span data-ttu-id="a8aaf-131">FaultContract\<TDetail></span><span class="sxs-lookup"><span data-stu-id="a8aaf-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="a8aaf-132">Objetos de proxy de cliente</span><span class="sxs-lookup"><span data-stu-id="a8aaf-132">Client proxy objects</span></span>|<span data-ttu-id="a8aaf-133">Proxies transparentes com rigidez de tipos são criados automaticamente a partir de MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="a8aaf-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="a8aaf-134">Proxies com rigidez de tipos são gerados sob demanda usando\<ChannelFactory TChannel ></span><span class="sxs-lookup"><span data-stu-id="a8aaf-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="a8aaf-135">Plataforma necessária</span><span class="sxs-lookup"><span data-stu-id="a8aaf-135">Platform required</span></span>|<span data-ttu-id="a8aaf-136">O cliente e o servidor devem usar o Microsoft OS e o .NET</span><span class="sxs-lookup"><span data-stu-id="a8aaf-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="a8aaf-137">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="a8aaf-137">Cross-platform</span></span>|  
|<span data-ttu-id="a8aaf-138">Formato da mensagem</span><span class="sxs-lookup"><span data-stu-id="a8aaf-138">Message format</span></span>|<span data-ttu-id="a8aaf-139">Particular</span><span class="sxs-lookup"><span data-stu-id="a8aaf-139">Private</span></span>|<span data-ttu-id="a8aaf-140">Padrões do setor (SOAP, WS-\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="a8aaf-140">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="a8aaf-141">Comparação de implementação do servidor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="a8aaf-142">Criando um servidor na comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="a8aaf-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="a8aaf-143">Os tipos de servidor de comunicação remota do .NET devem derivar de MarshalByRefObject e definir métodos que o cliente pode chamar, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="a8aaf-144">Os métodos públicos desse tipo de servidor tornam-se o contrato público disponível para os clientes.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="a8aaf-145">Não há nenhuma separação entre a interface pública do servidor e sua implementação – um tipo manipula ambos.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="a8aaf-146">Depois que o tipo de servidor tiver sido definido, ele poderá ser disponibilizado para os clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a8aaf-147">Há várias maneiras de tornar o tipo de comunicação remota disponível como um servidor, incluindo o uso de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="a8aaf-148">Este é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="a8aaf-149">Criando um servidor no WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="a8aaf-150">A etapa equivalente no WCF envolve a criação de dois tipos – o "contrato de serviço" público e a implementação concreta.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="a8aaf-151">A primeira é declarada como uma interface marcada com [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="a8aaf-152">Os métodos disponíveis para os clientes são marcados com [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="a8aaf-153">A implementação do servidor é definida em uma classe concreta separada, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="a8aaf-154">Depois que esses tipos tiverem sido definidos, o servidor WCF poderá ser disponibilizado para os clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
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
> <span data-ttu-id="a8aaf-155">O TCP é usado em ambos os exemplos para mantê-los o mais semelhante possível.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="a8aaf-156">Consulte as instruções detalhadas do cenário mais adiante neste tópico para obter exemplos usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="a8aaf-157">Há várias maneiras de configurar e hospedar serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="a8aaf-158">Esse é apenas um exemplo, conhecido como "auto-hospedado".</span><span class="sxs-lookup"><span data-stu-id="a8aaf-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="a8aaf-159">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-159">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a8aaf-160">Como: Definir um contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="a8aaf-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="a8aaf-161">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a8aaf-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="a8aaf-162">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="a8aaf-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="a8aaf-163">Comparação de implementação do cliente</span><span class="sxs-lookup"><span data-stu-id="a8aaf-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="a8aaf-164">Criando um cliente no .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="a8aaf-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="a8aaf-165">Depois que um objeto de servidor de comunicação remota do .NET tiver sido disponibilizado, ele poderá ser consumido por clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="a8aaf-166">A instância RemotingServer retornada de Activator. GetObject () é conhecida como "proxy transparente".</span><span class="sxs-lookup"><span data-stu-id="a8aaf-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="a8aaf-167">Ele implementa a API pública para o tipo RemotingServer no cliente, mas todos os métodos chamam o objeto Server em execução em um processo ou computador diferente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="a8aaf-168">Criando um cliente no WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="a8aaf-169">A etapa equivalente no WCF envolve o uso de uma fábrica de canais para criar o proxy explicitamente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="a8aaf-170">Como a comunicação remota, o objeto proxy pode ser usado para invocar operações no servidor, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a8aaf-171">Este exemplo mostra a programação no nível do canal porque ele é mais semelhante ao exemplo de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="a8aaf-172">Também está disponível a abordagem **Adicionar referência de serviço** no Visual Studio que gera código para simplificar a programação do cliente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="a8aaf-173">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-173">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a8aaf-174">Programação de nível de canal do cliente</span><span class="sxs-lookup"><span data-stu-id="a8aaf-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="a8aaf-175">Como: Adicionar, atualizar ou remover uma referência de serviço</span><span class="sxs-lookup"><span data-stu-id="a8aaf-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="a8aaf-176">Uso de serialização</span><span class="sxs-lookup"><span data-stu-id="a8aaf-176">Serialization Usage</span></span>  
 <span data-ttu-id="a8aaf-177">Tanto a comunicação remota do .NET quanto o WCF usam a serialização para enviar objetos entre o cliente e o servidor, mas diferem nessas maneiras importantes:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="a8aaf-178">Eles usam serializadores e convenções diferentes para indicar o que serializar.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="a8aaf-179">A comunicação remota do .NET dá suporte à serialização "por referência" que permite o acesso de método ou propriedade em uma camada para executar o código na outra camada, que está entre limites de segurança.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="a8aaf-180">Esse recurso expõe vulnerabilidades de segurança e é um dos principais motivos pelos quais os pontos de extremidade de comunicação remota nunca devem ser expostos a clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="a8aaf-181">A serialização usada pela comunicação remota é opcional (exclua explicitamente o que não serializar) e a serialização do WCF é opcional (marque explicitamente quais membros serão serializados).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="a8aaf-182">Serialização na comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="a8aaf-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="a8aaf-183">O .NET Remoting dá suporte a duas maneiras de serializar e desserializar objetos entre o cliente e o servidor:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="a8aaf-184">*Por valor* – os valores do objeto são serializados entre limites de camada e uma nova instância desse objeto é criada na outra camada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="a8aaf-185">Todas as chamadas para métodos ou Propriedades dessa nova instância são executadas apenas localmente e não afetam o objeto ou a camada original.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="a8aaf-186">*Por referência* – uma "referência de objeto" especial é serializada entre limites de camada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="a8aaf-187">Quando uma camada interage com métodos ou propriedades desse objeto, ela se comunica de volta ao objeto original na camada original.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="a8aaf-188">Objetos de referência podem fluir em qualquer direção – servidor para cliente ou cliente para servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="a8aaf-189">Tipos de valor em comunicação remota são marcados com o atributo [Serializable] ou implementam ISerializable, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="a8aaf-190">Tipos de referência derivam da classe MarshalByRefObject, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="a8aaf-191">É extremamente importante entender as implicações dos objetos por referência de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="a8aaf-192">Se qualquer camada (cliente ou servidor) enviar um objeto por referência para a outra camada, todas as chamadas de método executarão novamente a camada que possui o objeto.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="a8aaf-193">Por exemplo, um cliente que chama métodos em um objeto por referência retornado pelo servidor executará o código no servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="a8aaf-194">Da mesma forma, um servidor que chama métodos em um objeto por referência fornecido pelo cliente executará o código de volta no cliente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="a8aaf-195">Por esse motivo, o uso da comunicação remota do .NET é recomendado somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="a8aaf-196">Expor um ponto de extremidade de comunicação remota do .NET público para clientes não confiáveis tornará um servidor de comunicação remota vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="a8aaf-197">Serialização no WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-197">Serialization in WCF</span></span>  
 <span data-ttu-id="a8aaf-198">O WCF dá suporte apenas à serialização de valor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="a8aaf-199">A maneira mais comum de definir um tipo para troca entre cliente e servidor é como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
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
  
 <span data-ttu-id="a8aaf-200">O atributo [DataContract] identifica esse tipo como um que pode ser serializado e desserializado entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="a8aaf-201">O atributo [DataMember] identifica as propriedades individuais ou os campos a serem serializados.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="a8aaf-202">Quando o WCF envia um objeto entre as camadas, ele serializa apenas os valores e cria uma nova instância do objeto na outra camada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="a8aaf-203">Todas as interações com os valores do objeto ocorrem somente localmente – elas não se comunicam com a outra camada da forma como os objetos de referência de comunicação remota do .NET fazem.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="a8aaf-204">Para obter mais informações, consulte [serialização e](./feature-details/serialization-and-deserialization.md)desserialização.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-204">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="a8aaf-205">Recursos de manipulação de exceção</span><span class="sxs-lookup"><span data-stu-id="a8aaf-205">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="a8aaf-206">Exceções na comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="a8aaf-206">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="a8aaf-207">As exceções geradas por um servidor remoto são serializadas, enviadas ao cliente e lançadas localmente no cliente, como qualquer outra exceção.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-207">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="a8aaf-208">As exceções personalizadas podem ser criadas por meio da subclasse do tipo de exceção e de sua marcação com [Serializable].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-208">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="a8aaf-209">A maioria das exceções de estrutura já está marcada dessa forma, permitindo que a maioria seja lançada pelo servidor, serializada e relançada no cliente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-209">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="a8aaf-210">Embora esse design seja conveniente durante o desenvolvimento, as informações do lado do servidor podem ser inadvertidamente divulgadas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-210">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="a8aaf-211">Esse é um dos muitos motivos pelos quais a comunicação remota deve ser usada somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-211">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="a8aaf-212">Exceções e falhas no WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-212">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="a8aaf-213">O WCF não permite que tipos de exceção arbitrárias sejam retornados do servidor para o cliente, pois isso pode levar à divulgação inadvertida de informações.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-213">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="a8aaf-214">Se uma operação de serviço lançar uma exceção inesperada, ela fará com que uma FaultException de uso geral seja gerada no cliente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-214">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="a8aaf-215">Essa exceção não carrega nenhuma informação por quê ou onde o problema ocorreu, e para alguns aplicativos isso é suficiente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-215">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="a8aaf-216">Os aplicativos que precisam comunicar informações de erro mais avançadas para o cliente fazem isso definindo um contrato de falha.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-216">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="a8aaf-217">Para fazer isso, primeiro crie um tipo [DataContract] para transportar as informações de falha.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-217">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
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
  
 <span data-ttu-id="a8aaf-218">Especifique o contrato de falha a ser usado para cada operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-218">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="a8aaf-219">O servidor relata as condições de erro lançando uma FaultException.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-219">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="a8aaf-220">E sempre que o cliente fizer uma solicitação ao servidor, ele poderá detectar falhas como exceções normais.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-220">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
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
  
 <span data-ttu-id="a8aaf-221">Para obter mais informações sobre contratos de falha <xref:System.ServiceModel.FaultException>, consulte.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-221">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="a8aaf-222">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="a8aaf-222">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="a8aaf-223">Segurança na comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="a8aaf-223">Security in .NET Remoting</span></span>  
 <span data-ttu-id="a8aaf-224">Alguns canais de comunicação remota do .NET dão suporte a recursos de segurança como autenticação e criptografia na camada de canal (IPC e TCP).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-224">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="a8aaf-225">O canal HTTP depende do Serviços de Informações da Internet (IIS) para autenticação e criptografia.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-225">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="a8aaf-226">Apesar desse suporte, você deve considerar o .NET Remoting um protocolo de comunicação não seguro e usá-lo somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-226">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="a8aaf-227">Nunca exponha um ponto de extremidade de comunicação remota pública para a Internet ou clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-227">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="a8aaf-228">Segurança no WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-228">Security in WCF</span></span>  
 <span data-ttu-id="a8aaf-229">O WCF foi projetado tendo em mente a segurança, em parte para abordar os tipos de vulnerabilidades encontrados na comunicação remota do .NET.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-229">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="a8aaf-230">O WCF oferece segurança no nível de transporte e de mensagem e oferece muitas opções de autenticação, autorização, criptografia e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-230">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="a8aaf-231">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-231">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a8aaf-232">Segurança</span><span class="sxs-lookup"><span data-stu-id="a8aaf-232">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="a8aaf-233">Diretrizes de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-233">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="a8aaf-234">Migrando para o WCF</span><span class="sxs-lookup"><span data-stu-id="a8aaf-234">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="a8aaf-235">Por que migrar da comunicação remota para o WCF?</span><span class="sxs-lookup"><span data-stu-id="a8aaf-235">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="a8aaf-236">**O .NET Remoting é um produto herdado.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-236">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="a8aaf-237">Conforme descrito em [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), ele é considerado um produto herdado e não é recomendado para um novo desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-237">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="a8aaf-238">O WCF ou o ASP.NET Web API são recomendados para aplicativos novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-238">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="a8aaf-239">**O WCF usa padrões de plataforma cruzada.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-239">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="a8aaf-240">O WCF foi projetado com a interoperabilidade entre plataformas em mente e dá suporte a muitos padrões do setor (SOAP, WS-Security, WS-Trust, etc.).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-240">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="a8aaf-241">Um serviço WCF pode interoperar com clientes em execução em sistemas operacionais diferentes do Windows.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-241">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="a8aaf-242">A comunicação remota foi projetada principalmente para ambientes em que ambos os aplicativos cliente e servidor são executados usando o .NET Framework em um sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-242">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
- <span data-ttu-id="a8aaf-243">**O WCF tem segurança interna.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-243">**WCF has built-in security.**</span></span> <span data-ttu-id="a8aaf-244">O WCF foi projetado tendo em mente a segurança e oferece muitas opções de autenticação, segurança de nível de transporte, segurança de nível de mensagem, etc. A comunicação remota foi projetada para tornar mais fácil para os aplicativos interoperarem, mas não foram projetados para serem seguros em ambientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-244">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="a8aaf-245">O WCF foi projetado para funcionar em ambientes confiáveis e não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-245">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="a8aaf-246">Recomendações de migração</span><span class="sxs-lookup"><span data-stu-id="a8aaf-246">Migration Recommendations</span></span>  
 <span data-ttu-id="a8aaf-247">A seguir estão as etapas recomendadas para migrar do .NET Remoting para o WCF:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-247">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="a8aaf-248">**Crie o contrato de serviço.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-248">**Create the service contract.**</span></span> <span data-ttu-id="a8aaf-249">Defina os tipos de interface de serviço e marque-os com o atributo [ServiceContract]. Marque todos os métodos aos quais os clientes terão permissão para chamar [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-249">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="a8aaf-250">**Crie o contrato de dados.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-250">**Create the data contract.**</span></span> <span data-ttu-id="a8aaf-251">Defina os tipos de dados que serão trocados entre o servidor e o cliente e marque-os com o atributo [DataContract].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-251">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="a8aaf-252">Marque todos os campos e propriedades que o cliente terá permissão para usar com [DataMember].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-252">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="a8aaf-253">**Crie o contrato de falha (opcional).**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-253">**Create the fault contract (optional).**</span></span> <span data-ttu-id="a8aaf-254">Crie os tipos que serão trocados entre o servidor e o cliente quando forem encontrados erros.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-254">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="a8aaf-255">Marque esses tipos com [DataContract] e [DataMember] para torná-los serializáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-255">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="a8aaf-256">Para todas as operações de serviço que você marcou com [OperationContract], também marque-as com [FaultContract] para indicar quais erros podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-256">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="a8aaf-257">**Configure e hospede o serviço.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-257">**Configure and host the service.**</span></span> <span data-ttu-id="a8aaf-258">Depois que o contrato de serviço tiver sido criado, a próxima etapa será configurar uma associação para expor o serviço em um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-258">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="a8aaf-259">Para obter mais informações, [consulte pontos de extremidade: Endereços, associações e contratos](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-259">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="a8aaf-260">Depois que um aplicativo de comunicação remota é migrado para o WCF, ainda é importante remover dependências na comunicação remota do .NET.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-260">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="a8aaf-261">Isso garante que todas as vulnerabilidades de comunicação remota sejam removidas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-261">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="a8aaf-262">Essas etapas incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-262">These steps include the following:</span></span>  
  
- <span data-ttu-id="a8aaf-263">**Descontinuar o uso de MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-263">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="a8aaf-264">O tipo MarshalByRefObject existe somente para comunicação remota e não é usado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-264">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="a8aaf-265">Qualquer tipo de aplicativo que a subclasse MarshalByRefObject deve ser removida ou alterada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-265">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="a8aaf-266">**Descontinue o uso de [Serializable] e ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-266">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="a8aaf-267">O atributo [Serializable] e a interface ISerializable foram originalmente projetados para serializar tipos em ambientes confiáveis e são usados pela comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-267">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="a8aaf-268">A serialização do WCF depende dos tipos marcados com [DataContract] e [DataMember].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-268">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="a8aaf-269">Os tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não para usar ISerializable ou [Serializable].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-269">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="a8aaf-270">Cenários de migração</span><span class="sxs-lookup"><span data-stu-id="a8aaf-270">Migration Scenarios</span></span>  
 <span data-ttu-id="a8aaf-271">Agora, vejamos como realizar os seguintes cenários comuns de comunicação remota no WCF:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-271">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="a8aaf-272">O servidor retorna um objeto por valor para o cliente</span><span class="sxs-lookup"><span data-stu-id="a8aaf-272">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="a8aaf-273">O servidor retorna um objeto por referência ao cliente</span><span class="sxs-lookup"><span data-stu-id="a8aaf-273">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="a8aaf-274">O cliente envia um objeto por valor para o servidor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-274">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8aaf-275">O envio de um objeto por referência do cliente para o servidor não é permitido no WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-275">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="a8aaf-276">Ao ler esses cenários, suponha que nossas interfaces de linha de base para .NET Remoting sejam semelhantes ao exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-276">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="a8aaf-277">A implementação de comunicação remota do .NET não é importante aqui porque queremos ilustrar apenas como usar o WCF para implementar a funcionalidade equivalente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-277">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="a8aaf-278">Cenário 1: O serviço retorna um objeto por valor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-278">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="a8aaf-279">Este cenário demonstra um servidor que retorna um objeto ao cliente por valor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-279">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="a8aaf-280">O WCF sempre retorna objetos do servidor por valor, portanto, as etapas a seguir descrevem simplesmente como criar um serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-280">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="a8aaf-281">Comece definindo uma interface pública para o serviço WCF e marque-a com o atributo [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-281">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="a8aaf-282">Usamos [OperationContract] para identificar os métodos do lado do servidor que nosso cliente chamará.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-282">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
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
  
2. <span data-ttu-id="a8aaf-283">A próxima etapa é criar o contrato de dados para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-283">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="a8aaf-284">Fazemos isso criando classes (não interfaces) marcadas com o atributo [DataContract].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-284">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="a8aaf-285">As propriedades ou os campos individuais que queremos que sejam visíveis para o cliente e para o servidor são marcados com [DataMember].</span><span class="sxs-lookup"><span data-stu-id="a8aaf-285">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="a8aaf-286">Se quisermos que tipos derivados sejam permitidos, devemos usar o atributo [KnownType] para identificá-los.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-286">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="a8aaf-287">Os únicos tipos do WCF permitirão que sejam serializados ou desserializados para esse serviço são aqueles na interface de serviço e esses "tipos conhecidos".</span><span class="sxs-lookup"><span data-stu-id="a8aaf-287">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="a8aaf-288">A tentativa de trocar qualquer outro tipo que não esteja nesta lista será rejeitada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-288">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
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
  
3. <span data-ttu-id="a8aaf-289">Em seguida, fornecemos a implementação para a interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-289">Next, we provide the implementation for the service interface.</span></span>  
  
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
  
4. <span data-ttu-id="a8aaf-290">Para executar o serviço WCF, precisamos declarar um ponto de extremidade que expõe essa interface de serviço em uma URL específica usando uma associação WCF específica.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-290">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="a8aaf-291">Isso normalmente é feito adicionando as seções a seguir ao arquivo Web. config do projeto de servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-291">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
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
  
5. <span data-ttu-id="a8aaf-292">O serviço WCF pode então ser iniciado com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-292">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="a8aaf-293">Quando esse ServiceHost é iniciado, ele usa o arquivo Web. config para estabelecer o contrato, a associação e o ponto de extremidade apropriados.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-293">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="a8aaf-294">Para obter mais informações sobre arquivos de configuração, consulte Configurando [serviços usando arquivos de configuração](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-294">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="a8aaf-295">Esse estilo de inicialização do servidor é conhecido como hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-295">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="a8aaf-296">Para saber mais sobre outras opções de Hospedagem de serviços WCF, consulte [serviços de hospedagem](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-296">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="a8aaf-297">O app. config do projeto do cliente deve declarar informações de associação correspondentes para o ponto de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-297">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="a8aaf-298">A maneira mais fácil de fazer isso no Visual Studio é usar **Adicionar referência de serviço**, que atualizará automaticamente o arquivo app. config.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-298">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="a8aaf-299">Como alternativa, essas mesmas alterações podem ser adicionadas manualmente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-299">Alternatively, these same changes can be added manually.</span></span>  
  
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
  
     <span data-ttu-id="a8aaf-300">Para obter mais informações sobrecomo usar Adicionar referência de serviço [, consulte Como: Adicionar, atualizar ou remover uma referência](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)de serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-300">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="a8aaf-301">Agora, podemos chamar o serviço WCF do cliente.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-301">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="a8aaf-302">Fazemos isso criando uma fábrica de canais para esse serviço, solicitando-o por um canal e chamando diretamente o método que desejamos nesse canal.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-302">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="a8aaf-303">Podemos fazer isso porque o canal implementa a interface do serviço e manipula a lógica de solicitação/resposta subjacente para nós.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-303">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="a8aaf-304">O valor de retorno dessa chamada de método é a cópia desserializada da resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-304">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="a8aaf-305">Os objetos retornados pelo WCF do servidor para o cliente são sempre por valor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-305">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="a8aaf-306">Os objetos são cópias desserializadas dos dados enviados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-306">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="a8aaf-307">O cliente pode chamar métodos nessas cópias locais sem nenhum perigo de invocar o código do servidor por meio de retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-307">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="a8aaf-308">Cenário 2: O servidor retorna um objeto por referência</span><span class="sxs-lookup"><span data-stu-id="a8aaf-308">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="a8aaf-309">Este cenário demonstra o servidor que fornece um objeto ao cliente por referência.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-309">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="a8aaf-310">Na comunicação remota do .NET, isso é manipulado automaticamente para qualquer tipo derivado de MarshalByRefObject, que é serializado por referência.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-310">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="a8aaf-311">Um exemplo desse cenário é permitir que vários clientes tenham objetos do lado do servidor de sessão independentes.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-311">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="a8aaf-312">Como mencionado anteriormente, os objetos retornados por um serviço WCF são sempre por valor, portanto, não há nenhum equivalente direto de um objeto por referência, mas é possível obter algo semelhante à semântica por referência usando um <xref:System.ServiceModel.EndpointAddress10> objeto.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-312">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="a8aaf-313">Esse é um objeto de valor serializável que pode ser usado pelo cliente para obter uma sessão por objeto de referência no servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-313">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="a8aaf-314">Isso habilita o cenário de ter vários clientes com objetos do lado do servidor de sessão independentes.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-314">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="a8aaf-315">Primeiro, precisamos definir um contrato de serviço do WCF que corresponda ao próprio objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-315">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
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
    > <span data-ttu-id="a8aaf-316">Observe que o objeto de sessão está marcado com [ServiceContract], tornando-o uma interface de serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-316">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="a8aaf-317">Definir a Propriedade SessionMode indica que será um serviço de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-317">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="a8aaf-318">No WCF, uma sessão é uma maneira de correlacionar várias mensagens enviadas entre dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-318">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="a8aaf-319">Isso significa que, depois que um cliente obtiver uma conexão para esse serviço, uma sessão será estabelecida entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-319">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="a8aaf-320">O cliente usará uma única instância exclusiva do objeto do lado do servidor para todas as interações dele nessa única sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-320">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="a8aaf-321">Em seguida, precisamos fornecer a implementação dessa interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-321">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="a8aaf-322">Ao denotar isso com [serviceInstance] e definir o InstanceContextmode, dizemos ao WCF que desejamos usar uma instância exclusiva desse tipo para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-322">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
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
  
3. <span data-ttu-id="a8aaf-323">Agora precisamos de uma maneira de obter uma instância desse objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-323">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="a8aaf-324">Fazemos isso criando outra interface de serviço do WCF que retorna um objeto EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-324">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="a8aaf-325">Essa é uma forma serializável de um ponto de extremidade que o cliente pode usar para criar o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-325">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="a8aaf-326">E implementamos este serviço WCF:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-326">And we implement this WCF service:</span></span>  
  
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
  
     <span data-ttu-id="a8aaf-327">Essa implementação mantém uma fábrica de canais única para criar objetos de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-327">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="a8aaf-328">Quando GetInstanceAddress () é chamado, ele cria um canal e cria um objeto EndpointAddress10 que aponta efetivamente para o endereço remoto associado a esse canal.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-328">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="a8aaf-329">EndpointAddress10 é simplesmente um tipo de dados que pode ser retornado ao cliente por valor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-329">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="a8aaf-330">Precisamos modificar o arquivo de configuração do servidor fazendo as duas ações a seguir, conforme mostrado no exemplo abaixo:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-330">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="a8aaf-331">Declare um \<cliente > seção que descreve o ponto de extremidade para o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-331">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="a8aaf-332">Isso é necessário porque o servidor também atua como um cliente nessa situação.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-332">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="a8aaf-333">Declare pontos de extremidade para a fábrica e o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-333">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="a8aaf-334">Isso é necessário para permitir que o cliente se comunique com os pontos de extremidade de serviço para adquirir o EndpointAddress10 e criar o canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-334">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
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
  
     <span data-ttu-id="a8aaf-335">E, em seguida, podemos iniciar esses serviços:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-335">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="a8aaf-336">Configuramos o cliente declarando esses mesmos pontos de extremidade no arquivo app. config do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-336">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
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
  
6. <span data-ttu-id="a8aaf-337">Para criar e usar esse objeto de sessão, o cliente deve executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="a8aaf-337">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="a8aaf-338">Crie um canal para o serviço ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-338">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="a8aaf-339">Use esse canal para invocar esse serviço para obter um EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-339">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="a8aaf-340">Use o EndpointAddress10 para criar um canal para obter um objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-340">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="a8aaf-341">Interaja com o objeto de sessão para demonstrar que ele permanece a mesma instância em várias chamadas.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-341">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
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
  
 <span data-ttu-id="a8aaf-342">O WCF sempre retorna objetos por valor, mas é possível dar suporte ao equivalente de semântica por referência por meio do uso de EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-342">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="a8aaf-343">Isso permite que o cliente solicite uma instância de serviço WCF de sessão, após a qual ela pode interagir com ela, como qualquer outro serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-343">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="a8aaf-344">Cenário 3: O cliente envia um servidor a uma instância por valor</span><span class="sxs-lookup"><span data-stu-id="a8aaf-344">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="a8aaf-345">Este cenário demonstra o cliente que envia uma instância de objeto não primitivo para o servidor por valor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-345">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="a8aaf-346">Como o WCF só envia objetos por valor, esse cenário demonstra o uso normal do WCF.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-346">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="a8aaf-347">Use o mesmo serviço WCF do cenário 1.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-347">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="a8aaf-348">Use o cliente para criar um novo objeto por valor (cliente), crie um canal para se comunicar com o serviço ICustomerService e envie o objeto para ele.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-348">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
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
  
     <span data-ttu-id="a8aaf-349">O objeto Customer será serializado e enviado para o servidor, onde será desserializado em uma nova cópia desse objeto.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-349">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a8aaf-350">Esse código também ilustra o envio de um tipo derivado (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-350">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="a8aaf-351">A interface de serviço espera um objeto de cliente, mas o atributo [KnownType] na classe Customer indicou PremiumCustomer também foi permitido.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-351">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="a8aaf-352">O WCF falhará em qualquer tentativa de serializar ou desserializar qualquer outro tipo por meio dessa interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-352">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="a8aaf-353">As trocas de dados WCF normais são por valor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-353">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="a8aaf-354">Isso garante que a invocação de métodos em um desses objetos de dados seja executada apenas localmente – ele não invocará o código na outra camada.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-354">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="a8aaf-355">Embora seja possível obter algo como objetos de referência retornados *do* servidor, não é possível que um cliente passe um objeto por referência *para* o servidor.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-355">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="a8aaf-356">Um cenário que requer uma conversa de ida e volta entre o cliente e o servidor pode ser obtido no WCF usando um serviço duplex.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-356">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="a8aaf-357">Para obter mais informações, consulte [duplex Services](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8aaf-357">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="a8aaf-358">Resumo</span><span class="sxs-lookup"><span data-stu-id="a8aaf-358">Summary</span></span>  
 <span data-ttu-id="a8aaf-359">A comunicação remota do .NET é uma estrutura de comunicação destinada a ser usada somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-359">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="a8aaf-360">Ele é um produto herdado e tem suporte apenas para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-360">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="a8aaf-361">Ele não deve ser usado para criar novos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-361">It should not be used to build new applications.</span></span> <span data-ttu-id="a8aaf-362">Por outro lado, o WCF foi projetado tendo em mente a segurança e é recomendado para aplicativos novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-362">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="a8aaf-363">A Microsoft recomenda que os aplicativos de comunicação remota existentes sejam migrados para usar o WCF ou ASP.NET Web API em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-363">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
