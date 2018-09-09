---
title: Como hospedar e executar um serviço básico do Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227175"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Como hospedar e executar um serviço básico do Windows Communication Foundation
Esta é a terceira de seis tarefas necessárias para criação de um aplicativo do WCF (Windows Communication Foundation). Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
 Este tópico descreve como hospedar um serviço WCF (Windows Communication Foundation) em um aplicativo de console. Este procedimento consiste nas seguintes etapas:  
  
-   Crie um projeto de aplicativo de console para hospedar o serviço.  
  
-   Crie um host de serviço para o serviço.  
  
-   Ative a troca de metadados.  
  
-   Abra o host do serviço.  
  
 Uma lista completa de código escrito nesta tarefa é fornecido no exemplo após o procedimento.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Para criar um novo aplicativo de console para hospedar o serviço  
  
1.  Crie um novo projeto de Aplicativo de Console clicando com o botão direito do mouse na solução Introdução e selecionando **Adicionar**, **Novo Projeto**. Na caixa de diálogo **Adicionar Novo Projeto** no lado esquerdo da caixa de diálogo, selecione **Windows** no **C#** ou no **VB**. Na seção central da caixa de diálogo, selecione **Aplicativo de Console**. Nomeie o projeto como GettingStartedHost.  
  
2.  Defina a estrutura de destino do projeto GettingStartedHost como .NET Framework 4.5 clicando com o botão direito do mouse em **GettingStartedHost** no Gerenciador de Soluções e selecionando **Propriedades**. Na caixa suspensa rotulada **Estrutura de Destino**, selecione **.NET Framework 4.5**. A definição da estrutura de destino de um projeto VB é um pouco diferente. Na caixa de diálogo de propriedades do projeto GettingStartedHost, clique na guia **Compilar** no lado esquerdo da tela e, em seguida, clique no botão **Opções Avançadas de Compilação** no canto inferior esquerdo da caixa de diálogo. Em seguida, selecione **.NET Framework 4.5** na caixa suspensa rotulada **Estrutura de Destino**.  
  
     A definição da estrutura de destino fará com que o [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] recarregue a solução; pressione **OK** quando solicitado.  
  
3.  Adicione uma referência ao projeto GettingStartedLib ao projeto GettingStartedHost clicando com o botão direito do mouse na pasta **Referências** do projeto GettingStartedHost no Gerenciador de Soluções e selecione **Adicionar Referência**. Na caixa de diálogo **Adicionar Referência**, selecione **Solução** no lado esquerdo da caixa de diálogo, selecione GettingStartedLib na seção central da caixa de diálogo e clique em **Adicionar**. Isso torna os tipos definidos em GettingStartedLib disponíveis para o projeto GettingStartedHost.  
  
4.  Adicione uma referência a System.ServiceModel ao projeto GettingStartedHost clicando com o botão direito do mouse na pasta **Referência** do projeto GettingStartedHost no Gerenciador de Soluções e selecione **Adicionar** Referência. Na caixa de diálogo **Adicionar Referência**, selecione **Estrutura** no lado esquerdo da caixa de diálogo. Na caixa de texto Pesquisar Assemblies, digite `System.ServiceModel`. Na seção central da caixa de diálogo, selecione **System.ServiceModel**, clique no botão **Adicionar** e no botão **Fechar**. Salve a solução clicando no botão Salvar Tudo abaixo do menu principal.  
  
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
  
    1.  Etapa 1 - Cria uma instância da classe URI para manter o endereço básico do serviço. Os serviços são identificados por uma URL que contém um endereço básico e um URI opcional. O endereço básico é formatado da seguinte maneira: [transport]://[machine-name or domain][:optional port #]/[optional URI segment] O endereço básico para o serviço de calculadora usa o transporte HTTP, o localhost , a porta 8000 e o segmento de URI "GettingStarted"  
  
    2.  Etapa 2 - Cria uma instância da classe <xref:System.ServiceModel.ServiceHost> para hospedar o serviço. O construtor aceita dois parâmetros, o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.  
  
    3.  Etapa 3 – Cria uma instância de <xref:System.ServiceModel.Description.ServiceEndpoint>. Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço. O construtor <xref:System.ServiceModel.Description.ServiceEndpoint> portanto utiliza o tipo de interface do contrato de serviço, uma associação e um endereço. O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço. A associação usada nesse exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna usada para conectar-se a pontos de extremidade que atendem às especificações de WS-*. Para obter mais informações sobre as associações WCF, confira [Visão geral das associações WCF](../../../docs/framework/wcf/bindings-overview.md). O endereço é adicionado ao endereço básico para identificar o ponto de extremidade. O endereço especificado nesse código é "CalculatorService", portanto, o endereço totalmente qualificado para o ponto de extremidade é `"http://localhost:8000/GettingStarted/CalculatorService"`.  
  
        > [!IMPORTANT]
        >  Adicionar um ponto de extremidade de serviço é opcional ao usar o .NET Framework 4 ou posterior. Nessas versões, se nenhum ponto final for adicionado no código ou na configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço. Para obter mais informações sobre pontos de extremidade padrão, confira [Especificando um endereço do ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md). Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  Etapa 4 – Ativa a troca de metadados. Os clientes usarão a troca de metadados para gerar os proxies que serão usados para chamar as operações de serviço. Para permitir que a troca de metadados crie uma instância de <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, defina sua propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true` e adicione o comportamento à coleção de <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` da instância <xref:System.ServiceModel.ServiceHost>.  
  
    5.  Etapa 5 – Abra o <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada. Observe que o código aguarda o usuário pressionar ENTER. Se você não fizer isso, o aplicativo será fechado imediatamente e o serviço será encerrado. Observe também que um bloco try/catch foi usado. Após o <xref:System.ServiceModel.ServiceHost> ter sido instanciado, todos os outros códigos serão colocados em um bloco try/catch. Para obter mais informações sobre a captura segura de exceções geradas por <xref:System.ServiceModel.ServiceHost>, confira [Evitando problemas com a instrução using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
> [!IMPORTANT]
> Edite App. config em GettingStartedLib para refletir as alterações feitas no código: 
> 1. Altere a linha 14 para `<service name="GettingStartedLib.CalculatorService">`
> 2. Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`
        
### <a name="to-verify-the-service-is-working"></a>Para verificar se o serviço está funcionando  
  
1.  Execute o aplicativo de console GettingStartedHost de dentro do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Ao executar em [!INCLUDE[wv](../../../includes/wv-md.md)] e em sistemas operacionais posteriores, o serviço deverá ser executado com privilégios de administrador. Como o Visual Studio foi executado com privilégios de Administrador, GettingStartedHost também é executado com privilégios de Administrador. Você também pode iniciar um novo prompt de comando executando-o com privilégios de administrador e execute service.exe dentro dele.  
  
2.  Abra o Internet Explorer e navegue até a página de depuração do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inclui o contrato e a implementação do serviço das etapas anteriores no tutorial e hospeda o serviço em um aplicativo de console.  
  
 Para compilar isso com um compilador de linha de comando, compile IService1.cs e Service1.cs em uma biblioteca de classes referenciando `System.ServiceModel.dll`. E compile Program.cs em um aplicativo de console.  
  
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
>  Os serviços como este exigem permissão para registrar endereços HTTP no computador para escuta. As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP. Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Ao ser executado no Visual Studio, o arquivo service.exe precisa ser executado com privilégios de administrador.  
  
 Agora o serviço está sendo executado. Vá para [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Para obter informações sobre solução de problemas, confira [Solução de problemas do tutorial de introdução](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Auto-hospedagem](../../../docs/framework/wcf/samples/self-host.md)
