---
title: Exemplo básico
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 5d0470fefff86ee3a88fa290be5f349c38ca8276
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716088"
---
# <a name="basic-sample"></a>Exemplo básico

Este exemplo mostra como tornar um serviço detectável e como Pesquisar e chamar um serviço que possa ser descoberto. Este exemplo é composto por dois projetos: serviço e cliente.

> [!NOTE]
> Este exemplo implementa a descoberta no código.  Para obter um exemplo que implementa a descoberta na configuração, consulte [configuração](../../../../docs/framework/wcf/samples/configuration-sample.md).

## <a name="service"></a>Service

Esta é uma implementação de serviço de calculadora simples. O código relacionado à descoberta pode ser encontrado em `Main` em que um <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> é adicionado ao host de serviço e um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> é adicionado, conforme mostrado no código a seguir.

```csharp
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

O cliente usa um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para localizar o serviço. O <xref:System.ServiceModel.Discovery.DynamicEndpoint>, um ponto de extremidade padrão, resolve o ponto de extremidade do serviço quando o cliente é aberto. Nesse caso, a <xref:System.ServiceModel.Discovery.DynamicEndpoint> procura o serviço com base no contrato de serviço. O <xref:System.ServiceModel.Discovery.DynamicEndpoint> realiza a pesquisa em um <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> por padrão. Depois de localizar um ponto de extremidade de serviço, o cliente se conecta a esse serviço pela associação especificada.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

O cliente define um método chamado `InvokeCalculatorService` que usa a classe <xref:System.ServiceModel.Discovery.DiscoveryClient> para Pesquisar serviços. O <xref:System.ServiceModel.Discovery.DynamicEndpoint> herda de <xref:System.ServiceModel.Description.ServiceEndpoint>, portanto, ele pode ser passado para o método `InvokeCalculatorService`. Em seguida, o exemplo usa o <xref:System.ServiceModel.Discovery.DynamicEndpoint> para criar uma instância do `CalculatorServiceClient` e chama as várias operações do serviço de calculadora.

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

1. Este exemplo usa pontos de extremidade HTTP e para executar este exemplo, as ACLs de URL adequadas devem ser adicionadas. Para obter mais informações, consulte [Configurando http e HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). A execução do comando a seguir em um privilégio elevado deve adicionar as ACLs apropriadas. Talvez você queira substituir seu domínio e nome de usuário pelos argumentos a seguir se o comando não funcionar como está. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Usando o Visual Studio 2012, abra o Basic. sln e compile o exemplo.

3. Execute o aplicativo Service. exe.

4. Depois que o serviço for iniciado, execute o Client. exe.

5. Observe que o cliente conseguiu encontrar o serviço sem saber seu endereço.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
