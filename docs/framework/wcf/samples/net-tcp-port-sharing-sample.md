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
# <a name="nettcp-port-sharing-sample"></a>Exemplo de compartilhamento de porta Net.TCP
O protocolo TCP/IP usa um número de 16 bits, chamado de porta, para diferenciar conexões a vários aplicativos de rede em execução na mesma máquina. Se um aplicativo estiver ouvindo em uma porta, então todo o tráfego de TCP para essa porta vai para esse aplicativo. Outros aplicativos não podem ouvir essa porta ao mesmo tempo.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Muitos protocolos têm um número de porta padrão ou padrão que eles usam. Por exemplo, o protocolo HTTP normalmente usa a porta TCP 80. O Internet Information Services (IIS) tem um ouvinte para compartilhar uma porta entre vários aplicativos HTTP. O IIS ouve diretamente na porta e encaminha mensagens para o aplicativo apropriado com base nas informações dentro do fluxo de mensagens. Isso permite que vários aplicativos HTTP usem o mesmo número de porta sem ter que competir para reservar a porta para receber mensagens.  
  
 NetTcp Port Sharing é um recurso da Windows Communication Foundation (WCF) que também permite que vários aplicativos de rede compartilhem uma única porta. O Serviço de Compartilhamento de Portas NetTcp aceita conexões usando o protocolo net.tcp e encaminha mensagens com base em seu endereço de destino.  
  
 O Serviço de Compartilhamento de Portas NetTcp não está habilitado por padrão. Antes de executar esta amostra, você deve ativar manualmente o serviço. Para obter mais informações, [consulte Como: Ativar o serviço de compartilhamento de portas Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Se o serviço estiver desativado, uma exceção será lançada quando o aplicativo do servidor for iniciado.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 O compartilhamento de portas é habilitado no servidor definindo a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade da <xref:System.ServiceModel.NetTcpBinding> vinculação ou do <xref:System.ServiceModel.Channels.TcpTransportBindingElement> elemento de vinculação. O cliente não precisa saber como o compartilhamento de portas foi configurado para usá-lo no servidor.  
  
## <a name="enabling-port-sharing"></a>Habilitando o compartilhamento de portas  
 O código a seguir demonstra a habilitação do compartilhamento de portas no servidor. Ele inicia uma `ICalculator` instância do serviço em uma porta fixa com um caminho URI aleatório. Embora dois serviços possam compartilhar a mesma porta, seus endereços de ponto final global ainda devem ser únicos para que o Serviço de Compartilhamento de Portas NetTcp possa encaminhar mensagens para o aplicativo correto.  

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

 Com o compartilhamento de portas ativado, você pode executar o serviço várias vezes sem ter um conflito sobre o número da porta. Se você alterar o código para desativar o compartilhamento de portas, iniciar <xref:System.ServiceModel.AddressAlreadyInUseException>duas cópias do serviço resultará na segunda falha com um .  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Executando o exemplo  
 Você pode usar o cliente de teste para verificar se as mensagens estão corretamente encaminhadas para serviços que compartilham a porta.  

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

 Cada instância do serviço imprime seu número e endereço únicos. Por exemplo, você pode ver o seguinte texto quando executar service.exe.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Digite o número de serviço que você vê aqui quando executar client.exe.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Esta amostra pode ser executada em uma configuração de máquina cruzada alterando o endereço gerado que o cliente usa. No Client.cs, altere a seqüência de formato de endereço de ponto final para corresponder ao novo endereço do seu serviço. Substitua quaisquer referências a "localhost" pelo endereço IP da máquina do servidor. Você deve recompilar a amostra depois de fazer esta mudança.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Instale ASP.NET 4.0 usando o seguinte comando.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Habilite o Serviço de Compartilhamento de Portas NetTcp conforme descrito anteriormente na seção introdução.  
  
4. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Detalhes específicos para a execução desta amostra estão incluídos anteriormente na seção Executando a amostra.  
