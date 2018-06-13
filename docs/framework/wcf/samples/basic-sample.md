---
title: Exemplo básico
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 67c626dfa511251043da81e025aab20578be3016
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502132"
---
# <a name="basic-sample"></a>Exemplo básico
Este exemplo mostra como criar um serviço detectável e como procurar e chamar um serviço detectável. Este exemplo é composto de dois projetos: serviço e cliente.  
  
> [!NOTE]
>  Este exemplo implementa descoberta no código.  Para obter um exemplo que implementa a descoberta de configuração, consulte [configuração](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Serviço  
 Isso é uma implementação de serviço de cálculo simples. A descoberta relacionadas código pode ser encontrado em `Main` onde um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é adicionada para o host de serviço e um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é adicionado, como mostrado no código a seguir.  
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Cliente  
 O cliente usa um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para localizar o serviço. O <xref:System.ServiceModel.Discovery.DynamicEndpoint>, um ponto de extremidade padrão resolve o ponto de extremidade do serviço quando o cliente é aberto. Nesse caso, o <xref:System.ServiceModel.Discovery.DynamicEndpoint> procura o serviço com base no contrato de serviço. O <xref:System.ServiceModel.Discovery.DynamicEndpoint> realiza a pesquisa em um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> por padrão. Depois que ele localiza um ponto de extremidade de serviço, o cliente se conecta ao serviço sobre a associação especificada.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 O cliente define um método chamado `InvokeCalculatorService` que usa o <xref:System.ServiceModel.Discovery.DiscoveryClient> classe para procurar serviços. O <xref:System.ServiceModel.Discovery.DynamicEndpoint> herda de <xref:System.ServiceModel.Description.ServiceEndpoint>, portanto, ele pode ser passado para o `InvokeCalculatorService` método. O exemplo usa o <xref:System.ServiceModel.Discovery.DynamicEndpoint> para criar uma instância de `CalculatorServiceClient` e chama as várias operações do serviço de cálculo.  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Este exemplo usa pontos de extremidade HTTP e para executar este exemplo, as ACLs adequadas de URL deve ser adicionado. Para obter mais informações, consulte [Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Executando o seguinte comando em um privilégio elevado deve adicionar as ACLs corretas. Convém substituir seu domínio e nome de usuário para os argumentos a seguir se o comando não funcionar como está. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o Basic.sln e compilar o exemplo.  
  
3.  Execute o aplicativo service.exe.  
  
4.  Depois que o serviço foi iniciado, execute o client.exe.  
  
5.  Observe que o cliente foi capaz de encontrar o serviço sem saber o endereço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a>Consulte também
