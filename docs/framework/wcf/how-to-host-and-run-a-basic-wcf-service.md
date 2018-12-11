---
title: 'Como: Hospedar e executar um serviço básico do Windows Communication Foundation'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 710ccd69d7b0f8cd8cd3e04729fd952308a3fb4a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129370"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="de96e-102">Como: Hospedar e executar um serviço básico do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="de96e-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>

<span data-ttu-id="de96e-103">Esta é a terceira de seis tarefas necessárias para criação de um aplicativo do WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="de96e-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="de96e-104">Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="de96e-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="de96e-105">Este tópico descreve como hospedar um serviço WCF (Windows Communication Foundation) em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="de96e-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="de96e-106">Este procedimento consiste nas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="de96e-106">This procedure consists of the following steps:</span></span>

- <span data-ttu-id="de96e-107">Crie um projeto de aplicativo de console para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-107">Create a console application project to host the service.</span></span>

- <span data-ttu-id="de96e-108">Crie um host de serviço para o serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-108">Create a service host for the service.</span></span>

- <span data-ttu-id="de96e-109">Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="de96e-109">Enable metadata exchange.</span></span>

- <span data-ttu-id="de96e-110">Abra o host do serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-110">Open the service host.</span></span>

<span data-ttu-id="de96e-111">Uma lista completa de código escrito nesta tarefa é fornecido no exemplo após o procedimento.</span><span class="sxs-lookup"><span data-stu-id="de96e-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>

## <a name="create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="de96e-112">Criar um novo aplicativo de console para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="de96e-112">Create a new console application to host the service</span></span>

1. <span data-ttu-id="de96e-113">Criar um novo projeto de aplicativo de Console no Visual Studio clicando duas vezes na solução guia de Introdução e selecionando **Add** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="de96e-113">Create a new Console Application project in Visual Studio by right-clicking on the Getting Started solution and selecting **Add** > **New Project**.</span></span> <span data-ttu-id="de96e-114">No **adicionar novo projeto** caixa de diálogo, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual c#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="de96e-114">In the **Add New Project** dialog, on the left-hand side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> <span data-ttu-id="de96e-115">Selecione o **aplicativo de Console (.NET Framework)** modelo e, em seguida, nomeie o projeto **GettingStartedHost**.</span><span class="sxs-lookup"><span data-stu-id="de96e-115">Select the **Console App (.NET Framework)** template, and then name the project **GettingStartedHost**.</span></span>

2. <span data-ttu-id="de96e-116">Adicione uma referência ao projeto GettingStartedLib ao projeto GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="de96e-116">Add a reference to the GettingStartedLib project to the GettingStartedHost project.</span></span> <span data-ttu-id="de96e-117">Clique com botão direito no **referências** pasta sob o projeto GettingStartedHost no **Gerenciador de soluções**e, em seguida, selecione **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="de96e-117">Right-click on the **References** folder under the GettingStartedHost project in **Solution Explorer**, and then select **Add Reference**.</span></span> <span data-ttu-id="de96e-118">No **adicionar referência** caixa de diálogo, selecione **solução** no lado esquerdo da caixa de diálogo, selecione GettingStartedLib na seção central da caixa de diálogo e, em seguida, escolha **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="de96e-118">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog, select GettingStartedLib in the center section of the dialog, and then choose **Add**.</span></span> <span data-ttu-id="de96e-119">Isso torna os tipos definidos em GettingStartedLib disponíveis para o projeto GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="de96e-119">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>

3. <span data-ttu-id="de96e-120">Adicione uma referência a System. ServiceModel ao projeto GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="de96e-120">Add a reference to System.ServiceModel to the GettingStartedHost project.</span></span> <span data-ttu-id="de96e-121">Clique com botão direito do **referências** pasta sob o projeto GettingStartedHost no **Gerenciador de soluções** e selecione **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="de96e-121">Right-click the **References** folder under the GettingStartedHost project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="de96e-122">No **adicionar referência** caixa de diálogo, selecione **Framework** no lado esquerdo da caixa de diálogo, sob **Assemblies**.</span><span class="sxs-lookup"><span data-stu-id="de96e-122">In the **Add Reference** dialog, select **Framework** on the left-hand side of the dialog under **Assemblies**.</span></span> <span data-ttu-id="de96e-123">Localize e selecione **System. ServiceModel**e, em seguida, escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="de96e-123">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> <span data-ttu-id="de96e-124">Salve a solução selecionando **arquivo** > **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="de96e-124">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="host-the-service"></a><span data-ttu-id="de96e-125">O serviço de host</span><span class="sxs-lookup"><span data-stu-id="de96e-125">Host the service</span></span>

<span data-ttu-id="de96e-126">Abra o arquivo Program.cs ou Module.vb e insira o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="de96e-126">Open the Program.cs or Module.vb file and enter the following code:</span></span>

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

<span data-ttu-id="de96e-127">**Etapa 1** -cria uma instância da classe do Uri para manter o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-127">**Step 1** - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="de96e-128">Os serviços são identificados por uma URL que contém um endereço básico e um URI opcional.</span><span class="sxs-lookup"><span data-stu-id="de96e-128">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="de96e-129">O endereço básico é formatado da seguinte maneira: [transport]://[machine-name or domain][:optional port #]/[optional URI segment] O endereço básico para o serviço de calculadora usa o transporte HTTP, o localhost , a porta 8000 e o segmento de URI "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="de96e-129">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>

<span data-ttu-id="de96e-130">**Etapa 2** – cria uma instância do <xref:System.ServiceModel.ServiceHost> classe para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-130">**Step 2** – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="de96e-131">O construtor aceita dois parâmetros, o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-131">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>

<span data-ttu-id="de96e-132">**Etapa 3** – cria um <xref:System.ServiceModel.Description.ServiceEndpoint> instância.</span><span class="sxs-lookup"><span data-stu-id="de96e-132">**Step 3** – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="de96e-133">Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-133">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="de96e-134">O construtor <xref:System.ServiceModel.Description.ServiceEndpoint> portanto utiliza o tipo de interface do contrato de serviço, uma associação e um endereço.</span><span class="sxs-lookup"><span data-stu-id="de96e-134">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="de96e-135">O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-135">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="de96e-136">A associação usada nesse exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna usada para conectar-se a pontos de extremidade que atendem às especificações de WS-\*.</span><span class="sxs-lookup"><span data-stu-id="de96e-136">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="de96e-137">Para obter mais informações sobre as associações WCF, confira [Visão geral das associações WCF](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="de96e-137">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="de96e-138">O endereço é adicionado ao endereço básico para identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="de96e-138">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="de96e-139">O endereço especificado nesse código é "CalculatorService", portanto, o endereço totalmente qualificado para o ponto de extremidade é `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="de96e-139">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

<span data-ttu-id="de96e-140">**Etapa 4** – habilitar a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="de96e-140">**Step 4** – Enable metadata exchange.</span></span> <span data-ttu-id="de96e-141">Os clientes usarão a troca de metadados para gerar os proxies que serão usados para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="de96e-141">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="de96e-142">Para permitir que a troca de metadados crie uma instância de <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, defina sua propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true` e adicione o comportamento à coleção de <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` da instância <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="de96e-142">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

<span data-ttu-id="de96e-143">**Etapa 5** – abra o <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="de96e-143">**Step 5** – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="de96e-144">Observe que o código aguarda o usuário pressionar ENTER.</span><span class="sxs-lookup"><span data-stu-id="de96e-144">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="de96e-145">Se você não fizer isso, o aplicativo será fechado imediatamente e o serviço será encerrado. Observe também que um bloco try/catch foi usado.</span><span class="sxs-lookup"><span data-stu-id="de96e-145">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="de96e-146">Após o <xref:System.ServiceModel.ServiceHost> ter sido instanciado, todos os outros códigos serão colocados em um bloco try/catch.</span><span class="sxs-lookup"><span data-stu-id="de96e-146">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="de96e-147">Para obter mais informações sobre como capturar com segurança exceções geradas pelo <xref:System.ServiceModel.ServiceHost>, consulte [uso Close e Abort para liberar os recursos de cliente do WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)</span><span class="sxs-lookup"><span data-stu-id="de96e-147">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de96e-148">Edite App. config em GettingStartedLib para refletir as alterações feitas no código:</span><span class="sxs-lookup"><span data-stu-id="de96e-148">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span>
> 1. <span data-ttu-id="de96e-149">Altere a linha 14 para `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="de96e-149">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="de96e-150">Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="de96e-150">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="de96e-151">Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="de96e-151">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="de96e-152">Verifique se que o serviço está funcionando</span><span class="sxs-lookup"><span data-stu-id="de96e-152">Verify the service is working</span></span>

1. <span data-ttu-id="de96e-153">Executar o console GettingStartedHost aplicativo de dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="de96e-153">Run the GettingStartedHost console application from inside Visual Studio.</span></span>

   <span data-ttu-id="de96e-154">O serviço deve ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="de96e-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="de96e-155">Porque o Visual Studio foi aberto com privilégios de administrador, o GettingStartedHost também será executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="de96e-155">Because Visual Studio was opened with administrator privileges, GettingStartedHost is also run with administrator privileges.</span></span> <span data-ttu-id="de96e-156">Você também pode abrir um prompt de comando usando a nova **executar como administrador** e executar service.exe dentro dele.</span><span class="sxs-lookup"><span data-stu-id="de96e-156">You can also open a new command prompt using **Run as administrator** and run service.exe within it.</span></span>

2. <span data-ttu-id="de96e-157">Abra um navegador da web e navegue até a página de depuração do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="de96e-157">Open a web browser and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

## <a name="example"></a><span data-ttu-id="de96e-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de96e-158">Example</span></span>

<span data-ttu-id="de96e-159">O exemplo a seguir inclui o contrato e a implementação do serviço das etapas anteriores no tutorial e hospeda o serviço em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="de96e-159">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>

<span data-ttu-id="de96e-160">Para compilar isso com um compilador de linha de comando, compile IService1.cs e Service1.cs em uma biblioteca de classes que faz referência a `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="de96e-160">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library that references `System.ServiceModel.dll`.</span></span> <span data-ttu-id="de96e-161">Compile Program.cs como um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="de96e-161">Compile Program.cs as a console application.</span></span>

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
> <span data-ttu-id="de96e-162">Os serviços como este exigem permissão para registrar endereços HTTP no computador para escuta.</span><span class="sxs-lookup"><span data-stu-id="de96e-162">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="de96e-163">As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP.</span><span class="sxs-lookup"><span data-stu-id="de96e-163">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="de96e-164">Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="de96e-164">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="de96e-165">Ao ser executado no Visual Studio, o arquivo service.exe precisa ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="de96e-165">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>

## <a name="next-steps"></a><span data-ttu-id="de96e-166">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="de96e-166">Next steps</span></span>

<span data-ttu-id="de96e-167">Agora o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="de96e-167">Now the service is running.</span></span> <span data-ttu-id="de96e-168">A próxima tarefa, você criará um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="de96e-168">In the next task, you create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="de96e-169">Como: Criar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="de96e-169">How to: Create a WCF client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

<span data-ttu-id="de96e-170">Para obter informações sobre solução de problemas, confira [Solução de problemas do tutorial de introdução](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="de96e-170">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de96e-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de96e-171">See also</span></span>

- [<span data-ttu-id="de96e-172">Introdução</span><span class="sxs-lookup"><span data-stu-id="de96e-172">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="de96e-173">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="de96e-173">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)