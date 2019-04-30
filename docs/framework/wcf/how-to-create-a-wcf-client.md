---
title: 'Tutorial: Criar um cliente do Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: a16a0ccabfd0f9fbe69db1ea88d4613185f3c1da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002073"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="9a7e2-102">Tutorial: Criar um cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9a7e2-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="9a7e2-103">Este tutorial descreve o quarto de cinco tarefas necessárias para criar um aplicativo básico do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9a7e2-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="9a7e2-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="9a7e2-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="9a7e2-105">A próxima tarefa para a criação de um aplicativo WCF é criar um cliente recuperando metadados de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="9a7e2-106">Usar o Visual Studio para adicionar uma referência de serviço, que obtém os metadados do ponto de extremidade MEX do serviço.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="9a7e2-107">Em seguida, o Visual Studio gera um arquivo de código fonte gerenciado para um proxy de cliente na linguagem escolhida.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="9a7e2-108">Ele também cria um arquivo de configuração do cliente (*App. config*).</span><span class="sxs-lookup"><span data-stu-id="9a7e2-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="9a7e2-109">Esse arquivo permite que o aplicativo cliente conectar-se para o serviço em um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="9a7e2-110">Se você chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, use o **adicionar referência de serviço** recurso para gerar automaticamente um proxy e um arquivo de configuração associado.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="9a7e2-111">No entanto, como projetos de biblioteca de classe não usam esse arquivo de configuração, você precisará adicionar as configurações no arquivo de configuração gerado para o *App. config* arquivo para o executável que chama a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="9a7e2-112">Como alternativa, use o [ferramenta de utilitário de metadados ServiceModel](#servicemodel-metadata-utility-tool) em vez do Visual Studio para gerar o arquivo de classe e a configuração de proxy.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="9a7e2-113">O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="9a7e2-114">Esse procedimento é descrito na [Tutorial: Usar um cliente](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="9a7e2-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="9a7e2-115">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="9a7e2-116">Criar e configurar um projeto de aplicativo de console para o cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="9a7e2-117">Adicione uma referência de serviço para o serviço do WCF para gerar os arquivos de classe e a configuração de proxy.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="9a7e2-118">Criar um cliente do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9a7e2-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="9a7e2-119">Crie um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="9a7e2-120">Dos **arquivo** menu, selecione **abra** > **projeto/solução** e navegue até o **GettingStarted** solução você criado anteriormente (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="9a7e2-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="9a7e2-121">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-121">Select **Open**.</span></span>

    2. <span data-ttu-id="9a7e2-122">Dos **modo de exibição** menu, selecione **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="9a7e2-123">No **Gerenciador de soluções** janela, selecione a **GettingStarted** solução (nó superior) e, em seguida, selecione **Add** > **denovoprojeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="9a7e2-124">No **adicionar novo projeto** janela, no lado esquerdo, selecione o **área de trabalho do Windows** categoria sob **Visual C#**  ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="9a7e2-125">Selecione o **aplicativo de Console (.NET Framework)** modelo e insira *GettingStartedClient* para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="9a7e2-126">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-126">Select **OK**.</span></span>

2. <span data-ttu-id="9a7e2-127">Adicionar uma referência na **GettingStartedClient** do projeto para o <xref:System.ServiceModel> assembly:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="9a7e2-128">No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedClient** do projeto e, em seguida, selecione **Add Reference** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="9a7e2-129">No **adicionar referência** janela, em **Assemblies** no lado esquerdo da janela, selecione **Framework**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="9a7e2-130">Localize e selecione **System. ServiceModel**e, em seguida, escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="9a7e2-131">Salve a solução selecionando **arquivo** > **Salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="9a7e2-132">Adicione uma referência de serviço para o serviço da Calculadora:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="9a7e2-133">No **Gerenciador de soluções** janela, selecione a **referências** pasta sob o **GettingStartedClient** do projeto e, em seguida, selecione **adicionar referência de serviço**  no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="9a7e2-134">No **adicionar referência de serviço** janela, selecione **Discover**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="9a7e2-135">O CalculatorService serviço é iniciado e o Visual Studio exibe-o na **Services** caixa.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="9a7e2-136">Selecione **CalculatorService** para expandi-lo e exibir os contratos de serviço implementados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="9a7e2-137">Deixe o padrão **Namespace** e escolha **Okey**.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="9a7e2-138">O Visual Studio adiciona um novo item sob o **serviços conectados** pasta o **GettingStartedClient** projeto.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="9a7e2-139">Ferramenta Utilitário de metadados de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a7e2-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="9a7e2-140">Os exemplos a seguir mostram como usar opcionalmente a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o arquivo de classe de proxy.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="9a7e2-141">Essa ferramenta gera o arquivo de classe de proxy e o *App. config* arquivo.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="9a7e2-142">Os exemplos a seguir mostram como gerar o proxy no C# e Visual Basic, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="9a7e2-143">Arquivo de configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="9a7e2-143">Client configuration file</span></span>

<span data-ttu-id="9a7e2-144">Depois de criar o cliente, o Visual Studio cria o **App. config** arquivo de configuração do **GettingStartedClient** projeto, que deve ser semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="9a7e2-145">Sob o [ \<System. ServiceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) seção, observe o [ \<ponto de extremidade >](../configure-apps/file-schema/wcf/endpoint-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="9a7e2-146">O **&lt;ponto de extremidade&gt;** elemento define o ponto de extremidade que o cliente usa para acessar o serviço da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>
- <span data-ttu-id="9a7e2-147">Endereço: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="9a7e2-148">O endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-148">The address of the endpoint.</span></span>
- <span data-ttu-id="9a7e2-149">Contrato de serviço: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="9a7e2-150">O contrato de serviço gerencia a comunicação entre o cliente do WCF e o serviço.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="9a7e2-151">Visual Studio gerado esse contrato quando você usou seu **adicionar referência de serviço** função.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="9a7e2-152">Ele é essencialmente uma cópia do contrato que você definiu no projeto GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="9a7e2-153">Associação: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="9a7e2-154">A associação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9a7e2-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9a7e2-155">Next steps</span></span>

<span data-ttu-id="9a7e2-156">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="9a7e2-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="9a7e2-157">Criar e configurar um projeto de aplicativo de console para o cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="9a7e2-158">Adicione uma referência de serviço para o serviço do WCF para gerar os arquivos de classe e a configuração de proxy para o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="9a7e2-159">Avance para o próximo tutorial para aprender a usar o cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="9a7e2-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a7e2-160">Tutorial: Usar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="9a7e2-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
