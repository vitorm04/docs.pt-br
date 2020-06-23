---
title: 'Tutorial: criar um cliente Windows Communication Foundation'
description: Saiba como criar um cliente Recuperando metadados de um serviço WCF como parte de uma série de artigos que ajudam você a começar a criar um aplicativo WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246318"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="d56e3-103">Tutorial: criar um cliente Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d56e3-103">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="d56e3-104">Este tutorial descreve a quarta de cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF).</span><span class="sxs-lookup"><span data-stu-id="d56e3-104">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="d56e3-105">Para obter uma visão geral dos tutoriais, consulte [tutorial: introdução aos aplicativos Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d56e3-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="d56e3-106">A próxima tarefa para criar um aplicativo WCF é criar um cliente Recuperando metadados de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="d56e3-106">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="d56e3-107">Você usa o Visual Studio para adicionar uma referência de serviço, que obtém os metadados do ponto de extremidade MEX do serviço.</span><span class="sxs-lookup"><span data-stu-id="d56e3-107">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="d56e3-108">Em seguida, o Visual Studio gera um arquivo de código-fonte gerenciado para um proxy de cliente no idioma escolhido.</span><span class="sxs-lookup"><span data-stu-id="d56e3-108">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="d56e3-109">Ele também cria um arquivo de configuração de cliente (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="d56e3-109">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="d56e3-110">Esse arquivo permite que o aplicativo cliente se conecte ao serviço em um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d56e3-110">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="d56e3-111">Se você chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, use o recurso **Adicionar referência de serviço** para gerar automaticamente um proxy e um arquivo de configuração associado.</span><span class="sxs-lookup"><span data-stu-id="d56e3-111">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="d56e3-112">No entanto, como os projetos de biblioteca de classes não usam esse arquivo de configuração, você precisa adicionar as configurações no arquivo de configuração gerado ao arquivo de *App.config* para o executável que chama a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="d56e3-112">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="d56e3-113">Como alternativa, use a [ferramenta de utilitário de metadados ServiceModel](#servicemodel-metadata-utility-tool) em vez do Visual Studio para gerar a classe proxy e o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d56e3-113">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="d56e3-114">O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="d56e3-114">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="d56e3-115">Este procedimento é descrito em [tutorial: usar um cliente](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d56e3-115">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="d56e3-116">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="d56e3-116">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d56e3-117">Criar e configurar um projeto de aplicativo de console para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="d56e3-117">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="d56e3-118">Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="d56e3-118">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="d56e3-119">Criar um cliente Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d56e3-119">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="d56e3-120">Criar um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d56e3-120">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="d56e3-121">No menu **arquivo** , selecione **abrir**  >  **projeto/solução** e navegue até a solução **gettingstarted** que você criou anteriormente (*gettingstarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="d56e3-121">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="d56e3-122">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-122">Select **Open**.</span></span>

    2. <span data-ttu-id="d56e3-123">No menu **Exibir** , selecione **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-123">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="d56e3-124">Na janela **Gerenciador de soluções** , selecione a solução **gettingstarted** (nó superior) e, em seguida, selecione **Adicionar**  >  **novo projeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="d56e3-124">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="d56e3-125">Na janela **Adicionar novo projeto** , no lado esquerdo, selecione a categoria **área de trabalho do Windows** em **Visual C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-125">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="d56e3-126">Selecione o modelo **aplicativo de console (.NET Framework)** e digite *GettingStartedClient* para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-126">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="d56e3-127">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-127">Select **OK**.</span></span>

2. <span data-ttu-id="d56e3-128">Adicione uma referência no projeto **GettingStartedClient** ao <xref:System.ServiceModel> assembly:</span><span class="sxs-lookup"><span data-stu-id="d56e3-128">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="d56e3-129">Na janela **Gerenciador de soluções** , selecione a pasta **referências** no projeto **GettingStartedClient** e, em seguida, selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="d56e3-129">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="d56e3-130">Na janela **Adicionar referência** , em **assemblies** no lado esquerdo da janela, selecione **estrutura**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-130">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="d56e3-131">Localize e selecione **System. ServiceModel**e, em seguida, escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-131">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="d56e3-132">Salve a solução selecionando **arquivo**  >  **salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-132">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="d56e3-133">Adicione uma referência de serviço ao serviço de calculadora:</span><span class="sxs-lookup"><span data-stu-id="d56e3-133">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="d56e3-134">Na janela **Gerenciador de soluções** , selecione a pasta **referências** no projeto **GettingStartedClient** e, em seguida, selecione **Adicionar referência de serviço** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="d56e3-134">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="d56e3-135">Na janela **Adicionar referência de serviço** , selecione **descobrir**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-135">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="d56e3-136">O serviço CalculatorService é iniciado e o Visual Studio o exibe na caixa **Serviços** .</span><span class="sxs-lookup"><span data-stu-id="d56e3-136">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="d56e3-137">Selecione **CalculatorService** para expandi-lo e exibir os contratos de serviço implementados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d56e3-137">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="d56e3-138">Deixe o **namespace** padrão e escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="d56e3-138">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="d56e3-139">O Visual Studio adiciona um novo item na pasta **Serviços conectados** no projeto **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="d56e3-139">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="d56e3-140">Ferramenta de utilitário de metadados ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d56e3-140">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="d56e3-141">Os exemplos a seguir mostram como opcionalmente usar a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o arquivo de classe de proxy.</span><span class="sxs-lookup"><span data-stu-id="d56e3-141">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="d56e3-142">Essa ferramenta gera o arquivo de classe de proxy e o arquivo de *App.config* .</span><span class="sxs-lookup"><span data-stu-id="d56e3-142">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="d56e3-143">Os exemplos a seguir mostram como gerar o proxy em C# e Visual Basic, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="d56e3-143">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="d56e3-144">Arquivo de configuração de cliente</span><span class="sxs-lookup"><span data-stu-id="d56e3-144">Client configuration file</span></span>

<span data-ttu-id="d56e3-145">Depois de criar o cliente, o Visual Studio cria o arquivo de configuração **App.config** no projeto **GettingStartedClient** , que deve ser semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d56e3-145">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="d56e3-146">Na [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) seção, observe o [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d56e3-146">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="d56e3-147">O elemento de \*\* &lt; ponto de extremidade &gt; \*\* define o ponto de extremidade que o cliente usa para acessar o serviço da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d56e3-147">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="d56e3-148">Endereço: `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="d56e3-148">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="d56e3-149">O endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d56e3-149">The address of the endpoint.</span></span>
- <span data-ttu-id="d56e3-150">Contrato de serviço: `ServiceReference1.ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="d56e3-150">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="d56e3-151">O contrato de serviço lida com a comunicação entre o cliente WCF e o serviço.</span><span class="sxs-lookup"><span data-stu-id="d56e3-151">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="d56e3-152">O Visual Studio gerou esse contrato quando você usou sua função **Adicionar referência de serviço** .</span><span class="sxs-lookup"><span data-stu-id="d56e3-152">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="d56e3-153">Basicamente, é uma cópia do contrato que você definiu no projeto GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="d56e3-153">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="d56e3-154">Associação: <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d56e3-154">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="d56e3-155">A associação especifica HTTP como transporte, segurança interoperável e outros detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="d56e3-155">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d56e3-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d56e3-156">Next steps</span></span>

<span data-ttu-id="d56e3-157">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="d56e3-157">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d56e3-158">Criar e configurar um projeto de aplicativo de console para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="d56e3-158">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="d56e3-159">Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração para o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="d56e3-159">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="d56e3-160">Avance para o próximo tutorial para aprender a usar o cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="d56e3-160">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d56e3-161">Tutorial: usar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="d56e3-161">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
