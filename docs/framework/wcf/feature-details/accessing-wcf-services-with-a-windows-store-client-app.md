---
title: Acessando os serviços WCF com um aplicativo cliente da Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: d575907feea3d831b7e6f69410c8d4647e6ac95d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557951"
---
# <a name="access-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="b147a-102">Acessar serviços WCF com um aplicativo cliente da Windows Store</span><span class="sxs-lookup"><span data-stu-id="b147a-102">Access WCF Services with a Windows Store Client App</span></span>

<span data-ttu-id="b147a-103">O Windows 8 apresenta um novo tipo de aplicativos chamados aplicativos da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="b147a-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="b147a-104">Esses aplicativos são criados em torno de uma interface de tela sensível ao toque.</span><span class="sxs-lookup"><span data-stu-id="b147a-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="b147a-105">O .NET Framework 4.5 permite que aplicativos da Windows Store chamem serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="b147a-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="b147a-106">Suporte do WCF em aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="b147a-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="b147a-107">Um subconjunto da funcionalidade do WCF está disponível a partir de um aplicativo da Windows Store. Consulte as seções a seguir para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="b147a-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b147a-108">Use as APIs de agregação de WinRT em vez dessas expostas pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="b147a-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="b147a-109">Para obter mais informações, consulte [API de distribuição do WinRT](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="b147a-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b147a-110">Não há suporte para o uso de Adicionar Referência de Serviço para adicionar uma referência de serviço Web a um componente Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="b147a-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn't supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="b147a-111">Associações com suporte</span><span class="sxs-lookup"><span data-stu-id="b147a-111">Supported Bindings</span></span>  
 <span data-ttu-id="b147a-112">As seguintes associações do WCF têm suporte em aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b147a-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="b147a-113">Os seguintes elementos de associação têm suporte em aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="b147a-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="b147a-114">Codificações de texto e binários têm suporte.</span><span class="sxs-lookup"><span data-stu-id="b147a-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="b147a-115">Todos os modos de transferência de WCF têm suporte.</span><span class="sxs-lookup"><span data-stu-id="b147a-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="b147a-116">Para obter mais informações, consulte [streaming de transferência de mensagens](streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="b147a-116">For more information see, [Streaming Message Transfer](streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="b147a-117">Adicionar Referência de Serviço</span><span class="sxs-lookup"><span data-stu-id="b147a-117">Add Service Reference</span></span>  
 <span data-ttu-id="b147a-118">Para chamar um serviço WCF de um aplicativo da Windows Store, use o recurso Adicionar Referência de Serviço do Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="b147a-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="b147a-119">Você observará algumas alterações na funcionalidade de Adicionar Referência de Serviço quando forem feitas dentro de um aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="b147a-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="b147a-120">Nenhum arquivo de configuração é gerado primeiro.</span><span class="sxs-lookup"><span data-stu-id="b147a-120">First no configuration file is generated.</span></span> <span data-ttu-id="b147a-121">Os aplicativos da Windows Store não usam arquivos de configuração. Eles devem ser configurados no código.</span><span class="sxs-lookup"><span data-stu-id="b147a-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="b147a-122">Este código de configuração pode ser localizado no arquivo References.cs gerado por Adicionar Referência de Serviço.</span><span class="sxs-lookup"><span data-stu-id="b147a-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="b147a-123">Para ver esse arquivo, certifique-se de selecionar "Mostrar todos os arquivos" no Gerenciador de soluções.</span><span class="sxs-lookup"><span data-stu-id="b147a-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="b147a-124">O arquivo será localizado nos nós de Referências de Serviço e, em seguida, Reference.svcmap dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="b147a-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="b147a-125">Todas as operações geradas para os serviços WCF dentro de um aplicativo da Windows Store serão assíncronas usando o padrão assíncrono baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="b147a-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="b147a-126">Para obter mais informações, consulte [tarefas assíncronas – simplificar a programação assíncrona com tarefas](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span><span class="sxs-lookup"><span data-stu-id="b147a-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="b147a-127">Como a configuração agora é gerada no código, todas as alterações feitas no arquivo Reference.cs serão substituídas toda vez que a referência do serviço for atualizada.</span><span class="sxs-lookup"><span data-stu-id="b147a-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="b147a-128">Para solucionar essa situação, o código de configuração é gerado dentro de um método parcial, que você pode implementar em sua classe de proxy cliente.</span><span class="sxs-lookup"><span data-stu-id="b147a-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="b147a-129">O método parcial é declarado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b147a-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="b147a-130">Você pode implementar esse método parcial e alterar a associação ou o ponto de extremidade em sua classe de proxy cliente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b147a-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="b147a-131">Serialização</span><span class="sxs-lookup"><span data-stu-id="b147a-131">Serialization</span></span>  
 <span data-ttu-id="b147a-132">Os seguintes serializadores têm suporte em aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b147a-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="b147a-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="b147a-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="b147a-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="b147a-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="b147a-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b147a-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b147a-136">XmlDictionaryWriter.Write(DateTime) grava agora o objeto DateTime como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b147a-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="b147a-137">Segurança</span><span class="sxs-lookup"><span data-stu-id="b147a-137">Security</span></span>  

<span data-ttu-id="b147a-138">Os seguintes modos de segurança têm suporte em aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b147a-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="b147a-139">Os seguintes tipos de credencial de cliente têm suporte em aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b147a-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="b147a-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b147a-140">None</span></span>  
  
2. <span data-ttu-id="b147a-141">Básico</span><span class="sxs-lookup"><span data-stu-id="b147a-141">Basic</span></span>  
  
3. <span data-ttu-id="b147a-142">Digest</span><span class="sxs-lookup"><span data-stu-id="b147a-142">Digest</span></span>  
  
4. <span data-ttu-id="b147a-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="b147a-143">Negotiate</span></span>  
  
5. <span data-ttu-id="b147a-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="b147a-144">NTLM</span></span>  
  
6. <span data-ttu-id="b147a-145">Windows</span><span class="sxs-lookup"><span data-stu-id="b147a-145">Windows</span></span>  
  
7. <span data-ttu-id="b147a-146">Username (Segurança de Mensagem)</span><span class="sxs-lookup"><span data-stu-id="b147a-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="b147a-147">Windows (Segurança de Transporte)</span><span class="sxs-lookup"><span data-stu-id="b147a-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="b147a-148">Para que os aplicativos da Windows Store acessem e enviem credenciais padrão do Windows, você deverá habilitar essa funcionalidade dentro do arquivo Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="b147a-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="b147a-149">Abra esse arquivo e selecione a guia recursos e selecione "credenciais padrão do Windows".</span><span class="sxs-lookup"><span data-stu-id="b147a-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="b147a-150">Isso permite que o aplicativo se conecte aos recursos de intranet que exigem credenciais de domínio.</span><span class="sxs-lookup"><span data-stu-id="b147a-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b147a-151">Para que os aplicativos da Windows Store façam chamadas entre computadores, você deve habilitar outra funcionalidade chamada "rede doméstica/corporativa".</span><span class="sxs-lookup"><span data-stu-id="b147a-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="b147a-152">Essa configuração também está no arquivo Package. arquivo AppManifest na guia recursos. Selecione a caixa de seleção rede doméstica/trabalho.</span><span class="sxs-lookup"><span data-stu-id="b147a-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="b147a-153">Isso dá ao seu aplicativo acesso de entrada e saída às redes dos locais confiáveis do usuário, como Home e Work.</span><span class="sxs-lookup"><span data-stu-id="b147a-153">This gives your application inbound and outbound access to the networks of the user's trusted places like home and work.</span></span> <span data-ttu-id="b147a-154">As portas críticas de entrada são sempre bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="b147a-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="b147a-155">Para acessar serviços na Internet, é necessário habilitar o recurso Internet (Cliente).</span><span class="sxs-lookup"><span data-stu-id="b147a-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="b147a-156">Diversos</span><span class="sxs-lookup"><span data-stu-id="b147a-156">Misc</span></span>  
 <span data-ttu-id="b147a-157">O uso das seguintes classes tem suporte para aplicativos da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="b147a-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="b147a-158">Definindo contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="b147a-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="b147a-159">É recomendável somente a definição de operações de serviço assíncronas usando o padrão assíncrono baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="b147a-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="b147a-160">Isso garante que os aplicativos da Windows Store permaneçam respondendo ao chamar uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="b147a-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b147a-161">Embora nenhuma exceção seja gerada se você definir uma operação síncrona, é altamente recomendável definir apenas operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="b147a-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="b147a-162">Chamando serviços WCF de aplicativos da Windows Store</span><span class="sxs-lookup"><span data-stu-id="b147a-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="b147a-163">Como mencionado acima, todas as configurações devem ser feitas no código no método GetBindingForEndpoint na classe proxy gerada.</span><span class="sxs-lookup"><span data-stu-id="b147a-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="b147a-164">Chamar uma operação de serviço é feito da mesma maneira que chamar qualquer método assíncrono baseado em tarefas conforme mostrado no seguinte snippet de código.</span><span class="sxs-lookup"><span data-stu-id="b147a-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="b147a-165">Observe o uso da palavra-chave async no método que faz a chamada assíncrona e da palavra-chave await ao chamar o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b147a-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b147a-166">Confira também</span><span class="sxs-lookup"><span data-stu-id="b147a-166">See also</span></span>

- [<span data-ttu-id="b147a-167">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="b147a-167">Programming WCF Security</span></span>](programming-wcf-security.md)
- [<span data-ttu-id="b147a-168">Associações</span><span class="sxs-lookup"><span data-stu-id="b147a-168">Bindings</span></span>](../bindings.md)
