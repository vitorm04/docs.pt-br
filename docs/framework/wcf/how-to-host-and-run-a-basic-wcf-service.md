---
title: Como hospedar e executar um serviço básico do Windows Communication Foundation
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a13e5a0044c51700acce6b123688868443f635ae
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Como hospedar e executar um serviço básico do Windows Communication Foundation
Esta é a terceira das seis tarefas necessárias para criar um aplicativo [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Para obter uma visão geral de todos os seis das tarefas, consulte o [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md) tópico.  
  
 Este tópico descreve como hospedar um serviço do [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] em um aplicativo de console. Este procedimento consiste nas seguintes etapas:  
  
-   Crie um projeto de aplicativo de console para hospedar o serviço.  
  
-   Crie um host de serviço para o serviço.  
  
-   Ative a troca de metadados.  
  
-   Abra o host do serviço.  
  
 Uma lista completa de código escrito nesta tarefa é fornecido no exemplo após o procedimento.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Para criar um novo aplicativo de console para hospedar o serviço  
  
1.  Criar um novo projeto de aplicativo de Console clicando na solução Introdução, selecionar, **adicionar**, **novo projeto**. No **adicionar novo projeto** caixa de diálogo no lado esquerdo da caixa de diálogo Selecionar **Windows** em **c#** ou **VB**. Na seção central da caixa de diálogo Selecionar **aplicativo de Console**. Nomeie o projeto como GettingStartedHost.  
  
2.  Definir a estrutura de destino do projeto GettingStartedHost .NET Framework 4.5, clique com o botão direito em **GettingStartedHost** no Gerenciador de soluções e selecionando **propriedades**. Na caixa suspensa rotulada **Framework de destino** selecione **.NET Framework 4.5**. Configuração da estrutura de destino para um projeto VB é um pouco diferente, a caixa de diálogo de propriedades de projeto GettingStartedHost, clique o **compilar** guia no lado esquerdo da tela e, em seguida, clique no **avançadas de compilação Opções** botão no canto inferior esquerdo da caixa de diálogo. Em seguida, selecione **.NET Framework 4.5** na caixa suspensa rotulada **Framework de destino**.  
  
     Configuração da estrutura de destino causará [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] para recarregar a solução, pressione **Okey** quando solicitado.  
  
3.  Adicione uma referência ao projeto GettingStartedLib ao projeto GettingStartedHost, clique com o botão direito no **referências** pasta sob o projeto GettingStartedHost no Gerenciador de soluções e selecione **adicionar referência** . No **adicionar referência** caixa de diálogo, selecione **solução** no lado esquerdo da caixa de diálogo e selecione GettingStartedLib na seção central da caixa de diálogo e clique em **adicionar**. Isso torna os tipos definidos em GettingStartedLib disponíveis para o projeto GettingStartedHost.  
  
4.  Adicione uma referência a System. ServiceModel para o projeto GettingStartedHost clicando com o **referência** pasta no projeto no Gerenciador de soluções e selecione GettingStartedHost **adicionar** Referência. No **adicionar referência** caixa de diálogo Selecionar **Framework** no lado esquerdo da caixa de diálogo. Na caixa de texto Pesquisar Assemblies, digite `System.ServiceModel`. Na seção central da caixa de diálogo Selecionar **System. ServiceModel**, clique no **adicionar** botão e, em seguida, clique no **fechar** botão. Salve a solução clicando no botão Salvar Tudo abaixo do menu principal.  
  
### <a name="to-host-the-service"></a>Para hospedar o serviço  
  
-   Abra o arquivo Program.cs ou Module.vb e insira o código a seguir:  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
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
    'Module1.vb  
    Imports System  
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
  
    1.  Etapa 1 - Cria uma instância da classe URI para manter o endereço básico do serviço. Os serviços são identificados por uma URL que contém um endereço básico e um URI opcional. O endereço base é formatado da seguinte maneira: [de transporte] :// [nome do computador ou domínio] [: opcional # da porta] / [segmento URI opcional] o endereço base para o serviço da Calculadora usa o transporte HTTP, localhost, porta 8000 e o URI do segmento "GettingStarted"  
  
    2.  Etapa 2 - Cria uma instância da classe <xref:System.ServiceModel.ServiceHost> para hospedar o serviço. O construtor aceita dois parâmetros, o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.  
  
    3.  Etapa 3 – cria um <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instância. Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço. O <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` construtor, portanto, usa o tipo de interface de contrato de serviço, uma associação e um endereço. O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço. A associação usada nesse exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna usada para conectar-se a pontos de extremidade que atendem às especificações de WS-*. Para obter mais informações sobre as associações do WCF, consulte [visão geral de associações do WCF](../../../docs/framework/wcf/bindings-overview.md). O endereço é adicionado ao endereço básico para identificar o ponto de extremidade. O endereço especificado nesse código é "CalculatorService" para o endereço totalmente qualificado para o ponto de extremidade é `"http://localhost:8000/GettingStarted/CalculatorService"` adicionando um ponto de extremidade de serviço é opcional ao usar o .NET Framework 4.0 ou posterior. Nessas versões, se nenhum ponto final for adicionado no código ou na configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço. Para obter mais informações sobre padrão de pontos de extremidade consulte [especificando um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
        > [!IMPORTANT]
        >  Adicionar um ponto de extremidade de serviço é opcional ao usar o .NET Framework 4 ou posterior. Nessas versões, se nenhum ponto final for adicionado no código ou na configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço. Para obter mais informações sobre padrão de pontos de extremidade consulte [especificando um endereço de ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  Etapa 4 – Ativa a troca de metadados. Os clientes usarão a troca de metadados para gerar os proxies que serão usados para chamar as operações de serviço. Para habilitar a troca de metadados é criar um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da instância, defina-o do <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade `true`e adicionar o comportamento para o <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` coleção do <xref:System.ServiceModel.ServiceHost> instância.  
  
    5.  Etapa 5 – Abra o <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada. Observe que o código aguarda o usuário pressionar ENTER. Se você não fizer isso, o aplicativo será fechado imediatamente e o serviço será encerrado. Observe também que um bloco try/catch foi usado. Após o <xref:System.ServiceModel.ServiceHost> ter sido instanciado, todos os outros códigos serão colocados em um bloco try/catch. Para obter mais informações sobre segurança Capturando exceções lançadas por <xref:System.ServiceModel.ServiceHost>, consulte [evitando problemas com a instrução Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
### <a name="to-verify-the-service-is-working"></a>Para verificar se o serviço está funcionando  
  
1.  Execute o aplicativo de console GettingStartedHost de dentro do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Ao executar em [!INCLUDE[wv](../../../includes/wv-md.md)] e em sistemas operacionais posteriores, o serviço deverá ser executado com privilégios de administrador. Como o Visual Studio foi executado com privilégios de administrador, GettingStartedHost também é executado com privilégios de administrador. Você também pode iniciar um novo prompt de comando executando-o com privilégios de administrador e execute service.exe dentro dele.  
  
2.  Abra o Internet Explorer e navegue até a página de depuração do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui o contrato e a implementação do serviço das etapas anteriores no tutorial e hospeda o serviço em um aplicativo de console.  
  
 Para compilar isso com um compilador de linha de comando, compilar Iservice1 e Service1 em uma biblioteca de classe referência `System.ServiceModel.dll`. E compile Program.cs em um aplicativo de console.  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
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
'IService1.vb  
Imports System  
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
'Service1.vb  
Imports System  
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
'Module1.vb  
Imports System  
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
>  Os serviços como este exigem permissão para registrar endereços HTTP no computador para escuta. As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP. [!INCLUDE[crabout](../../../includes/crabout-md.md)] como definir reservas de namespace, consulte [Configurando HTTP e HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Ao ser executado no Visual Studio, o service.exe deve ser executado com privilégios de administrador.  
  
 Agora o serviço está sendo executado. Vá para [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Para obter informações de solução de problemas, consulte [o Tutorial de introdução de solução de problemas](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)
