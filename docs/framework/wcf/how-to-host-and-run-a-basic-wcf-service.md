---
title: 'Tutorial: Hospede e execute um serviço básico da Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184079"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="c0fed-102">Tutorial: Hospede e execute um serviço básico da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c0fed-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="c0fed-103">Este tutorial descreve a terceira das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c0fed-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="c0fed-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="c0fed-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="c0fed-105">A próxima tarefa para criar um aplicativo WCF é hospedar um serviço WCF em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="c0fed-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="c0fed-106">Um serviço WCF expõe um ou mais *pontos finais*, cada um dos quais expõe uma ou mais operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="c0fed-107">Um ponto final de serviço especifica as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="c0fed-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="c0fed-108">Um endereço onde você pode encontrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-108">An address where you can find the service.</span></span>
- <span data-ttu-id="c0fed-109">Uma vinculação que contém as informações que descrevem como um cliente deve se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="c0fed-110">Um contrato que define a funcionalidade que o serviço oferece aos seus clientes.</span><span class="sxs-lookup"><span data-stu-id="c0fed-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="c0fed-111">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="c0fed-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c0fed-112">Crie e configure um projeto de aplicativo de console para hospedar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c0fed-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="c0fed-113">Adicione código para hospedar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c0fed-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="c0fed-114">Atualize o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0fed-114">Update the configuration file.</span></span>
> - <span data-ttu-id="c0fed-115">Inicie o serviço WCF e verifique se está em execução.</span><span class="sxs-lookup"><span data-stu-id="c0fed-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="c0fed-116">Crie e configure um projeto de aplicativo de console para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="c0fed-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="c0fed-117">Crie um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c0fed-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="c0fed-118">No menu **Arquivo,** selecione **Abrir** > **projeto/solução** e navegue até a solução **GettingStarted** criada anteriormente *(GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="c0fed-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="c0fed-119">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-119">Select **Open**.</span></span>

    2. <span data-ttu-id="c0fed-120">No menu **Exibir,** selecione **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="c0fed-121">Na janela **Solution Explorer,** selecione a solução **GettingStarted** (nó superior e selecione **Adicionar** > **novo projeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="c0fed-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="c0fed-122">Na janela **Adicionar novo projeto,** no lado esquerdo, selecione a categoria **Windows Desktop** em **Visual C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="c0fed-123">Selecione o modelo **Console App (.NET Framework)** e insira *GettingStartedHost* para o **Nome**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="c0fed-124">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-124">Select **OK**.</span></span>

2. <span data-ttu-id="c0fed-125">Adicione uma referência no projeto **GettingStartedHost** ao projeto **GettingStartedLib:**</span><span class="sxs-lookup"><span data-stu-id="c0fed-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="c0fed-126">Na janela **'Explorador de soluções',** selecione a pasta **Referências** no projeto **GettingStartedHost** e selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="c0fed-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="c0fed-127">Na caixa de diálogo **Adicionar referência,** em **Projetos** no lado esquerdo da janela, selecione **Solução**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="c0fed-128">Selecione **GettingStartedLib** na seção central da janela e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="c0fed-129">Essa ação torna os tipos definidos no projeto **GettingStartedLib** disponíveis para o projeto **GettingStartedHost.**</span><span class="sxs-lookup"><span data-stu-id="c0fed-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="c0fed-130">Adicione uma referência no projeto **GettingStartedHost** à <xref:System.ServiceModel> montagem:</span><span class="sxs-lookup"><span data-stu-id="c0fed-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="c0fed-131">Na janela **'Explorador de soluções',** selecione a pasta **Referências** no projeto **GettingStartedHost** e selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="c0fed-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="c0fed-132">Na janela **Adicionar referência,** em **Montagens** no lado esquerdo da janela, **selecione Quadro**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="c0fed-133">Selecione **System.ServiceModel**e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="c0fed-134">Salve a solução selecionando **'Salvar todos'** **do arquivo** > .</span><span class="sxs-lookup"><span data-stu-id="c0fed-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="c0fed-135">Adicionar código para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="c0fed-135">Add code to host the service</span></span>

<span data-ttu-id="c0fed-136">Para hospedar o serviço, adicione código para fazer as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c0fed-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="c0fed-137">Crie um URI para o endereço base.</span><span class="sxs-lookup"><span data-stu-id="c0fed-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="c0fed-138">Crie uma instância de classe para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="c0fed-139">Crie um ponto final de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="c0fed-140">Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="c0fed-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="c0fed-141">Abra o host de serviço para ouvir as mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="c0fed-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="c0fed-142">Faça as alterações a seguir ao código:</span><span class="sxs-lookup"><span data-stu-id="c0fed-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="c0fed-143">Abra o arquivo **Program.cs** ou **Module1.vb** no projeto **GettingStartedHost** e substitua seu código pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c0fed-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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

    <span data-ttu-id="c0fed-144">Para obter informações sobre como esse código funciona, consulte [as etapas do programa de hospedagem de serviços](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="c0fed-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="c0fed-145">Atualize as propriedades do projeto:</span><span class="sxs-lookup"><span data-stu-id="c0fed-145">Update the project properties:</span></span>

   1. <span data-ttu-id="c0fed-146">Na janela **'Explorador de soluções',** selecione a pasta **GettingStartedHost** e selecione **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="c0fed-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="c0fed-147">Na página **Propriedades GettingStartedHost,** selecione a guia **Aplicativo:**</span><span class="sxs-lookup"><span data-stu-id="c0fed-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="c0fed-148">Para projetos C#, selecione **GettingStartedHost.Program** na lista **de objetos Iniciar.**</span><span class="sxs-lookup"><span data-stu-id="c0fed-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="c0fed-149">Para projetos Visual Basic, selecione **Service.Program** na lista **de objetos Iniciar.**</span><span class="sxs-lookup"><span data-stu-id="c0fed-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="c0fed-150">No menu **Arquivo,** selecione **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="c0fed-151">Verifique se o serviço está funcionando</span><span class="sxs-lookup"><span data-stu-id="c0fed-151">Verify the service is working</span></span>

1. <span data-ttu-id="c0fed-152">Crie a solução e execute o aplicativo de console **GettingStartedHost** de dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c0fed-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="c0fed-153">O serviço deve ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="c0fed-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="c0fed-154">Como você abriu o Visual Studio com privilégios de administrador, quando executa **o GettingStartedHost** no Visual Studio, o aplicativo também é executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="c0fed-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="c0fed-155">Como alternativa, você pode abrir um novo prompt de comando como administrador (selecione **Mais** > **Executar como administrador** no menu de atalho) e executar **GettingStartedHost.exe** dentro dele.</span><span class="sxs-lookup"><span data-stu-id="c0fed-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="c0fed-156">Abra um navegador da Web e navegue até a página do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="c0fed-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c0fed-157">Serviços como este exigem a permissão adequada para registrar endereços HTTP na máquina para ouvir.</span><span class="sxs-lookup"><span data-stu-id="c0fed-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="c0fed-158">As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP.</span><span class="sxs-lookup"><span data-stu-id="c0fed-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="c0fed-159">Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="c0fed-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="c0fed-160">Etapas do programa de hospedagem de serviços</span><span class="sxs-lookup"><span data-stu-id="c0fed-160">Service hosting program steps</span></span>

<span data-ttu-id="c0fed-161">As etapas do código adicionado para hospedar o serviço são descritas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c0fed-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="c0fed-162">**Passo 1**: Crie `Uri` uma instância da classe para manter o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="c0fed-163">Uma URL que contém um endereço base tem um URI opcional que identifica um serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="c0fed-164">O endereço base é formatado `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`da seguinte forma: .</span><span class="sxs-lookup"><span data-stu-id="c0fed-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="c0fed-165">O endereço base do serviço de calculadora usa o transporte HTTP, localhost, port 8000 e o segmento URI, GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="c0fed-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="c0fed-166">**Passo 2**: Crie <xref:System.ServiceModel.ServiceHost> uma instância da classe, que você usa para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="c0fed-167">A construtora tem dois parâmetros: o tipo da classe que implementa o contrato de serviço e o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="c0fed-168">**Passo 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Criar uma instância.</span><span class="sxs-lookup"><span data-stu-id="c0fed-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="c0fed-169">Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="c0fed-170">O <xref:System.ServiceModel.Description.ServiceEndpoint> construtor é composto pelo tipo de interface de contrato de serviço, uma vinculação e um endereço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="c0fed-171">O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="c0fed-172">A vinculação para <xref:System.ServiceModel.WSHttpBinding>esta amostra é , que é uma ligação incorporada e se conecta a pontos finais que estão de acordo com as especificações WS-\*.</span><span class="sxs-lookup"><span data-stu-id="c0fed-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="c0fed-173">Para obter mais informações sobre as vinculações do WCF, consulte [a visão geral das vinculações do WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c0fed-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="c0fed-174">Você anexa o endereço ao endereço base para identificar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="c0fed-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="c0fed-175">O código especifica o endereço como CalculatorService e o `http://localhost:8000/GettingStarted/CalculatorService`endereço totalmente qualificado para o ponto final como .</span><span class="sxs-lookup"><span data-stu-id="c0fed-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c0fed-176">Para .NET Framework Version 4 e posterior, adicionar um ponto final de serviço é opcional.</span><span class="sxs-lookup"><span data-stu-id="c0fed-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="c0fed-177">Para essas versões, se você não adicionar seu código ou configuração, o WCF adicionará um ponto final padrão para cada combinação de endereço base e contrato implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="c0fed-178">Para obter mais informações sobre pontos finais padrão, consulte [Especificando um endereço de ponto final](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="c0fed-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="c0fed-179">Para obter mais informações sobre pontos finais padrão, vinculações e comportamentos, consulte [Configuração simplificada](simplified-configuration.md) e [configuração simplificada para serviços WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c0fed-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="c0fed-180">**Passo 4**: Habilite a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="c0fed-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="c0fed-181">Os clientes usam a troca de metadados para gerar proxies para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="c0fed-182">Para habilitar a troca <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de metadados, `true`crie uma `ServiceMetadataBehavior` instância, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> defina <xref:System.ServiceModel.ServiceHost> sua <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> propriedade e adicione o objeto à coleção da instância.</span><span class="sxs-lookup"><span data-stu-id="c0fed-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="c0fed-183">**Passo 5** <xref:System.ServiceModel.ServiceHost> : Aberto para ouvir as mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="c0fed-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="c0fed-184">O aplicativo espera que você pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="c0fed-185">Depois que o <xref:System.ServiceModel.ServiceHost>aplicativo instancia, ele executa um bloco de tentativa/captura.</span><span class="sxs-lookup"><span data-stu-id="c0fed-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="c0fed-186">Para obter mais informações sobre a <xref:System.ServiceModel.ServiceHost>captura segura de exceções lançadas, consulte [Use Close e Abort para liberar recursos do cliente WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c0fed-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0fed-187">Quando você adiciona uma biblioteca de serviços WCF, o Visual Studio a hospeda para você se você depurar, iniciando um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="c0fed-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="c0fed-188">Para evitar conflitos, você pode impedir o Visual Studio de hospedar a biblioteca de serviços do WCF.</span><span class="sxs-lookup"><span data-stu-id="c0fed-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="c0fed-189">Selecione o projeto **GettingStartedLib** no **Solution Explorer** e escolha **Propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="c0fed-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="c0fed-190">Selecione **opções WCF** e desmarque **Iniciar o Host de serviço WCF ao depurar outro projeto na mesma solução**.</span><span class="sxs-lookup"><span data-stu-id="c0fed-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0fed-191">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c0fed-191">Next steps</span></span>

<span data-ttu-id="c0fed-192">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="c0fed-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="c0fed-193">Crie e configure um projeto de aplicativo de console para hospedar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c0fed-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="c0fed-194">Adicione código para hospedar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c0fed-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="c0fed-195">Atualize o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0fed-195">Update the configuration file.</span></span>
> - <span data-ttu-id="c0fed-196">Inicie o serviço WCF e verifique se está em execução.</span><span class="sxs-lookup"><span data-stu-id="c0fed-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="c0fed-197">Avance para o próximo tutorial para aprender como criar um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="c0fed-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c0fed-198">Tutorial: Crie um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="c0fed-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
