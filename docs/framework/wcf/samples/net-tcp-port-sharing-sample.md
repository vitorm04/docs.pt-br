---
title: Exemplo de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: ac90a50c6fe06a643881da2889fdea308404508e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144286"
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="9624a-102">Exemplo de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9624a-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="9624a-103">O protocolo TCP/IP usa um número de 16 bits, chamado de porta, para diferenciar conexões a vários aplicativos de rede em execução na mesma máquina.</span><span class="sxs-lookup"><span data-stu-id="9624a-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="9624a-104">Se um aplicativo estiver ouvindo em uma porta, então todo o tráfego de TCP para essa porta vai para esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9624a-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="9624a-105">Outros aplicativos não podem ouvir essa porta ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="9624a-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9624a-106">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9624a-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9624a-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9624a-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9624a-108">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="9624a-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9624a-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9624a-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="9624a-110">Muitos protocolos têm um número de porta padrão ou padrão que eles usam.</span><span class="sxs-lookup"><span data-stu-id="9624a-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="9624a-111">Por exemplo, o protocolo HTTP normalmente usa a porta TCP 80.</span><span class="sxs-lookup"><span data-stu-id="9624a-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="9624a-112">O Internet Information Services (IIS) tem um ouvinte para compartilhar uma porta entre vários aplicativos HTTP.</span><span class="sxs-lookup"><span data-stu-id="9624a-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="9624a-113">O IIS ouve diretamente na porta e encaminha mensagens para o aplicativo apropriado com base nas informações dentro do fluxo de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9624a-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="9624a-114">Isso permite que vários aplicativos HTTP usem o mesmo número de porta sem ter que competir para reservar a porta para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="9624a-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="9624a-115">NetTcp Port Sharing é um recurso da Windows Communication Foundation (WCF) que também permite que vários aplicativos de rede compartilhem uma única porta.</span><span class="sxs-lookup"><span data-stu-id="9624a-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="9624a-116">O Serviço de Compartilhamento de Portas NetTcp aceita conexões usando o protocolo net.tcp e encaminha mensagens com base em seu endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="9624a-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="9624a-117">O Serviço de Compartilhamento de Portas NetTcp não está habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="9624a-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="9624a-118">Antes de executar esta amostra, você deve ativar manualmente o serviço.</span><span class="sxs-lookup"><span data-stu-id="9624a-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="9624a-119">Para obter mais informações, [consulte Como: Ativar o serviço de compartilhamento de portas Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="9624a-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="9624a-120">Se o serviço estiver desativado, uma exceção será lançada quando o aplicativo do servidor for iniciado.</span><span class="sxs-lookup"><span data-stu-id="9624a-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="9624a-121">O compartilhamento de portas é habilitado no servidor definindo a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade da <xref:System.ServiceModel.NetTcpBinding> vinculação ou do <xref:System.ServiceModel.Channels.TcpTransportBindingElement> elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="9624a-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="9624a-122">O cliente não precisa saber como o compartilhamento de portas foi configurado para usá-lo no servidor.</span><span class="sxs-lookup"><span data-stu-id="9624a-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="9624a-123">Habilitando o compartilhamento de portas</span><span class="sxs-lookup"><span data-stu-id="9624a-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="9624a-124">O código a seguir demonstra a habilitação do compartilhamento de portas no servidor.</span><span class="sxs-lookup"><span data-stu-id="9624a-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="9624a-125">Ele inicia uma `ICalculator` instância do serviço em uma porta fixa com um caminho URI aleatório.</span><span class="sxs-lookup"><span data-stu-id="9624a-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="9624a-126">Embora dois serviços possam compartilhar a mesma porta, seus endereços de ponto final global ainda devem ser únicos para que o Serviço de Compartilhamento de Portas NetTcp possa encaminhar mensagens para o aplicativo correto.</span><span class="sxs-lookup"><span data-stu-id="9624a-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="9624a-127">Com o compartilhamento de portas ativado, você pode executar o serviço várias vezes sem ter um conflito sobre o número da porta.</span><span class="sxs-lookup"><span data-stu-id="9624a-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="9624a-128">Se você alterar o código para desativar o compartilhamento de portas, iniciar <xref:System.ServiceModel.AddressAlreadyInUseException>duas cópias do serviço resultará na segunda falha com um .</span><span class="sxs-lookup"><span data-stu-id="9624a-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="9624a-129">Executando o exemplo</span><span class="sxs-lookup"><span data-stu-id="9624a-129">Running the Sample</span></span>  
 <span data-ttu-id="9624a-130">Você pode usar o cliente de teste para verificar se as mensagens estão corretamente encaminhadas para serviços que compartilham a porta.</span><span class="sxs-lookup"><span data-stu-id="9624a-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="9624a-131">Cada instância do serviço imprime seu número e endereço únicos.</span><span class="sxs-lookup"><span data-stu-id="9624a-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="9624a-132">Por exemplo, você pode ver o seguinte texto quando executar service.exe.</span><span class="sxs-lookup"><span data-stu-id="9624a-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="9624a-133">Digite o número de serviço que você vê aqui quando executar client.exe.</span><span class="sxs-lookup"><span data-stu-id="9624a-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="9624a-134">Esta amostra pode ser executada em uma configuração de máquina cruzada alterando o endereço gerado que o cliente usa.</span><span class="sxs-lookup"><span data-stu-id="9624a-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="9624a-135">No Client.cs, altere a seqüência de formato de endereço de ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="9624a-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="9624a-136">Substitua quaisquer referências a "localhost" pelo endereço IP da máquina do servidor.</span><span class="sxs-lookup"><span data-stu-id="9624a-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="9624a-137">Você deve recompilar a amostra depois de fazer esta mudança.</span><span class="sxs-lookup"><span data-stu-id="9624a-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9624a-138">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9624a-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9624a-139">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9624a-139">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="9624a-140">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9624a-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="9624a-141">Habilite o Serviço de Compartilhamento de Portas NetTcp conforme descrito anteriormente na seção introdução.</span><span class="sxs-lookup"><span data-stu-id="9624a-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="9624a-142">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9624a-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="9624a-143">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9624a-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="9624a-144">Detalhes específicos para a execução desta amostra estão incluídos anteriormente na seção Executando a amostra.</span><span class="sxs-lookup"><span data-stu-id="9624a-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
