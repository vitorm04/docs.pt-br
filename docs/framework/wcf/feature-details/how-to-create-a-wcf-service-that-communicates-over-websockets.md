---
title: "Como criar um serviço WCF que se comunica por meio de WebSockets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99d091e5ef0998a3818609b7d52ecd62a609eeb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="55f62-102">Como criar um serviço WCF que se comunica por meio de WebSockets</span><span class="sxs-lookup"><span data-stu-id="55f62-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>
<span data-ttu-id="55f62-103">Serviços WCF e os clientes podem usar o <xref:System.ServiceModel.NetHttpBinding> associação para se comunicar por meio de WebSockets.</span><span class="sxs-lookup"><span data-stu-id="55f62-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="55f62-104">O WebSocket será usado quando o <xref:System.ServiceModel.NetHttpBinding> determina o contrato de serviço define um contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="55f62-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="55f62-105">Este tópico descreve como implementar um serviço WCF e um cliente que usa o <xref:System.ServiceModel.NetHttpBinding> para se comunicar por meio de WebSockets.</span><span class="sxs-lookup"><span data-stu-id="55f62-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="55f62-106">Definir o serviço</span><span class="sxs-lookup"><span data-stu-id="55f62-106">Define the Service</span></span>  
  
1.  <span data-ttu-id="55f62-107">Definir um contrato de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="55f62-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="55f62-108">Este contrato será implementado pelo aplicativo cliente para permitir que o serviço enviar mensagens de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="55f62-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2.  <span data-ttu-id="55f62-109">Definir o contrato de serviço e especifique o `IStockQuoteCallback` interface como o contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="55f62-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3.  <span data-ttu-id="55f62-110">Implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="55f62-110">Implement the service contract.</span></span>  
  
    ```  
    public class StockQuoteService : IStockQuoteService  
        {  
            public async Task StartSendingQuotes()  
            {  
                var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
                var random = new Random();  
                double price = 29.00;  
  
                while (((IChannel)callback).State == CommunicationState.Opened)  
                {  
                    await callback.SendQuote("MSFT", price);  
                    price += random.NextDouble();  
                    await Task.Delay(1000);  
                }  
            }  
        }  
    ```  
  
     <span data-ttu-id="55f62-111">A operação de serviço `StartSendingQuotes` é implementado como uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="55f62-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="55f62-112">Podemos recuperar o canal de retorno de chamada usando o `OperationContext` e se o canal estiver aberto, podemos fazer async chamada no canal de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="55f62-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4.  <span data-ttu-id="55f62-113">Configurar o serviço</span><span class="sxs-lookup"><span data-stu-id="55f62-113">Configure the service</span></span>  
  
    ```xml  
    <configuration>  
        <appSettings>  
          <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />        
        </appSettings>  
        <system.web>  
          <compilation debug="true" targetFramework="4.5" />        
        </system.web>  
        <system.serviceModel>  
            <protocolMapping>  
              <add scheme="http" binding="netHttpBinding"/>  
              <add scheme="https" binding="netHttpsBinding"/>  
            </protocolMapping>  
            <behaviors>  
                <serviceBehaviors>  
                    <behavior name="">  
                        <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                        <serviceDebug includeExceptionDetailInFaults="false" />  
                    </behavior>  
                </serviceBehaviors>  
            </behaviors>  
            <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
                multipleSiteBindingsEnabled="true" />  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="55f62-114">Arquivo de configuração do serviço depende de pontos de extremidade do WCF padrão.</span><span class="sxs-lookup"><span data-stu-id="55f62-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="55f62-115">O `<protocolMapping>` seção é usada para especificar que o `NetHttpBinding` devem ser usados para pontos de extremidade padrão criados.</span><span class="sxs-lookup"><span data-stu-id="55f62-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="55f62-116">Definir o cliente</span><span class="sxs-lookup"><span data-stu-id="55f62-116">Define the Client</span></span>  
  
1.  <span data-ttu-id="55f62-117">Implemente o contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="55f62-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="55f62-118">A operação do contrato de retorno de chamada é implementada como um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="55f62-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1.  <span data-ttu-id="55f62-119">Implemente o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="55f62-119">Implement the client code.</span></span>  
  
        ```csharp  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                var context = new InstanceContext(new CallbackHandler());  
                var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
                client.StartSendingQuotes();              
                Console.ReadLine();  
            }  
  
            private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
        }  
        ```  
  
         <span data-ttu-id="55f62-120">O CallbackHandler é repetido aqui para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="55f62-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="55f62-121">O aplicativo cliente cria um novo InstanceContext e especifica a implementação da interface de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="55f62-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="55f62-122">Em seguida, ele cria uma instância da classe de proxy do envio de uma referência a InstanceContext recém-criado.</span><span class="sxs-lookup"><span data-stu-id="55f62-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="55f62-123">Quando o cliente chama o serviço, o serviço chamará o cliente usando o contrato de retorno de chamada especificado.</span><span class="sxs-lookup"><span data-stu-id="55f62-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2.  <span data-ttu-id="55f62-124">Configurar o cliente</span><span class="sxs-lookup"><span data-stu-id="55f62-124">Configure the client</span></span>  
  
        ```xml  
        <?xml version="1.0" encoding="utf-8" ?>  
        <configuration>  
            <startup>   
                <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
            </startup>  
            <system.serviceModel>  
                <bindings>  
                    <netHttpBinding>  
                        <binding name="NetHttpBinding_IStockQuoteService">  
                            <webSocketSettings transportUsage="Always" />  
                        </binding>  
                    </netHttpBinding>  
                </bindings>  
                <client>  
                    <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                        binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                        contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
                </client>  
            </system.serviceModel>  
        </configuration>  
        ```  
  
         <span data-ttu-id="55f62-125">Não há nada de especial que você precisa fazer na configuração do cliente, basta especificar o ponto de extremidade de lado cliente usando o `NetHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="55f62-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55f62-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55f62-126">Example</span></span>  
 <span data-ttu-id="55f62-127">Este é o código completo usado neste tópico.</span><span class="sxs-lookup"><span data-stu-id="55f62-127">The following is the complete code used in this topic.</span></span>  
  
```csharp  
// IStockQuoteService.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
    public interface IStockQuoteService  
    {  
        [OperationContract(IsOneWay = true)]  
        Task StartSendingQuotes();  
    }  
  
    [ServiceContract]  
    public interface IStockQuoteCallback  
    {  
        [OperationContract(IsOneWay = true)]  
        Task SendQuote(string code, double value);  
    }  
}  
```  
  
```  
// StockQuoteService.svc.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  
  
            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
}  
```  
  
```xml  
<?xml version="1.0"?>  
  
<!--  
  For more information on how to configure your ASP.NET application, please visit  
  http://go.microsoft.com/fwlink/?LinkId=169433  
  -->  
  
<configuration>  
    <appSettings>  
      <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />        
    </appSettings>  
    <system.web>  
      <compilation debug="true" targetFramework="4.5" />        
    </system.web>  
    <system.serviceModel>  
        <protocolMapping>  
          <add scheme="http" binding="netHttpBinding"/>  
          <add scheme="https" binding="netHttpsBinding"/>  
        </protocolMapping>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="">  
                    <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                    <serviceDebug includeExceptionDetailInFaults="false" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
        <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
            multipleSiteBindingsEnabled="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
```  
<!-- StockQuoteService.svc -->  
<%@ ServiceHost Language="C#" Debug="true" Service="Server.StockQuoteService" CodeBehind="StockQuoteService.svc.cs" %>  
```  
  
```csharp  
// Client.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            var context = new InstanceContext(new CallbackHandler());  
            var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
            client.StartSendingQuotes();              
            Console.ReadLine();  
        }  
  
        private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
        {  
            public async Task SendQuoteAsync(string code, double value)  
            {  
                Console.WriteLine("{0}: {1:f2}", code, value);  
            }  
        }  
    }  
}  
```  
  
```xml  
<!—App.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <startup>   
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
    <system.serviceModel>  
        <bindings>  
            <netHttpBinding>  
                <binding name="NetHttpBinding_IStockQuoteService">  
                    <webSocketSettings transportUsage="Always" />  
                </binding>  
            </netHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55f62-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55f62-128">See Also</span></span>  
 [<span data-ttu-id="55f62-129">Operações síncronas e assíncronas</span><span class="sxs-lookup"><span data-stu-id="55f62-129">Synchronous and Asynchronous Operations</span></span>](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [<span data-ttu-id="55f62-130">Usando o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="55f62-130">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)
