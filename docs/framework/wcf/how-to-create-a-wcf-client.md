---
title: 'Tutorial: Criar um cliente Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928899"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="33eaf-102">Tutorial: Criar um cliente Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="33eaf-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="33eaf-103">Este tutorial descreve a quarta de cinco tarefas necessárias para criar um aplicativo de Windows Communication Foundation básico (WCF).</span><span class="sxs-lookup"><span data-stu-id="33eaf-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="33eaf-104">Para obter uma visão geral dos tutoriais, [consulte o tutorial: Introdução aos aplicativos](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="33eaf-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="33eaf-105">A próxima tarefa para criar um aplicativo WCF é criar um cliente Recuperando metadados de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="33eaf-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="33eaf-106">Você usa o Visual Studio para adicionar uma referência de serviço, que obtém os metadados do ponto de extremidade MEX do serviço.</span><span class="sxs-lookup"><span data-stu-id="33eaf-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="33eaf-107">Em seguida, o Visual Studio gera um arquivo de código-fonte gerenciado para um proxy de cliente no idioma escolhido.</span><span class="sxs-lookup"><span data-stu-id="33eaf-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="33eaf-108">Ele também cria um arquivo de configuração de cliente (*app. config*).</span><span class="sxs-lookup"><span data-stu-id="33eaf-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="33eaf-109">Esse arquivo permite que o aplicativo cliente se conecte ao serviço em um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="33eaf-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="33eaf-110">Se você chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, use o recurso **Adicionar referência de serviço** para gerar automaticamente um proxy e um arquivo de configuração associado.</span><span class="sxs-lookup"><span data-stu-id="33eaf-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="33eaf-111">No entanto, como os projetos de biblioteca de classes não usam esse arquivo de configuração, você precisa adicionar as configurações no arquivo de configuração gerado ao arquivo *app. config* para o executável que chama a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="33eaf-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="33eaf-112">Como alternativa, use a [ferramenta de utilitário de metadados ServiceModel](#servicemodel-metadata-utility-tool) em vez do Visual Studio para gerar a classe proxy e o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="33eaf-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="33eaf-113">O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="33eaf-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="33eaf-114">Este procedimento é descrito em [tutorial: Usar um cliente](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="33eaf-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="33eaf-115">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="33eaf-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="33eaf-116">Criar e configurar um projeto de aplicativo de console para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="33eaf-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="33eaf-117">Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="33eaf-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="33eaf-118">Criar um cliente Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="33eaf-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="33eaf-119">Criar um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="33eaf-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="33eaf-120">No menu **arquivo** , selecione **abrir** > **projeto/solução** e navegue até a solução **gettingstarted** que você criou anteriormente (*gettingstarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="33eaf-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="33eaf-121">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-121">Select **Open**.</span></span>

    2. <span data-ttu-id="33eaf-122">No menu **Exibir** , selecione **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="33eaf-123">Na janela **Gerenciador de soluções** , selecione a solução **gettingstarted** (nó superior) e, em seguida, selecione **Adicionar** > **novo projeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="33eaf-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="33eaf-124">Na janela **Adicionar novo projeto** , no lado esquerdo, selecione a categoria **área de trabalho do Windows** em  **C# Visual** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="33eaf-125">Selecione o modelo **aplicativo de console (.NET Framework)** e digite *GettingStartedClient* para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="33eaf-126">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-126">Select **OK**.</span></span>

2. <span data-ttu-id="33eaf-127">Adicione uma referência no projeto **GettingStartedClient** ao <xref:System.ServiceModel> assembly:</span><span class="sxs-lookup"><span data-stu-id="33eaf-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="33eaf-128">Na janela **Gerenciador de soluções** , selecione a pasta **referências** no projeto **GettingStartedClient** e, em seguida, selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="33eaf-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="33eaf-129">Na janela **Adicionar referência** , em **assemblies** no lado esquerdo da janela, selecione **estrutura**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="33eaf-130">Localize e selecione **System. ServiceModel**e, em seguida, escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="33eaf-131">Salve a solução selecionando **arquivo** > **salvar tudo**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="33eaf-132">Adicione uma referência de serviço ao serviço de calculadora:</span><span class="sxs-lookup"><span data-stu-id="33eaf-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="33eaf-133">Na janela **Gerenciador de soluções** , selecione a pasta **referências** no projeto **GettingStartedClient** e, em seguida, selecione **Adicionar referência de serviço** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="33eaf-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="33eaf-134">Na janela **Adicionar referência de serviço** , selecione **descobrir**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="33eaf-135">O serviço CalculatorService é iniciado e o Visual Studio o exibe na caixa **Serviços** .</span><span class="sxs-lookup"><span data-stu-id="33eaf-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="33eaf-136">Selecione **CalculatorService** para expandi-lo e exibir os contratos de serviço implementados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="33eaf-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="33eaf-137">Deixe o **namespace** padrão e escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="33eaf-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="33eaf-138">O Visual Studio adiciona um novo item na pasta **Serviços conectados** no projeto **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="33eaf-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="33eaf-139">Ferramenta de utilitário de metadados ServiceModel</span><span class="sxs-lookup"><span data-stu-id="33eaf-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="33eaf-140">Os exemplos a seguir mostram como opcionalmente usar a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o arquivo de classe de proxy.</span><span class="sxs-lookup"><span data-stu-id="33eaf-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="33eaf-141">Essa ferramenta gera o arquivo de classe de proxy e o arquivo *app. config* .</span><span class="sxs-lookup"><span data-stu-id="33eaf-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="33eaf-142">Os exemplos a seguir mostram como gerar o proxy no C# e Visual Basic, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="33eaf-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="33eaf-143">Arquivo de configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="33eaf-143">Client configuration file</span></span>

<span data-ttu-id="33eaf-144">Depois de criar o cliente, o Visual Studio cria o arquivo de configuração **app. config** no projeto **GettingStartedClient** , que deve ser semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="33eaf-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="33eaf-145">Na seção [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) System. [ServiceModel >, observe o elemento Endpoint >. \<](../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="33eaf-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="33eaf-146">O elemento de **&lt;ponto de extremidade&gt;** define o ponto de extremidade que o cliente usa para acessar o serviço da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="33eaf-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="33eaf-147">Endereço: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="33eaf-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="33eaf-148">O endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="33eaf-148">The address of the endpoint.</span></span>
- <span data-ttu-id="33eaf-149">Contrato de serviço `ServiceReference1.ICalculator`:.</span><span class="sxs-lookup"><span data-stu-id="33eaf-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="33eaf-150">O contrato de serviço lida com a comunicação entre o cliente WCF e o serviço.</span><span class="sxs-lookup"><span data-stu-id="33eaf-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="33eaf-151">O Visual Studio gerou esse contrato quando você usou sua função **Adicionar referência de serviço** .</span><span class="sxs-lookup"><span data-stu-id="33eaf-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="33eaf-152">Basicamente, é uma cópia do contrato que você definiu no projeto GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="33eaf-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="33eaf-153">Associação: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="33eaf-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="33eaf-154">A associação especifica HTTP como transporte, segurança interoperável e outros detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="33eaf-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="33eaf-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="33eaf-155">Next steps</span></span>

<span data-ttu-id="33eaf-156">Neste tutorial, você aprendeu como:</span><span class="sxs-lookup"><span data-stu-id="33eaf-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="33eaf-157">Criar e configurar um projeto de aplicativo de console para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="33eaf-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="33eaf-158">Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração para o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="33eaf-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="33eaf-159">Avance para o próximo tutorial para aprender a usar o cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="33eaf-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="33eaf-160">Tutorial: Usar um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="33eaf-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
