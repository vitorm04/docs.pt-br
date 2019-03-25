---
title: 'Tutorial: Hospedar e executar um serviço básico do Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 38fd9b89e2719be8ce4d33b1b50f68171d587369
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410089"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="a83d6-102">Tutorial: Hospedar e executar um serviço básico do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a83d6-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="a83d6-103">Este tutorial descreve o terceiro de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a83d6-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a83d6-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a83d6-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="a83d6-105">A próxima tarefa para a criação de um aplicativo WCF é hospedar um serviço WCF em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a83d6-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="a83d6-106">Um serviço WCF expõe uma ou mais *pontos de extremidade*, cada um deles expõe uma ou mais operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="a83d6-107">Um ponto de extremidade de serviço Especifica as informações a seguir:</span><span class="sxs-lookup"><span data-stu-id="a83d6-107">A service endpoint specifies the following information:</span></span> 
- <span data-ttu-id="a83d6-108">Um endereço em que você pode encontrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-108">An address where you can find the service.</span></span>
- <span data-ttu-id="a83d6-109">Uma associação que contém as informações que descrevem como um cliente deve se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="a83d6-110">Um contrato que define a funcionalidade que o serviço fornece a seus clientes.</span><span class="sxs-lookup"><span data-stu-id="a83d6-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="a83d6-111">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="a83d6-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="a83d6-112">Criar e configurar um projeto de aplicativo de console para hospedar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a83d6-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="a83d6-113">Adicione código para hospedar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a83d6-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="a83d6-114">Atualize o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a83d6-114">Update the configuration file.</span></span>
> - <span data-ttu-id="a83d6-115">Inicie o serviço do WCF e verificar se ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="a83d6-115">Start the WCF service and verify it's running.</span></span>


## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="a83d6-116">Criar e configurar um projeto de aplicativo de console para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="a83d6-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="a83d6-117">Crie um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a83d6-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="a83d6-118">Dos **arquivo** menu, selecione **abra** > **projeto/solução** e navegue até o **GettingStarted** solução você criado anteriormente (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="a83d6-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="a83d6-119">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-119">Select **Open**.</span></span>

    2. <span data-ttu-id="a83d6-120">Dos **modo de exibição** menu, selecione **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="a83d6-121">No **Gerenciador de soluções** janela, selecione a **GettingStarted** solução (nó superior) e, em seguida, selecione **Add** > **denovoprojeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="a83d6-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="a83d6-122">No **adicionar novo projeto** janela, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual C#**  ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="a83d6-123">Selecione o **aplicativo de Console (.NET Framework)** modelo e insira *GettingStartedHost* para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="a83d6-124">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-124">Select **OK**.</span></span>

2. <span data-ttu-id="a83d6-125">Adicionar uma referência na **GettingStartedHost** do projeto para o **GettingStartedLib** projeto:</span><span class="sxs-lookup"><span data-stu-id="a83d6-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="a83d6-126">No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedHost** do projeto e, em seguida, selecione **Add Reference** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="a83d6-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="a83d6-127">No **adicionar referência** caixa de diálogo, em **projetos** no lado esquerdo da janela, selecione **solução**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="a83d6-128">Selecione **GettingStartedLib** na seção central da janela e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="a83d6-129">Essa ação faz com que os tipos definidos na **GettingStartedLib** projeto disponível para o **GettingStartedHost** projeto.</span><span class="sxs-lookup"><span data-stu-id="a83d6-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="a83d6-130">Adicionar uma referência na **GettingStartedHost** do projeto para o <xref:System.ServiceModel> assembly:</span><span class="sxs-lookup"><span data-stu-id="a83d6-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="a83d6-131">No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedHost** do projeto e, em seguida, selecione **Add Reference** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="a83d6-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="a83d6-132">No **adicionar referência** janela, em **Assemblies** no lado esquerdo da janela, selecione **Framework**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="a83d6-133">Selecione **System. ServiceModel**e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="a83d6-134">Salve a solução selecionando **arquivo** > **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="a83d6-135">Adicione código para hospedar o serviço</span><span class="sxs-lookup"><span data-stu-id="a83d6-135">Add code to host the service</span></span>

<span data-ttu-id="a83d6-136">Para hospedar o serviço, é possível adicionar código para fazer as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="a83d6-136">To host the service, you add code to do the following steps:</span></span> 
   1. <span data-ttu-id="a83d6-137">Crie um URI para o endereço básico.</span><span class="sxs-lookup"><span data-stu-id="a83d6-137">Create a URI for the base address.</span></span>
   2. <span data-ttu-id="a83d6-138">Crie uma instância da classe para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-138">Create a class instance for hosting the service.</span></span>
   3. <span data-ttu-id="a83d6-139">Crie um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-139">Create a service endpoint.</span></span>
   4. <span data-ttu-id="a83d6-140">Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="a83d6-140">Enable metadata exchange.</span></span>
   5. <span data-ttu-id="a83d6-141">Abra o host de serviço para escutar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="a83d6-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="a83d6-142">Faça as seguintes alterações no código:</span><span class="sxs-lookup"><span data-stu-id="a83d6-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="a83d6-143">Abra o **Program.cs** ou **Module1.vb** de arquivo no **GettingStartedHost** do projeto e substitua seu código com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a83d6-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
    
    <span data-ttu-id="a83d6-144">Para obter informações sobre como esse código funciona, consulte [serviço de hospedagem de etapas de programa](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="a83d6-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>


2. <span data-ttu-id="a83d6-145">Atualize as propriedades do projeto:</span><span class="sxs-lookup"><span data-stu-id="a83d6-145">Update the project properties:</span></span>

   1. <span data-ttu-id="a83d6-146">No **Gerenciador de soluções** janela, selecione a **GettingStartedHost** pasta e, em seguida, selecione **propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="a83d6-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="a83d6-147">Sobre o **GettingStartedHost** página de propriedades, selecione a **aplicativo** guia:</span><span class="sxs-lookup"><span data-stu-id="a83d6-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="a83d6-148">Para C# projetos, selecionados **GettingStartedHost.Program** do **objeto de inicialização** lista.</span><span class="sxs-lookup"><span data-stu-id="a83d6-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="a83d6-149">Para projetos do Visual Basic, selecione **Service.Program** da **objeto de inicialização** lista.</span><span class="sxs-lookup"><span data-stu-id="a83d6-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="a83d6-150">Dos **arquivo** menu, selecione **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-150">From the **File** menu, select **Save All**.</span></span>


## <a name="verify-the-service-is-working"></a><span data-ttu-id="a83d6-151">Verifique se que o serviço está funcionando</span><span class="sxs-lookup"><span data-stu-id="a83d6-151">Verify the service is working</span></span>

1. <span data-ttu-id="a83d6-152">Compile a solução e, em seguida, execute as **GettingStartedHost** console do aplicativo de dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a83d6-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="a83d6-153">O serviço deve ser executado com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="a83d6-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="a83d6-154">Porque o Visual Studio é aberto com privilégios de administrador, quando você executa **GettingStartedHost** no Visual Studio, o aplicativo é executado com privilégios de administrador também.</span><span class="sxs-lookup"><span data-stu-id="a83d6-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="a83d6-155">Como alternativa, você pode abrir um novo prompt de comando como administrador (selecione **mais** > **executar como administrador** no menu de atalho) e execute **GettingStartedHost.exe**  dentro dele.</span><span class="sxs-lookup"><span data-stu-id="a83d6-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="a83d6-156">Abra um navegador da web e navegue até a página do serviço em `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="a83d6-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="a83d6-157">Serviços como este exigem a permissão apropriada para registrar endereços HTTP no computador para escuta.</span><span class="sxs-lookup"><span data-stu-id="a83d6-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="a83d6-158">As contas de administrador têm essa permissão, mas as contas de não administrador devem ter permissão para namespaces de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a83d6-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="a83d6-159">Para obter mais informações sobre como configurar reservas de namespace, confira [Configurando HTTP e HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="a83d6-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 


## <a name="service-hosting-program-steps"></a><span data-ttu-id="a83d6-160">Etapas de programa de hospedagem de serviço</span><span class="sxs-lookup"><span data-stu-id="a83d6-160">Service hosting program steps</span></span>

<span data-ttu-id="a83d6-161">As etapas no código que você adicionou ao host de serviço são descritas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a83d6-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="a83d6-162">**Etapa 1**: Criar uma instância da `Uri` classe para manter o endereço base do serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="a83d6-163">Uma URL que contém um endereço base tem um URI opcional que identifica um serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="a83d6-164">O endereço básico é formatado da seguinte maneira: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span><span class="sxs-lookup"><span data-stu-id="a83d6-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="a83d6-165">O endereço base para o serviço da Calculadora usa o transporte HTTP, localhost, porta 8000 e o segmento do URI, GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="a83d6-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="a83d6-166">**Etapa 2**: Criar uma instância da <xref:System.ServiceModel.ServiceHost> classe, que você pode usar para hospedar o serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="a83d6-167">O construtor aceita dois parâmetros: o tipo da classe que implementa o contrato de serviço e o endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="a83d6-168">**Etapa 3**: Crie uma instância de <xref:System.ServiceModel.Description.ServiceEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="a83d6-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="a83d6-169">Um ponto de extremidade de serviço é composto de um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="a83d6-170">O <xref:System.ServiceModel.Description.ServiceEndpoint> construtor é composto de um endereço, uma associação e o tipo de interface de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="a83d6-171">O contrato de serviço é `ICalculator`, que você definiu e implementou no tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="a83d6-172">A associação para este exemplo é <xref:System.ServiceModel.WSHttpBinding>, que é uma associação interna e conecta-se aos pontos de extremidade que estão em conformidade com o WS-\* especificações.</span><span class="sxs-lookup"><span data-stu-id="a83d6-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="a83d6-173">Para obter mais informações sobre associações WCF, consulte [visão geral de associações do WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a83d6-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="a83d6-174">Você pode acrescentar o endereço para o endereço básico para identificar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a83d6-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="a83d6-175">O código especifica o endereço como CalculatorService e o endereço totalmente qualificado para o ponto de extremidade como `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="a83d6-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a83d6-176">Para o .NET Framework versão 4 e posterior, adicionar um ponto de extremidade de serviço é opcional.</span><span class="sxs-lookup"><span data-stu-id="a83d6-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="a83d6-177">Para essas versões, se você não adicionar seu código ou a configuração, o WCF adiciona um ponto de extremidade padrão para cada combinação de endereço básico e contrato implementada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="a83d6-178">Para obter mais informações sobre pontos de extremidade padrão, consulte [especificação de um endereço de ponto de extremidade](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="a83d6-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="a83d6-179">Para obter mais informações sobre pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificado](simplified-configuration.md) e [configuração simplificado para os serviços WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a83d6-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="a83d6-180">**Etapa 4**: Ative a troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="a83d6-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="a83d6-181">Os clientes usam a troca de metadados para gerar proxies para chamar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="a83d6-182">Para habilitar a troca de metadados, criar uma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da instância, defina sua <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> propriedade a ser `true`e adicione o `ServiceMetadataBehavior` do objeto para o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> coleção da <xref:System.ServiceModel.ServiceHost> instância.</span><span class="sxs-lookup"><span data-stu-id="a83d6-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="a83d6-183">**Etapa 5**: Abra <xref:System.ServiceModel.ServiceHost> para escutar as mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="a83d6-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="a83d6-184">O aplicativo espera que você pressionar **Enter**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="a83d6-185">Depois que o aplicativo cria uma instância <xref:System.ServiceModel.ServiceHost>, ele executa um bloco try/catch.</span><span class="sxs-lookup"><span data-stu-id="a83d6-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="a83d6-186">Para obter mais informações sobre como capturar com segurança exceções geradas pelo <xref:System.ServiceModel.ServiceHost>, consulte [uso Close e Abort para liberar os recursos de cliente do WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="a83d6-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a83d6-187">Quando você adiciona uma biblioteca de serviço do WCF, o Visual Studio o hospeda para você se depurá-lo, iniciando um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="a83d6-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="a83d6-188">Para evitar conflitos, você pode impedir que o Visual Studio hospeda o WCF service library.</span><span class="sxs-lookup"><span data-stu-id="a83d6-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
> 1. <span data-ttu-id="a83d6-189">Selecione o **GettingStartedLib** project no **Gerenciador de soluções** e escolha **propriedades** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="a83d6-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="a83d6-190">Selecione **opções do WCF** e desmarque **iniciar durante a depuração de outro projeto na mesma solução o Host de serviço de WCF**.</span><span class="sxs-lookup"><span data-stu-id="a83d6-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>


## <a name="next-steps"></a><span data-ttu-id="a83d6-191">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="a83d6-191">Next steps</span></span>

<span data-ttu-id="a83d6-192">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="a83d6-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="a83d6-193">Criar e configurar um projeto de aplicativo de console para hospedar um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a83d6-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="a83d6-194">Adicione código para hospedar o serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a83d6-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="a83d6-195">Atualize o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a83d6-195">Update the configuration file.</span></span>
> - <span data-ttu-id="a83d6-196">Inicie o serviço do WCF e verificar se ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="a83d6-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="a83d6-197">Avance para o próximo tutorial para aprender a criar um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="a83d6-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a83d6-198">Tutorial: Criar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="a83d6-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
