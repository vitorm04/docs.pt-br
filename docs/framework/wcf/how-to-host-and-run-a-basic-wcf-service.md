---
title: Como hospedar e executar um serviço básico do Windows Communication Foundation
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: b79c3246b7c12a3a99a5c68586387fc30573dcb6
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562288"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Como hospedar e executar um serviço básico do Windows Communication Foundation

Esta é a terceira de seis tarefas necessárias para criação de um aplicativo do WCF (Windows Communication Foundation). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).

Este tópico descreve como hospedar um serviço WCF (Windows Communication Foundation) em um aplicativo de console. Este procedimento consiste nas seguintes etapas:

- Crie um projeto de aplicativo de console para hospedar o serviço.

- Crie um host de serviço para o serviço.

- Ative a troca de metadados.

- Abra o host do serviço.

Uma lista completa de código escrito nesta tarefa é fornecido no exemplo após o procedimento.

## <a name="create-a-new-console-application-to-host-the-service"></a>Criar um novo aplicativo de console para hospedar o serviço

1. Criar um novo projeto de aplicativo de Console no Visual Studio clicando duas vezes na solução guia de Introdução e selecionando **Add** > **novo projeto**. No **adicionar novo projeto** caixa de diálogo, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual c#** ou **Visual Basic**. Selecione o **aplicativo de Console (.NET Framework)** modelo e, em seguida, nomeie o projeto **GettingStartedHost**.

2. Adicione uma referência ao projeto GettingStartedLib ao projeto GettingStartedHost. Clique com botão direito no **referências** pasta sob o projeto GettingStartedHost no **Gerenciador de soluções**e, em seguida, selecione **Add Reference**. No **adicionar referência** caixa de diálogo, selecione **solução** no lado esquerdo da caixa de diálogo, selecione GettingStartedLib na seção central da caixa de diálogo e, em seguida, escolha **adicionar**. Isso torna os tipos definidos em GettingStartedLib disponíveis para o projeto GettingStartedHost.

3. Adicione uma referência a System. ServiceModel ao projeto GettingStartedHost. Clique com botão direito do **referências** pasta sob o projeto GettingStartedHost no **Gerenciador de soluções** e selecione **Add Reference**. No **adicionar referência** caixa de diálogo, selecione **Framework** no lado esquerdo da caixa de diálogo, sob **Assemblies**. Localize e selecione **System. ServiceModel**e, em seguida, escolha **Okey**. Salve a solução selecionando **arquivo** > **Salvar tudo**.

## <a name="host-the-service"></a>O serviço de host

Abra o arquivo Program.cs ou Module.vb e insira o código a seguir:

```csharp
using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using GettingStartedLib;

namespace GettingStartedHost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 Create a ServiceHost instance
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 Start the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
                selfHost.Close();
            }
            catch (CommunicationException ce)
            {
                Console.WriteLine("An exception occurred: {0}", ce.Message);
                selfHost.Abort();
            }
        }
    }
}
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 Create a URI to serve as the base address
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")

            ' Step 2 Create a ServiceHost instance
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
           Try

                ' Step 3 Add a service endpoint
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 Enable metadata exchange.
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 Start the service
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

**Etapa 1** -cria uma instância da classe do Uri para manter o endereço base do serviço. Os serviços são identificados por uma URL que contém um endereço básico e um URI opcional. O endereço básico é formatado da seguinte maneira: [transport]://[machine-name or domain][:optional port #]/[optional URI segment] O endereço básico para o serviço de calculadora usa o transporte HTTP, o localhost , a porta 8000 e o segmento de URI "GettingStarted"

**Etapa 2** – cria uma instância do <xref:System.ServiceModel.ServiceHost> classe para hospedar o serviço. O construtor aceita dois parâmetros, o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.

**Etapa 3** – cria um <xref:System.ServiceModel.Description.ServiceEndpoint> instância. Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço. O construtor <xref:System.ServiceModel.Description.ServiceEndpoint> portanto utiliza o tipo de interface do contrato de serviço, uma associação e um endereço. O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço. A associação usada nesse exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna usada para conectar-se a pontos de extremidade que atendem às especificações de WS-*. Para obter mais informações sobre as associações WCF, confira [Visão geral das associações WCF](../../../docs/framework/wcf/bindings-overview.md). O endereço é adicionado ao endereço básico para identificar o ponto de extremidade. O endereço especificado nesse código é "CalculatorService", portanto, o endereço totalmente qualificado para o ponto de extremidade é `"http://localhost:8000/GettingStarted/CalculatorService"`.

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

**Etapa 4** – habilitar a troca de metadados. Os clientes usarão a troca de metadados para gerar os proxies que serão usados para chamar as operações de serviço. Para permitir que a troca de metadados crie uma instância de <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, defina sua propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true` e adicione o comportamento à coleção de <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` da instância <xref:System.ServiceModel.ServiceHost>.

**Etapa 5** – abra o <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada. Observe que o código aguarda o usuário pressionar ENTER. Se você não fizer isso, o aplicativo será fechado imediatamente e o serviço será encerrado. Observe também que um bloco try/catch foi usado. Após o <xref:System.ServiceModel.ServiceHost> ter sido instanciado, todos os outros códigos serão colocados em um bloco try/catch. Para obter mais informações sobre a captura segura de exceções geradas por <xref:System.ServiceModel.ServiceHost>, confira [Evitando problemas com a instrução using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)

> [!IMPORTANT]
> Edite App. config em GettingStartedLib para refletir as alterações feitas no código:
> 1. Altere a linha 14 para `<service name="GettingStartedLib.CalculatorService">`
> 2. Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

## <a name="verify-the-service-is-working"></a>Verifique se que o serviço está funcionando

1. Executar o console GettingStartedHost aplicativo de dentro do Visual Studio.

   O serviço deve ser executado com privilégios de administrador. Porque o Visual Studio foi aberto com privilégios de administrador, o GettingStartedHost também será executado com privilégios de administrador. Você também pode abrir um prompt de comando usando a nova **executar como administrador** e executar service.exe dentro dele.

2. Abra um navegador da web e navegue até a página de depuração do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.

## <a name="example"></a>Exemplo

O exemplo a seguir inclui o contrato e a implementação do serviço das etapas anteriores no tutorial e hospeda o serviço em um aplicativo de console.

Para compilar isso com um compilador de linha de comando, compile IService1.cs e Service1.cs em uma biblioteca de classes que faz referência a `System.ServiceModel.dll`. Compile Program.cs como um aplicativo de console.

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
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
}
```

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using GettingStartedLib;

namespace GettingStartedHost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");

            // Step 2 of the hosting procedure: Create ServiceHost
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 of the hosting procedure: Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 of the hosting procedure: Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
                selfHost.Close();
            }
            catch (CommunicationException ce)
            {
                Console.WriteLine("An exception occurred: {0}", ce.Message);
                selfHost.Abort();
            }
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")

            ' Step 2 of the hosting procedure: Create ServiceHost
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
            Try

                ' Step 3 of the hosting procedure: Add a service endpoint.
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 of the hosting procedure: Enable metadata exchange.
                ' Enable metadata exchange
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

> [!NOTE]
> Os serviços como este exigem permissão para registrar endereços HTTP no computador para escuta. As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP. Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Ao ser executado no Visual Studio, o arquivo service.exe precisa ser executado com privilégios de administrador.

## <a name="next-steps"></a>Próximas etapas

Agora o serviço está sendo executado. A próxima tarefa, você criará um cliente WCF.

> [!div class="nextstepaction"]
> [Como: criar um cliente WCF](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

Para obter informações sobre solução de problemas, confira [Solução de problemas do tutorial de introdução](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).

## <a name="see-also"></a>Consulte também

- [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)