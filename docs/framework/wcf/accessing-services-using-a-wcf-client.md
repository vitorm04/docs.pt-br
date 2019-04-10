---
title: Usando um cliente WCF para acessar um serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 6bf683cdd0a03a5d1dbc452c28e7b33911464f09
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297246"
---
# <a name="accessing-services-using-a-wcf-client"></a>Usando um cliente WCF para acessar um serviço

Depois de criar um serviço, a próxima etapa é criar um proxy de cliente do WCF. Um aplicativo cliente usa o proxy de cliente do WCF para se comunicar com o serviço. Normalmente, aplicativos cliente importar metadados de um serviço para gerar o código de cliente do WCF que pode ser usado para invocar o serviço.

 As etapas básicas para a criação de um cliente WCF incluem o seguinte:

1. Compile o código de serviço.

2. Gere o proxy de cliente do WCF.

3. Instancie o proxy de cliente do WCF.

O proxy de cliente do WCF pode ser gerado manualmente usando a ferramenta Utilitário de serviço de modelo de metadados (SvcUtil.exe) para obter mais informações, consulte [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). O proxy de cliente do WCF também pode ser gerado dentro do Visual Studio usando o **adicionar referência de serviço** recurso. Para gerar o proxy de cliente do WCF usando um método de serviço deve estar em execução. Se o serviço for auto-hospedado, você deve executar o host. Se o serviço está hospedado no IIS / WAS não é preciso fazer mais nada.

## <a name="servicemodel-metadata-utility-tool"></a>Ferramenta Utilitário de metadados de ServiceModel
 O [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) é uma ferramenta de linha de comando para gerar o código dos metadados. O uso a seguir é um exemplo de um comando Svcutil.exe básico.

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Como alternativa, você pode usar Svcutil.exe com arquivos de idioma (XSD) de definição descrição linguagem WSDL (Web Services) e o esquema XML no sistema de arquivos.

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 O resultado é um arquivo de código que contém o código de cliente do WCF que o aplicativo cliente pode usar para invocar o serviço.

 Você também pode usar a ferramenta para gerar arquivos de configuração.

```
Svcutil.exe <file1 [,file2]>
```

 Se apenas um nome de arquivo for fornecido, que é o nome do arquivo de saída. Se dois nomes de arquivo fornecidos, o primeiro arquivo é um arquivo de configuração de entrada cujo conteúdo é mesclado com a configuração gerada e gravado no segundo arquivo. Para obter mais informações sobre a configuração, consulte [configurando associações para serviços](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Solicitações de metadados não segura representam certos riscos da mesma maneira que faz a qualquer solicitação de rede não segura: Se não tiver certeza de que você está se comunicando com o ponto de extremidade é quem diz ser, as informações recuperadas podem ser metadados de um serviço mal-intencionado.

## <a name="add-service-reference-in-visual-studio"></a>Adicionar referência de serviço no Visual Studio

 Com o serviço em execução com o botão direito do mouse no projeto que conterá o proxy de cliente do WCF e selecione **Add** > **referência de serviço**. No **adicionar referência de caixa de diálogo serviço**, digite a URL para o serviço que você deseja chamar e clique no **vá** botão. A caixa de diálogo exibirá uma lista de serviços disponíveis no endereço que você especificar. Clique duas vezes o serviço para ver os contratos e operações disponíveis, especifique um namespace para o código gerado e clique no **Okey** botão.

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

 A ferramenta de utilitário ServiceModel Metadata e **adicionar referência de serviço** no Visual Studio gera a seguinte classe de cliente do WCF. A classe herda de genéricos <xref:System.ServiceModel.ClientBase%601> classe e implementa o `ICalculator` interface. A ferramenta também gera o `ICalculator` interface (não mostrado aqui).

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
 Para usar o cliente do WCF, crie uma instância do cliente WCF e, em seguida, chamar seus métodos, conforme mostrado no código a seguir.

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

## <a name="debugging-exceptions-thrown-by-a-client"></a>Depuração de exceções geradas por um cliente

Muitas exceções geradas por um cliente WCF são causadas por uma exceção no serviço. Alguns exemplos disso são:

-   <xref:System.Net.Sockets.SocketException>: Uma conexão existente foi fechada forçadamente pelo host remoto.

-   <xref:System.ServiceModel.CommunicationException>: A conexão subjacente foi fechado inesperadamente.

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: A conexão de soquete foi anulada. Isso pode ser causado por um erro ao processar a mensagem, um tempo limite de recebimento foi excedido pelo host remoto ou um problema de recurso de rede subjacente.

Quando esses tipos de exceções ocorrem, a melhor maneira de resolver o problema é ativar o rastreamento no lado do serviço e determinar qual exceção ocorreu lá. Para obter mais informações sobre rastreamento, consulte [rastreamento](../../../docs/framework/wcf/diagnostics/tracing/index.md) e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Consulte também

- [Como: Criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Como: acessar serviços com um contrato duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Como: chamar operações de serviço de forma assíncrona](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Como: acessar os serviços com contratos unidirecionais e de solicitação-resposta](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Como: acessar um serviço WSE 3.0](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Noções básicas de código de cliente gerado](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [Como: melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [Especificando a execução do cliente- Comportamento do tempo](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Configurando comportamentos do cliente](../../../docs/framework/wcf/configuring-client-behaviors.md)
