---
title: Exemplo de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: db4cd5be73e3c170f2feaa1e76f275eb7d9cd226
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800231"
---
# <a name="nettcp-port-sharing-sample"></a>Exemplo de compartilhamento de porta Net.TCP
O protocolo TCP/IP usa um número de 16 bits, chamado de porta, para diferenciar conexões para vários aplicativos de rede em execução no mesmo computador. Se um aplicativo estiver escutando em uma porta, todo o tráfego TCP para essa porta irá para esse aplicativo. Outros aplicativos não podem escutar nessa porta ao mesmo tempo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Muitos protocolos tem um número de porta padrão que eles usam. Por exemplo, o protocolo HTTP normalmente usa a porta TCP 80. Serviços de informações da Internet (IIS) tem um ouvinte para compartilhar uma porta entre vários aplicativos HTTP. O IIS escuta na porta diretamente e encaminha mensagens para o aplicativo apropriado com base nas informações dentro do fluxo de mensagens. Isso permite que vários aplicativos HTTP usar o mesmo número de porta sem ter que competir para reservar a porta para receber mensagens.  
  
 Compartilhamento de porta NetTcp é um recurso do Windows Communication Foundation (WCF) que da mesma forma permite que vários aplicativos de rede compartilhar uma única porta. O serviço de compartilhamento de porta NetTcp aceita conexões usando o protocolo NET. TCP e encaminha mensagens com base em seu endereço de destino.  
  
 O serviço de compartilhamento de porta NetTcp não é habilitado por padrão. Antes de executar este exemplo, você deve habilitar manualmente o serviço. Para obter mais informações, consulte [como: habilitar o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Se o serviço estiver desabilitado, uma exceção é lançada quando o aplicativo de servidor é iniciado.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Compartilhamento de porta está habilitado no servidor, definindo a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade do <xref:System.ServiceModel.NetTcpBinding> associação ou o <xref:System.ServiceModel.Channels.TcpTransportBindingElement> elemento de associação. O cliente não precisa saber como compartilhamento de porta foi configurado para usá-lo no servidor.  
  
## <a name="enabling-port-sharing"></a>Habilitar o compartilhamento de porta  
 O código a seguir demonstra a habilitação de compartilhamento de porta no servidor. Ele inicia uma instância da `ICalculator` serviço em uma porta fixa com um caminho URI aleatório. Mesmo que dois serviços podem compartilhar a mesma porta, seus endereços de ponto de extremidade geral ainda devem ser exclusivos para que o serviço de compartilhamento de porta NetTcp pode rotear mensagens para o aplicativo correto.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Com o compartilhamento de porta habilitado, você pode executar o serviço várias vezes sem a necessidade de um conflito de número de porta. Se você alterar o código para desabilitar o compartilhamento de porta, iniciar duas cópias do serviço resulta em falha do segundo com um <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>A execução do exemplo  
 Você pode usar o cliente de teste para verificar que mensagens sejam corretamente roteadas aos serviços de compartilhamento de porta.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
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

 Cada instância do serviço imprime seu número exclusivo e o endereço. Por exemplo, você pode ver o texto a seguir quando você executar service.exe.  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Insira o número de serviço que você vê aqui quando você executar client.exe.  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Este exemplo pode ser executado em uma configuração de várias máquinas, alterando o endereço gerado que o cliente usa. Em Client.cs, altere a cadeia de caracteres de formato de endereço de ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com o endereço IP do computador do servidor. Você deve recompilar o exemplo depois de fazer essa alteração.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Habilite o NetTcp porta compartilhamento serviço conforme descrito anteriormente na seção Introdução.  
  
4.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Detalhes específicos para executar esse exemplo estão incluídos anteriormente em execução a seção de exemplo.  
  
## <a name="see-also"></a>Consulte também
