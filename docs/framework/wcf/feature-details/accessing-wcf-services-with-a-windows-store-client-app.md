---
title: "Acessando os serviços WCF com um aplicativo cliente da Windows Store"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a1d30258063063cd4b91e328fc39e961ecb4425
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="ff34c-102">Acessando os serviços WCF com um aplicativo cliente da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="ff34c-103">O Windows 8 apresenta um novo tipo de aplicativos chamados aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ff34c-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="ff34c-104">Esses aplicativos são criados em torno de uma interface de tela sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="ff34c-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="ff34c-105">O .NET Framework 4.5 permite que aplicativos da Windows Store chamem serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="ff34c-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="ff34c-106">Suporte do WCF em aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="ff34c-107">Um subconjunto da funcionalidade do WCF está disponível a partir de um aplicativo da Windows Store. Consulte as seções a seguir para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="ff34c-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff34c-108">Use as APIs de agregação de WinRT em vez dessas expostas pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="ff34c-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="ff34c-109">Para obter mais informações, consulte [API de distribuição de WinRT](http://go.microsoft.com/fwlink/?LinkId=236265)</span><span class="sxs-lookup"><span data-stu-id="ff34c-109">For more information see, [WinRT Syndication API](http://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ff34c-110">Não há suporte para usar Adicionar Referência de Serviço para adicionar uma referência ao serviço Web para um componente de Tempo de Execução do Windows.</span><span class="sxs-lookup"><span data-stu-id="ff34c-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="ff34c-111">Associações com suporte</span><span class="sxs-lookup"><span data-stu-id="ff34c-111">Supported Bindings</span></span>  
 <span data-ttu-id="ff34c-112">As seguintes associações do WCF têm suporte em aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="ff34c-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="ff34c-113">Os seguintes elementos de associação têm suporte em aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="ff34c-114">Codificações de texto e binários têm suporte.</span><span class="sxs-lookup"><span data-stu-id="ff34c-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="ff34c-115">Todos os modos de transferência de WCF têm suporte.</span><span class="sxs-lookup"><span data-stu-id="ff34c-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="ff34c-116">Para obter mais informações, consulte [Streaming de transferência de mensagens](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="ff34c-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="ff34c-117">Adicionar Referência de Serviço</span><span class="sxs-lookup"><span data-stu-id="ff34c-117">Add Service Reference</span></span>  
 <span data-ttu-id="ff34c-118">Para chamar um serviço WCF de um aplicativo da Windows Store, use o recurso Adicionar Referência de Serviço do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ff34c-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="ff34c-119">Você observará algumas alterações na funcionalidade de Adicionar Referência de Serviço quando forem feitas dentro de um aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ff34c-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="ff34c-120">Nenhum arquivo de configuração é gerado primeiro.</span><span class="sxs-lookup"><span data-stu-id="ff34c-120">First no configuration file is generated.</span></span> <span data-ttu-id="ff34c-121">Os aplicativos da Windows Store não usam arquivos de configuração. Eles devem ser configurados no código.</span><span class="sxs-lookup"><span data-stu-id="ff34c-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="ff34c-122">Este código de configuração pode ser localizado no arquivo References.cs gerado por Adicionar Referência de Serviço.</span><span class="sxs-lookup"><span data-stu-id="ff34c-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="ff34c-123">Para ver esse arquivo, certifique-se de selecionar "Mostrar todos os arquivos" no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="ff34c-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="ff34c-124">O arquivo será localizado nos nós de Referências de Serviço e, em seguida, Reference.svcmap dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="ff34c-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="ff34c-125">Todas as operações geradas para os serviços WCF dentro de um aplicativo da Windows Store serão assíncronas usando o padrão assíncrono baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="ff34c-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="ff34c-126">Para obter mais informações, consulte [padrão assíncrono baseado em tarefa](http://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="ff34c-126">For more information, see [Task-based Asynchronous Pattern](http://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="ff34c-127">Como a configuração agora é gerada no código, todas as alterações feitas no arquivo Reference.cs serão substituídas toda vez que a referência do serviço for atualizada.</span><span class="sxs-lookup"><span data-stu-id="ff34c-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="ff34c-128">Para solucionar essa situação, o código de configuração é gerado dentro de um método parcial, que você pode implementar em sua classe de proxy cliente.</span><span class="sxs-lookup"><span data-stu-id="ff34c-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="ff34c-129">O método parcial é declarado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ff34c-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="ff34c-130">Você pode implementar esse método parcial e alterar a associação ou o ponto de extremidade em sua classe de proxy cliente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ff34c-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="ff34c-131">Serialização</span><span class="sxs-lookup"><span data-stu-id="ff34c-131">Serialization</span></span>  
 <span data-ttu-id="ff34c-132">Os seguintes serializadores têm suporte em aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="ff34c-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1.  <span data-ttu-id="ff34c-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="ff34c-133">DataContractSerializer</span></span>  
  
2.  <span data-ttu-id="ff34c-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="ff34c-134">DataContractJsonSerializer</span></span>  
  
3.  <span data-ttu-id="ff34c-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="ff34c-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ff34c-136">XmlDictionaryWriter.Write(DateTime) grava agora o objeto DateTime como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ff34c-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="ff34c-137">Segurança</span><span class="sxs-lookup"><span data-stu-id="ff34c-137">Security</span></span>  
 <span data-ttu-id="ff34c-138">Os seguintes modelos de segurança têm suporte em aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-138">The following security modes are supported in Windows Store applications</span></span>  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 <span data-ttu-id="ff34c-139">Os seguintes tipos de credenciais de clientes têm suporte em aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-139">The following client credential types are supported in Windows Store applications</span></span>  
  
1.  <span data-ttu-id="ff34c-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ff34c-140">None</span></span>  
  
2.  <span data-ttu-id="ff34c-141">Basic</span><span class="sxs-lookup"><span data-stu-id="ff34c-141">Basic</span></span>  
  
3.  <span data-ttu-id="ff34c-142">Digest</span><span class="sxs-lookup"><span data-stu-id="ff34c-142">Digest</span></span>  
  
4.  <span data-ttu-id="ff34c-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="ff34c-143">Negotiate</span></span>  
  
5.  <span data-ttu-id="ff34c-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="ff34c-144">NTLM</span></span>  
  
6.  <span data-ttu-id="ff34c-145">Windows</span><span class="sxs-lookup"><span data-stu-id="ff34c-145">Windows</span></span>  
  
7.  <span data-ttu-id="ff34c-146">Username (Segurança de Mensagem)</span><span class="sxs-lookup"><span data-stu-id="ff34c-146">Username (Message Security)</span></span>  
  
8.  <span data-ttu-id="ff34c-147">Windows (Segurança de Transporte)</span><span class="sxs-lookup"><span data-stu-id="ff34c-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="ff34c-148">Para que os aplicativos da Windows Store acessem e enviem credenciais padrão do Windows, você deverá habilitar essa funcionalidade dentro do arquivo Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="ff34c-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="ff34c-149">Abrir este arquivo e selecione a guia de recursos e selecione "Credenciais padrão do Windows".</span><span class="sxs-lookup"><span data-stu-id="ff34c-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="ff34c-150">Isso permite que o aplicativo se conecte aos recursos de intranet que exigem credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="ff34c-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff34c-151">Para aplicativos da Windows Store fazer chamadas de várias máquinas, você deve habilitar o recurso de outra chamado "Rede de casa/do trabalho".</span><span class="sxs-lookup"><span data-stu-id="ff34c-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="ff34c-152">Essa configuração também está no arquivo Package.appmanifest na guia Recursos. Marque a caixa de seleção Home/Work Networking.</span><span class="sxs-lookup"><span data-stu-id="ff34c-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="ff34c-153">Isso concede o acesso de entrada e saída do aplicativo às redes locais confiáveis do usuário como casa e trabalho.</span><span class="sxs-lookup"><span data-stu-id="ff34c-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="ff34c-154">As portas críticas de entrada são sempre bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="ff34c-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="ff34c-155">Para acessar serviços na Internet, é necessário habilitar o recurso Internet (Cliente).</span><span class="sxs-lookup"><span data-stu-id="ff34c-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="ff34c-156">Diversos</span><span class="sxs-lookup"><span data-stu-id="ff34c-156">Misc</span></span>  
 <span data-ttu-id="ff34c-157">O uso das seguintes classes tem suporte para aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="ff34c-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="ff34c-158">Definindo contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="ff34c-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="ff34c-159">É recomendável somente a definição de operações de serviço assíncronas usando o padrão assíncrono baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="ff34c-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="ff34c-160">Isso garante que os aplicativos da Windows Store permaneçam respondendo ao chamar uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="ff34c-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ff34c-161">Embora nenhuma exceção seja gerada se você definir uma operação síncrona, é altamente recomendável definir apenas operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="ff34c-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="ff34c-162">Chamando serviços WCF de aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="ff34c-163">Como mencionado acima, todas as configurações devem ser feitas no código no método GetBindingForEndpoint na classe proxy gerada.</span><span class="sxs-lookup"><span data-stu-id="ff34c-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="ff34c-164">Chamar uma operação de serviço é feito da mesma maneira que chamar qualquer método assíncrono baseado em tarefas conforme mostrado no seguinte trecho de código.</span><span class="sxs-lookup"><span data-stu-id="ff34c-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="ff34c-165">Observe o uso da palavra-chave async no método que faz a chamada assíncrona e da palavra-chave await ao chamar o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="ff34c-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff34c-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff34c-166">See Also</span></span>  
 [<span data-ttu-id="ff34c-167">WCF no Blog de aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-167">WCF in Windows Store Apps Blog</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [<span data-ttu-id="ff34c-168">Segurança e clientes do WCF Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-168">WCF Windows Store Clients and Security</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [<span data-ttu-id="ff34c-169">Aplicativos da Windows Store e chamadas de várias máquinas</span><span class="sxs-lookup"><span data-stu-id="ff34c-169">Windows Store Apps and Cross Machine Calls</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="ff34c-170">Chamar um serviço WCF implantado no Azure de um aplicativo da Windows Store</span><span class="sxs-lookup"><span data-stu-id="ff34c-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="ff34c-171">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="ff34c-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="ff34c-172">[Bindings](../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="ff34c-172">[Bindings](../../../../docs/framework/wcf/bindings.md)</span></span>
