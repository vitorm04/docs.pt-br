---
title: Exemplo de introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: b249137117f970a14284beb6439e501a3004eee1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298858"
---
# <a name="getting-started-sample"></a>Exemplo de introdução

Guia de Introdução do exemplo demonstra como implementar um serviço típico e um cliente típico usando o Windows Communication Foundation (WCF). Este exemplo é a base para todos os outros exemplos de tecnologia básica.

> [!NOTE]
> As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

O serviço descreve as operações que ele executa em um contrato de serviço que ele expõe publicamente como metadados. O serviço também contém o código para implementar as operações.

O cliente contém uma definição de contrato de serviço e uma classe de proxy para acessar o serviço. O código de proxy é gerado a partir de metadados de serviço usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).

Em [!INCLUDE[wv](../../../../includes/wv-md.md)], o serviço está hospedado no Windows Activation Service (WAS). Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ele é hospedado pelo Internet Information Services (IIS) e ASP.NET. Hospedar um serviço no IIS ou WAS permite que o serviço seja ativado automaticamente quando ele é acessado pela primeira vez.

> [!NOTE]
> Se você preferir começar com um exemplo que hospeda o serviço em um aplicativo de console, em vez de IIS, consulte a [auto-hospedar](../../../../docs/framework/wcf/samples/self-host.md) exemplo.

O serviço e o cliente especificam detalhes de acesso no arquivo de configuração, que fornecem flexibilidade no momento da implantação. Isso inclui uma definição de ponto de extremidade que especifica um endereço, ligação e contrato. A associação especifica os detalhes de transporte e segurança para como o serviço deve ser acessado.

O serviço configura um comportamento de tempo de execução para publicar seus metadados.

O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir). O cliente faz solicitações para uma operação matemática determinado e as respostas de serviço com o resultado. O serviço implementa um `ICalculator` contrato que é definido no código a seguir.

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

A implementação do serviço calcula e retorna o resultado apropriado, conforme mostrado no código de exemplo a seguir.

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

O serviço expõe um ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config), conforme mostrado no seguinte exemplo de configuração.

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

O serviço expõe o ponto de extremidade no endereço base fornecido pelo host do IIS ou WAS. A associação está configurada com um padrão <xref:System.ServiceModel.WSHttpBinding>, que fornece comunicação HTTP e protocolos padrão do serviço da Web para endereçamento e segurança. O contrato é o `ICalculator` implementadas pelo serviço.

Conforme configurado, o serviço pode ser acessado em `http://localhost/servicemodelsamples/service.svc` por um cliente no mesmo computador. Para clientes em computadores remotos acessar o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez do localhost.

A estrutura não expõem metadados por padrão. Como tal, ativa o serviço do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e expõe um ponto de extremidade do exchange (MEX) de metadados em `http://localhost/servicemodelsamples/service.svc/mex`. A configuração a seguir demonstra isso.

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

O cliente se comunica usando um tipo de contrato fornecida por meio de uma classe de cliente que é gerada pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Esse cliente gerado está contido no arquivo generatedClient.cs ou generatedClient.vb. Esse utilitário recupera metadados para um determinado serviço e gera um cliente para uso pelo aplicativo cliente para se comunicar usando um tipo de contrato indicado. O serviço hospedado deve estar disponível para gerar o código do cliente, porque o serviço é usado para recuperar os metadados atualizados.

 Execute o seguinte comando no prompt de comando do SDK no diretório do cliente para gerar o proxy tipado:

```
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

Para gerar o cliente no tipo de Visual Basic a seguir no prompt de comando do SDK:

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

Usando o cliente gerado, o cliente pode acessar um ponto de extremidade de serviço em questão, configurando o endereço apropriado e associação. Como o serviço, o cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade com o qual deseja se comunicar. A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e contrato, conforme mostrado no exemplo a seguir.

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

A implementação do cliente cria uma instância de cliente e usa a interface digitada para começar a se comunicar com o serviço, conforme mostrado no código de exemplo a seguir.

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

// Call the Subtract service operation.
value1 = 145.00D;
value2 = 76.54D;
result = client.Subtract(value1, value2);
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

// Call the Multiply service operation.
value1 = 9.00D;
value2 = 81.25D;
result = client.Multiply(value1, value2);
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

// Call the Divide service operation.
value1 = 22.00D;
value2 = 7.00D;
result = client.Divide(value1, value2);
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

//Closing the client releases all communication resources.
client.Close();
```

Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

O exemplo de introdução mostra o modo padrão para criar um serviço e cliente. A outra [básica](../../../../docs/framework/wcf/samples/basic-sample.md) expandir esse exemplo para demonstrar os recursos de produto específico.

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

## <a name="see-also"></a>Consulte também

- [Como: hospedar um serviço do WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Como: hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
