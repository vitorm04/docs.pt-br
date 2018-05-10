---
title: Usando um cliente WCF para acessar um serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: b0bde07dbeb70eaafbde4d90627d245554ad7ca6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="accessing-services-using-a-wcf-client"></a>Usando um cliente WCF para acessar um serviço
Depois de criar um serviço, a próxima etapa é criar um proxy de cliente do WCF. Um aplicativo cliente usa o proxy de cliente do WCF para se comunicar com o serviço. Aplicativos cliente geralmente importar metadados de um serviço para gerar o código do cliente WCF que pode ser usado para chamar o serviço.  
  
 As etapas básicas para a criação de um cliente WCF incluem o seguinte:  
  
1.  Compile o código de serviço.  
  
2.  Gere o proxy de cliente do WCF.  
  
3.  Criar uma instância do proxy de cliente do WCF.  
  
 O proxy de cliente do WCF pode ser gerado manualmente usando a ferramenta Utilitário de serviço de modelo de metadados (SvcUtil.exe) para obter mais informações, consulte [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). O proxy de cliente do WCF também pode ser gerado no Visual Studio usando o recurso Adicionar referência de serviço. Para gerar o proxy de cliente WCF usando qualquer método de serviço deve estar em execução. Se o serviço é hospedado automaticamente, você deve executar o host. Se o serviço está hospedado no IIS / WAS não é necessário fazer mais nada.  
  
## <a name="servicemodel-metadata-utility-tool"></a>Ferramenta de utilitário de metadados ServiceModel  
 O [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) é uma ferramenta de linha de comando para gerar o código de metadados. Use o seguinte é um exemplo de um comando Svcutil.exe básico.  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 Como alternativa, você pode usar o Svcutil.exe com arquivos de linguagem XSD definição WSDL Web Services Description Language () e o esquema XML no sistema de arquivos.  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 O resultado é um arquivo de código que contém o código do cliente WCF que o aplicativo cliente pode usar para chamar o serviço.  
  
 Você também pode usar a ferramenta para gerar arquivos de configuração.  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 Se apenas um nome de arquivo for fornecido, que é o nome do arquivo de saída. Se dois nomes de arquivo fornecidos, o primeiro arquivo é um arquivo de configuração de entrada cujo conteúdo é mesclado com a configuração gerada e gravado no arquivo de segundo. Para obter mais informações sobre a configuração, consulte [configurando associações para serviços](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Solicitações de metadados não segura representam determinados riscos da mesma maneira que qualquer solicitação de rede desprotegida: se não tiver certeza de que você está se comunicando com o ponto de extremidade é quem diz ser, as informações recuperadas podem ser os metadados de um serviço mal-intencionado.  
  
## <a name="add-service-reference-in-visual-studio"></a>Adicionar referência de serviço no Visual Studio  
 Com o serviço em execução, clique com botão direito do projeto que conterá o proxy de cliente do WCF e selecione **adicionar referência de serviço**. No **adicionar referência de caixa de diálogo serviço** digite a URL para o serviço que você deseja chamar e clique no **vá** botão. A caixa de diálogo exibirá uma lista de serviços disponíveis no endereço que você especificar. Clique duas vezes o serviço para ver os contratos e operações disponíveis, especifique um namespace para o código gerado e clique no **Okey** botão.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra um contrato de serviço criado para um serviço.  
  
```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```
  
```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```
  
 A ferramenta de utilitário de ServiceModel Metadata e adicionar a referência de serviço no Visual Studio gera a seguinte classe de cliente do WCF. A classe herda de genérica <xref:System.ServiceModel.ClientBase%601> classe e implemente o `ICalculator` interface. A ferramenta também gera o `ICalculator` interface (não mostrado aqui).  
  
```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```  
  
```vb  
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```
  
## <a name="using-the-wcf-client"></a>Usando o cliente do WCF  
 Para usar o cliente do WCF, crie uma instância do cliente WCF e, em seguida, chamar seus métodos, como mostrado no código a seguir.  
  
```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```
  
```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```
  
## <a name="debugging-exceptions-thrown-by-a-client"></a>Exceções geradas por um cliente de depuração  
 Muitas exceções geradas por um cliente WCF são causadas por uma exceção no serviço. Alguns exemplos são:  
  
-   <xref:System.Net.Sockets.SocketException>: Uma conexão existente foi fechada forçadamente pelo host remoto.  
  
-   <xref:System.ServiceModel.CommunicationException>: A conexão subjacente foi fechado inesperadamente.  
  
-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: A conexão de soquete foi anulada. Isso pode ser causado por um erro ao processar a mensagem, um tempo limite de recepção ultrapassado pelo host remoto ou um problema de recurso de rede subjacente.  
  
 Quando esses tipos de exceções ocorrem, a melhor maneira de resolver o problema é ativar o rastreamento no lado do serviço e determinar quais exceção existe. Para obter mais informações sobre rastreamento, consulte [rastreamento](../../../docs/framework/wcf/diagnostics/tracing/index.md) e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Como acessar serviços com um contrato Duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Como chamar operações de serviço de forma assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Como acessar os serviços com contratos unidirecionais e de solicitação-resposta](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Como acessar um WSE 3.0 Service](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Entendendo o código do cliente gerado](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)  
 [Como melhorar o tempo de inicialização de aplicativos clientes WCF usando o XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)  
 [Especificando o comportamento em tempo de execução do cliente](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Configurando comportamentos do cliente](../../../docs/framework/wcf/configuring-client-behaviors.md)
