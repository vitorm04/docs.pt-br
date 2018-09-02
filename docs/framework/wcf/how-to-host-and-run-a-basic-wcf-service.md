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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404665"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="398a9-102">Como hospedar e executar um serviço básico do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="398a9-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="398a9-103">Esta é a terceira de seis tarefas necessárias para criação de um aplicativo do WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="398a9-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="398a9-104">Para obter uma visão geral de todas as seis tarefas, confira o tópico [Tutorial de introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="398a9-105">Este tópico descreve como hospedar um serviço WCF (Windows Communication Foundation) em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="398a9-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="398a9-106">Este procedimento consiste nas seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="398a9-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="398a9-107">Crie um projeto de aplicativo de console para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="398a9-108">Crie um host de serviço para o serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="398a9-109">Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="398a9-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="398a9-110">Abra o host do serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-110">Open the service host.</span></span>  
  
 <span data-ttu-id="398a9-111">Uma lista completa de código escrito nesta tarefa é fornecido no exemplo após o procedimento.</span><span class="sxs-lookup"><span data-stu-id="398a9-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="398a9-112">Para criar um novo aplicativo de console para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="398a9-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="398a9-113">Crie um novo projeto de Aplicativo de Console clicando com o botão direito do mouse na solução Introdução e selecionando **Adicionar**, **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="398a9-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="398a9-114">Na caixa de diálogo **Adicionar Novo Projeto** no lado esquerdo da caixa de diálogo, selecione **Windows** no **C#** ou no **VB**.</span><span class="sxs-lookup"><span data-stu-id="398a9-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="398a9-115">Na seção central da caixa de diálogo, selecione **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="398a9-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="398a9-116">Nomeie o projeto como GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="398a9-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="398a9-117">Defina a estrutura de destino do projeto GettingStartedHost como .NET Framework 4.5 clicando com o botão direito do mouse em **GettingStartedHost** no Gerenciador de Soluções e selecionando **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="398a9-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="398a9-118">Na caixa suspensa rotulada **Estrutura de Destino**, selecione **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="398a9-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="398a9-119">A definição da estrutura de destino de um projeto VB é um pouco diferente. Na caixa de diálogo de propriedades do projeto GettingStartedHost, clique na guia **Compilar** no lado esquerdo da tela e, em seguida, clique no botão **Opções Avançadas de Compilação** no canto inferior esquerdo da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="398a9-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="398a9-120">Em seguida, selecione **.NET Framework 4.5** na caixa suspensa rotulada **Estrutura de Destino**.</span><span class="sxs-lookup"><span data-stu-id="398a9-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="398a9-121">A definição da estrutura de destino fará com que o [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] recarregue a solução; pressione **OK** quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="398a9-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="398a9-122">Adicione uma referência ao projeto GettingStartedLib ao projeto GettingStartedHost clicando com o botão direito do mouse na pasta **Referências** do projeto GettingStartedHost no Gerenciador de Soluções e selecione **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="398a9-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="398a9-123">Na caixa de diálogo **Adicionar Referência**, selecione **Solução** no lado esquerdo da caixa de diálogo, selecione GettingStartedLib na seção central da caixa de diálogo e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="398a9-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="398a9-124">Isso torna os tipos definidos em GettingStartedLib disponíveis para o projeto GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="398a9-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="398a9-125">Adicione uma referência a System.ServiceModel ao projeto GettingStartedHost clicando com o botão direito do mouse na pasta **Referência** do projeto GettingStartedHost no Gerenciador de Soluções e selecione **Adicionar** Referência.</span><span class="sxs-lookup"><span data-stu-id="398a9-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="398a9-126">Na caixa de diálogo **Adicionar Referência**, selecione **Estrutura** no lado esquerdo da caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="398a9-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="398a9-127">Na caixa de texto Pesquisar Assemblies, digite `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="398a9-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="398a9-128">Na seção central da caixa de diálogo, selecione **System.ServiceModel**, clique no botão **Adicionar** e no botão **Fechar**.</span><span class="sxs-lookup"><span data-stu-id="398a9-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="398a9-129">Salve a solução clicando no botão Salvar Tudo abaixo do menu principal.</span><span class="sxs-lookup"><span data-stu-id="398a9-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="398a9-130">Para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="398a9-130">To host the service</span></span>  
  
-   <span data-ttu-id="398a9-131">Abra o arquivo Program.cs ou Module.vb e insira o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="398a9-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
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
  
    1.  <span data-ttu-id="398a9-132">Etapa 1 - Cria uma instância da classe URI para manter o endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="398a9-133">Os serviços são identificados por uma URL que contém um endereço básico e um URI opcional.</span><span class="sxs-lookup"><span data-stu-id="398a9-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="398a9-134">O endereço básico é formatado da seguinte maneira: [transport]://[machine-name or domain][:optional port #]/[optional URI segment] O endereço básico para o serviço de calculadora usa o transporte HTTP, o localhost , a porta 8000 e o segmento de URI "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="398a9-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="398a9-135">Etapa 2 - Cria uma instância da classe <xref:System.ServiceModel.ServiceHost> para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="398a9-136">O construtor aceita dois parâmetros, o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="398a9-137">Etapa 3 – Cria uma instância de <xref:System.ServiceModel.Description.ServiceEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="398a9-137">Step 3 – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="398a9-138">Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="398a9-139">O construtor <xref:System.ServiceModel.Description.ServiceEndpoint> portanto utiliza o tipo de interface do contrato de serviço, uma associação e um endereço.</span><span class="sxs-lookup"><span data-stu-id="398a9-139">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="398a9-140">O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="398a9-141">A associação usada nesse exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna usada para conectar-se a pontos de extremidade que atendem às especificações de WS-\*.</span><span class="sxs-lookup"><span data-stu-id="398a9-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="398a9-142">Para obter mais informações sobre as associações WCF, confira [Visão geral das associações WCF](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="398a9-143">O endereço é adicionado ao endereço básico para identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="398a9-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="398a9-144">O endereço especificado nesse código é "CalculatorService", portanto, o endereço totalmente qualificado para o ponto de extremidade é `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="398a9-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="398a9-145">Adicionar um ponto de extremidade de serviço é opcional ao usar o .NET Framework 4 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="398a9-145">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="398a9-146">Nessas versões, se nenhum ponto final for adicionado no código ou na configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-146">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="398a9-147">Para obter mais informações sobre pontos de extremidade padrão, confira [Especificando um endereço do ponto de extremidade](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-147">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="398a9-148">Para obter mais informações sobre pontos de extremidade, associações e comportamentos padrão, confira [Configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [Configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-148">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="398a9-149">Etapa 4 – Ativa a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="398a9-149">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="398a9-150">Os clientes usarão a troca de metadados para gerar os proxies que serão usados para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="398a9-150">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="398a9-151">Para permitir que a troca de metadados crie uma instância de <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, defina sua propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> como `true` e adicione o comportamento à coleção de <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` da instância <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="398a9-151">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="398a9-152">Etapa 5 – Abra o <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="398a9-152">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="398a9-153">Observe que o código aguarda o usuário pressionar ENTER.</span><span class="sxs-lookup"><span data-stu-id="398a9-153">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="398a9-154">Se você não fizer isso, o aplicativo será fechado imediatamente e o serviço será encerrado. Observe também que um bloco try/catch foi usado.</span><span class="sxs-lookup"><span data-stu-id="398a9-154">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="398a9-155">Após o <xref:System.ServiceModel.ServiceHost> ter sido instanciado, todos os outros códigos serão colocados em um bloco try/catch.</span><span class="sxs-lookup"><span data-stu-id="398a9-155">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="398a9-156">Para obter mais informações sobre a captura segura de exceções geradas por <xref:System.ServiceModel.ServiceHost>, confira [Evitando problemas com a instrução using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="398a9-156">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="398a9-157">Edite App. config em GettingStartedLib para refletir as alterações feitas no código:</span><span class="sxs-lookup"><span data-stu-id="398a9-157">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span> 
> 1. <span data-ttu-id="398a9-158">Altere a linha 14 para `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="398a9-158">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="398a9-159">Altere a linha 17 para `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="398a9-159">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="398a9-160">Altere a linha 22 para `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="398a9-160">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>
        
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="398a9-161">Para verificar se o serviço está funcionando</span><span class="sxs-lookup"><span data-stu-id="398a9-161">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="398a9-162">Execute o aplicativo de console GettingStartedHost de dentro do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="398a9-162">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="398a9-163">Ao executar em [!INCLUDE[wv](../../../includes/wv-md.md)] e em sistemas operacionais posteriores, o serviço deverá ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="398a9-163">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="398a9-164">Como o Visual Studio foi executado com privilégios de Administrador, GettingStartedHost também é executado com privilégios de Administrador.</span><span class="sxs-lookup"><span data-stu-id="398a9-164">Because Visual Studio was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="398a9-165">Você também pode iniciar um novo prompt de comando executando-o com privilégios de administrador e execute service.exe dentro dele.</span><span class="sxs-lookup"><span data-stu-id="398a9-165">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="398a9-166">Abra o Internet Explorer e navegue até a página de depuração do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="398a9-166">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="398a9-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398a9-167">Example</span></span>  
 <span data-ttu-id="398a9-168">O exemplo a seguir inclui o contrato e a implementação do serviço das etapas anteriores no tutorial e hospeda o serviço em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="398a9-168">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="398a9-169">Para compilar isso com um compilador de linha de comando, compile IService1.cs e Service1.cs em uma biblioteca de classes referenciando `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="398a9-169">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="398a9-170">E compile Program.cs em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="398a9-170">And compile Program.cs to a console application.</span></span>  
  
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
>  <span data-ttu-id="398a9-171">Os serviços como este exigem permissão para registrar endereços HTTP no computador para escuta.</span><span class="sxs-lookup"><span data-stu-id="398a9-171">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="398a9-172">As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP.</span><span class="sxs-lookup"><span data-stu-id="398a9-172">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="398a9-173">Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-173">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="398a9-174">Ao ser executado no Visual Studio, o arquivo service.exe precisa ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="398a9-174">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="398a9-175">Agora o serviço está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="398a9-175">Now the service is running.</span></span> <span data-ttu-id="398a9-176">Vá para [Como criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-176">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="398a9-177">Para obter informações sobre solução de problemas, confira [Solução de problemas do tutorial de introdução](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="398a9-177">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="398a9-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="398a9-178">See Also</span></span>  
 [<span data-ttu-id="398a9-179">Introdução</span><span class="sxs-lookup"><span data-stu-id="398a9-179">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="398a9-180">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="398a9-180">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
