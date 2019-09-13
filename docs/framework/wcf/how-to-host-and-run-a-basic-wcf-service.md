---
title: 'Tutorial: Hospedar e executar um serviço de Windows Communication Foundation básico'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928720"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="aff7b-102">Tutorial: Hospedar e executar um serviço de Windows Communication Foundation básico</span><span class="sxs-lookup"><span data-stu-id="aff7b-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="aff7b-103">Este tutorial descreve a terceira das cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF).</span><span class="sxs-lookup"><span data-stu-id="aff7b-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="aff7b-104">Para obter uma visão geral dos tutoriais, [consulte o tutorial: Introdução aos aplicativos](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="aff7b-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="aff7b-105">A próxima tarefa para criar um aplicativo WCF é hospedar um serviço WCF em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="aff7b-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="aff7b-106">Um serviço WCF expõe um ou mais *pontos de extremidade*, cada um dos quais expõe uma ou mais operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="aff7b-107">Um ponto de extremidade de serviço especifica as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="aff7b-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="aff7b-108">Um endereço onde você pode encontrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-108">An address where you can find the service.</span></span>
- <span data-ttu-id="aff7b-109">Uma associação que contém as informações que descrevem como um cliente deve se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="aff7b-110">Um contrato que define a funcionalidade que o serviço fornece aos seus clientes.</span><span class="sxs-lookup"><span data-stu-id="aff7b-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="aff7b-111">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="aff7b-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="aff7b-112">Criar e configurar um projeto de aplicativo de console para hospedar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="aff7b-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="aff7b-113">Adicione o código para hospedar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="aff7b-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="aff7b-114">Atualize o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="aff7b-114">Update the configuration file.</span></span>
> - <span data-ttu-id="aff7b-115">Inicie o serviço WCF e verifique se ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="aff7b-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="aff7b-116">Criar e configurar um projeto de aplicativo de console para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="aff7b-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="aff7b-117">Criar um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="aff7b-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="aff7b-118">No menu **arquivo** , selecione **abrir** > **projeto/solução** e navegue até a solução **gettingstarted** que você criou anteriormente (*gettingstarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="aff7b-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="aff7b-119">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-119">Select **Open**.</span></span>

    2. <span data-ttu-id="aff7b-120">No menu **Exibir** , selecione **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="aff7b-121">Na janela **Gerenciador de soluções** , selecione a solução **gettingstarted** (nó superior) e, em seguida, selecione **Adicionar** > **novo projeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="aff7b-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="aff7b-122">Na janela **Adicionar novo projeto** , no lado esquerdo, selecione a categoria **área de trabalho do Windows** em  **C# Visual** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="aff7b-123">Selecione o modelo **aplicativo de console (.NET Framework)** e digite *GettingStartedHost* para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="aff7b-124">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-124">Select **OK**.</span></span>

2. <span data-ttu-id="aff7b-125">Adicione uma referência no projeto **GettingStartedHost** ao projeto **GettingStartedLib** :</span><span class="sxs-lookup"><span data-stu-id="aff7b-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="aff7b-126">Na janela **Gerenciador de soluções** , selecione a pasta **referências** no projeto **GettingStartedHost** e, em seguida, selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="aff7b-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="aff7b-127">Na caixa de diálogo **Adicionar referência** , em **projetos** no lado esquerdo da janela, selecione **solução**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="aff7b-128">Selecione **GettingStartedLib** na seção central da janela e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="aff7b-129">Essa ação torna os tipos definidos no projeto **GettingStartedLib** disponíveis para o projeto **GettingStartedHost** .</span><span class="sxs-lookup"><span data-stu-id="aff7b-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="aff7b-130">Adicione uma referência no projeto **GettingStartedHost** ao <xref:System.ServiceModel> assembly:</span><span class="sxs-lookup"><span data-stu-id="aff7b-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="aff7b-131">Na janela **Gerenciador de soluções** , selecione a pasta **referências** no projeto **GettingStartedHost** e, em seguida, selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="aff7b-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="aff7b-132">Na janela **Adicionar referência** , em **assemblies** no lado esquerdo da janela, selecione **estrutura**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="aff7b-133">Selecione **System. ServiceModel**e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="aff7b-134">Salve a solução selecionando **arquivo** > **salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="aff7b-135">Adicionar código para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="aff7b-135">Add code to host the service</span></span>

<span data-ttu-id="aff7b-136">Para hospedar o serviço, você adiciona código para realizar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="aff7b-136">To host the service, you add code to do the following steps:</span></span> 

1. <span data-ttu-id="aff7b-137">Crie um URI para o endereço base.</span><span class="sxs-lookup"><span data-stu-id="aff7b-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="aff7b-138">Crie uma instância de classe para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="aff7b-139">Criar um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="aff7b-140">Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="aff7b-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="aff7b-141">Abra o host de serviço para escutar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="aff7b-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="aff7b-142">Faça as seguintes alterações no código:</span><span class="sxs-lookup"><span data-stu-id="aff7b-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="aff7b-143">Abra o arquivo **Program.cs** ou **Module1. vb** no projeto **GettingStartedHost** e substitua seu código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="aff7b-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
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
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    <span data-ttu-id="aff7b-144">Para obter informações sobre como esse código funciona, consulte [etapas do programa de Hospedagem de serviço](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="aff7b-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="aff7b-145">Atualize as propriedades do projeto:</span><span class="sxs-lookup"><span data-stu-id="aff7b-145">Update the project properties:</span></span>

   1. <span data-ttu-id="aff7b-146">Na janela **Gerenciador de soluções** , selecione a pasta **GettingStartedHost** e, em seguida, selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="aff7b-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="aff7b-147">Na página Propriedades do **GettingStartedHost** , selecione a guia **aplicativo** :</span><span class="sxs-lookup"><span data-stu-id="aff7b-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="aff7b-148">Para C# projetos, selecione **GettingStartedHost. Program** na lista **objeto de inicialização** .</span><span class="sxs-lookup"><span data-stu-id="aff7b-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="aff7b-149">Para projetos Visual Basic, selecione **Service. Program** na lista **objeto de inicialização** .</span><span class="sxs-lookup"><span data-stu-id="aff7b-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="aff7b-150">No menu **arquivo** , selecione **salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="aff7b-151">Verifique se o serviço está funcionando</span><span class="sxs-lookup"><span data-stu-id="aff7b-151">Verify the service is working</span></span>

1. <span data-ttu-id="aff7b-152">Compile a solução e, em seguida, execute o aplicativo de console **GettingStartedHost** de dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aff7b-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="aff7b-153">O serviço deve ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="aff7b-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="aff7b-154">Como você abriu o Visual Studio com privilégios de administrador, ao executar o **GettingStartedHost** no Visual Studio, o aplicativo também é executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="aff7b-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="aff7b-155">Como alternativa, você pode abrir um novo prompt de comando como administrador (selecione **mais** > **Executar como administrador** no menu de atalho) e execute **GettingStartedHost. exe** nele.</span><span class="sxs-lookup"><span data-stu-id="aff7b-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="aff7b-156">Abra um navegador da Web e navegue até a página do serviço `http://localhost:8000/GettingStarted/CalculatorService`em.</span><span class="sxs-lookup"><span data-stu-id="aff7b-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="aff7b-157">Serviços como este exigem a permissão adequada para registrar endereços HTTP no computador para escuta.</span><span class="sxs-lookup"><span data-stu-id="aff7b-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="aff7b-158">As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP.</span><span class="sxs-lookup"><span data-stu-id="aff7b-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="aff7b-159">Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 

## <a name="service-hosting-program-steps"></a><span data-ttu-id="aff7b-160">Etapas do programa de Hospedagem de serviço</span><span class="sxs-lookup"><span data-stu-id="aff7b-160">Service hosting program steps</span></span>

<span data-ttu-id="aff7b-161">As etapas no código que você adicionou para hospedar o serviço são descritas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="aff7b-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="aff7b-162">**Etapa 1**: Crie uma instância da `Uri` classe para manter o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="aff7b-163">Uma URL que contém um endereço base tem um URI opcional que identifica um serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="aff7b-164">O endereço base é formatado da seguinte maneira `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`:.</span><span class="sxs-lookup"><span data-stu-id="aff7b-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="aff7b-165">O endereço base para o serviço de calculadora usa o transporte HTTP, localhost, a porta 8000 e o segmento URI, GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="aff7b-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="aff7b-166">**Etapa 2**: Crie uma instância da <xref:System.ServiceModel.ServiceHost> classe, que você usa para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="aff7b-167">O construtor usa dois parâmetros: o tipo da classe que implementa o contrato de serviço e o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="aff7b-168">**Etapa 3**: Crie uma instância de <xref:System.ServiceModel.Description.ServiceEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="aff7b-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="aff7b-169">Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="aff7b-170">O <xref:System.ServiceModel.Description.ServiceEndpoint> Construtor é composto pelo tipo de interface do contrato de serviço, uma associação e um endereço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="aff7b-171">O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="aff7b-172">A associação para este exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma ligação interna e se conecta a pontos de extremidade que estão em conformidade com as especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="aff7b-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="aff7b-173">Para obter mais informações sobre associações do WCF, consulte [visão geral de associações do WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="aff7b-174">Você acrescenta o endereço ao endereço base para identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="aff7b-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="aff7b-175">O código especifica o endereço como CalculatorService e o endereço totalmente qualificado para o ponto de `http://localhost:8000/GettingStarted/CalculatorService`extremidade como.</span><span class="sxs-lookup"><span data-stu-id="aff7b-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="aff7b-176">Para .NET Framework versão 4 e posterior, adicionar um ponto de extremidade de serviço é opcional.</span><span class="sxs-lookup"><span data-stu-id="aff7b-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="aff7b-177">Para essas versões, se você não adicionar seu código ou configuração, o WCF adicionará um ponto de extremidade padrão para cada combinação de endereço base e contrato implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="aff7b-178">Para obter mais informações sobre pontos de extremidade padrão, consulte [especificando um endereço de ponto de extremidades](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="aff7b-179">Para obter mais informações sobre pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](simplified-configuration.md) e [configuração simplificada para serviços WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="aff7b-180">**Etapa 4**: Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="aff7b-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="aff7b-181">Os clientes usam a troca de metadados para gerar proxies para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="aff7b-182">Para habilitar a troca de metadados, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> crie uma instância, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> defina sua `true`Propriedade como e <xref:System.ServiceModel.ServiceHost> Adicione `ServiceMetadataBehavior` o objeto à <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção da instância.</span><span class="sxs-lookup"><span data-stu-id="aff7b-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="aff7b-183">**Etapa 5**: Abrir <xref:System.ServiceModel.ServiceHost> para escutar mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="aff7b-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="aff7b-184">O aplicativo aguarda até que você pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="aff7b-185">Depois que o aplicativo instancia <xref:System.ServiceModel.ServiceHost>, ele executa um bloco try/catch.</span><span class="sxs-lookup"><span data-stu-id="aff7b-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="aff7b-186">Para obter mais informações sobre a captura segura de exceções <xref:System.ServiceModel.ServiceHost>lançadas pelo, consulte [usar fechar e anular para liberar recursos do cliente WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="aff7b-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aff7b-187">Quando você adiciona uma biblioteca de serviços WCF, o Visual Studio a hospeda para você se depurá-la iniciando um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="aff7b-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="aff7b-188">Para evitar conflitos, você pode impedir que o Visual Studio hospede a biblioteca de serviços do WCF.</span><span class="sxs-lookup"><span data-stu-id="aff7b-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
>
> 1. <span data-ttu-id="aff7b-189">Selecione o projeto **GettingStartedLib** em **Gerenciador de soluções** e escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="aff7b-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="aff7b-190">Selecione **Opções do WCF** e desmarque **Iniciar host de serviço WCF ao depurar outro projeto na mesma solução**.</span><span class="sxs-lookup"><span data-stu-id="aff7b-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="aff7b-191">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="aff7b-191">Next steps</span></span>

<span data-ttu-id="aff7b-192">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="aff7b-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="aff7b-193">Criar e configurar um projeto de aplicativo de console para hospedar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="aff7b-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="aff7b-194">Adicione o código para hospedar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="aff7b-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="aff7b-195">Atualize o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="aff7b-195">Update the configuration file.</span></span>
> - <span data-ttu-id="aff7b-196">Inicie o serviço WCF e verifique se ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="aff7b-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="aff7b-197">Avance para o próximo tutorial para aprender a criar um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="aff7b-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aff7b-198">Tutorial: Criar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="aff7b-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
