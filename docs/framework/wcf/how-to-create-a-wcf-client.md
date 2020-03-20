---
title: 'Tutorial: Crie um cliente da Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184108"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="6c467-102">Tutorial: Crie um cliente da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6c467-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="6c467-103">Este tutorial descreve a quarta das cinco tarefas necessárias para criar um aplicativo básico da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6c467-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="6c467-104">Para obter uma visão geral dos tutoriais, consulte [Tutorial: Comece com os aplicativos da Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="6c467-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="6c467-105">A próxima tarefa para criar um aplicativo WCF é criar um cliente recuperando metadados de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="6c467-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="6c467-106">Você usa o Visual Studio para adicionar uma referência de serviço, que obtém os metadados do ponto final mex do serviço.</span><span class="sxs-lookup"><span data-stu-id="6c467-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="6c467-107">O Visual Studio então gera um arquivo de código-fonte gerenciado para um proxy cliente no idioma que você escolheu.</span><span class="sxs-lookup"><span data-stu-id="6c467-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="6c467-108">Ele também cria um arquivo de configuração do cliente *(App.config*).</span><span class="sxs-lookup"><span data-stu-id="6c467-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="6c467-109">Este arquivo permite que o aplicativo cliente se conecte ao serviço em um ponto final.</span><span class="sxs-lookup"><span data-stu-id="6c467-109">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="6c467-110">Se você chamar um serviço WCF de um projeto de biblioteca de classes no Visual Studio, use o recurso **Adicionar referência de serviço** para gerar automaticamente um proxy e um arquivo de configuração associado.</span><span class="sxs-lookup"><span data-stu-id="6c467-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="6c467-111">No entanto, como os projetos de biblioteca de classe não usam esse arquivo de configuração, você precisa adicionar as configurações no arquivo de configuração gerada ao arquivo *App.config* para o executável que chama a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="6c467-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="6c467-112">Como alternativa, use a [ferramenta ServiceModel Metadata Utility](#servicemodel-metadata-utility-tool) em vez do Visual Studio para gerar a classe proxy e o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6c467-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="6c467-113">O aplicativo cliente usa a classe proxy gerada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="6c467-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="6c467-114">Este procedimento é descrito no [Tutorial: Use um cliente](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="6c467-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="6c467-115">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="6c467-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6c467-116">Crie e configure um projeto de aplicativo de console para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="6c467-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="6c467-117">Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="6c467-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="6c467-118">Crie um cliente da Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6c467-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="6c467-119">Crie um projeto de aplicativo de console no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="6c467-119">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="6c467-120">No menu **Arquivo,** selecione **Abrir** > **projeto/solução** e navegue até a solução **GettingStarted** criada anteriormente *(GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="6c467-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="6c467-121">Selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="6c467-121">Select **Open**.</span></span>

    2. <span data-ttu-id="6c467-122">No menu **Exibir,** selecione **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="6c467-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="6c467-123">Na janela **Solution Explorer,** selecione a solução **GettingStarted** (nó superior e selecione **Adicionar** > **novo projeto** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="6c467-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="6c467-124">Na janela **Adicionar novo projeto,** no lado esquerdo, selecione a categoria **Windows Desktop** em **Visual C#** ou **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="6c467-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="6c467-125">Selecione o modelo **Console App (.NET Framework)** e *digite GettingStartedClient* for the **Name**.</span><span class="sxs-lookup"><span data-stu-id="6c467-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="6c467-126">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c467-126">Select **OK**.</span></span>

2. <span data-ttu-id="6c467-127">Adicione uma referência no projeto **GettingStartedClient** à <xref:System.ServiceModel> montagem:</span><span class="sxs-lookup"><span data-stu-id="6c467-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="6c467-128">Na janela **Solution Explorer,** selecione a pasta **Referências** no projeto **GettingStartedClient** e selecione **Adicionar referência** no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="6c467-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="6c467-129">Na janela **Adicionar referência,** em **Montagens** no lado esquerdo da janela, **selecione Quadro**.</span><span class="sxs-lookup"><span data-stu-id="6c467-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="6c467-130">Encontre e selecione **System.ServiceModel**e escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c467-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="6c467-131">Salve a solução selecionando **'Salvar todos'** **do arquivo** > .</span><span class="sxs-lookup"><span data-stu-id="6c467-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="6c467-132">Adicionar uma referência de serviço ao serviço de calculadora:</span><span class="sxs-lookup"><span data-stu-id="6c467-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="6c467-133">Na janela **'Explorador de soluções',** selecione a pasta **Referências** no projeto **GettingStartedClient** e selecione **Adicionar referência** de serviço no menu de atalho.</span><span class="sxs-lookup"><span data-stu-id="6c467-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="6c467-134">Na **janela Adicionar referência de serviço,** selecione **Descobrir**.</span><span class="sxs-lookup"><span data-stu-id="6c467-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="6c467-135">O serviço CalculatorService é iniciado e o Visual Studio exibe-o na caixa **Serviços.**</span><span class="sxs-lookup"><span data-stu-id="6c467-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="6c467-136">Selecione **CalculadoraService** para expandi-lo e exibir os contratos de serviço implementados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="6c467-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="6c467-137">Deixe o **namespace** padrão e escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c467-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="6c467-138">O Visual Studio adiciona um novo item na pasta **Serviços Conectados** no projeto **GettingStartedClient.**</span><span class="sxs-lookup"><span data-stu-id="6c467-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="6c467-139">Ferramenta serviceModel Metadata Utility</span><span class="sxs-lookup"><span data-stu-id="6c467-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="6c467-140">Os exemplos a seguir mostram como usar opcionalmente a [ferramenta ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o arquivo de classe proxy.</span><span class="sxs-lookup"><span data-stu-id="6c467-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="6c467-141">Esta ferramenta gera o arquivo de classe proxy e o arquivo *App.config.*</span><span class="sxs-lookup"><span data-stu-id="6c467-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="6c467-142">Os exemplos a seguir mostram como gerar o proxy em C# e Visual Basic, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="6c467-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="6c467-143">Arquivo de configuração de cliente</span><span class="sxs-lookup"><span data-stu-id="6c467-143">Client configuration file</span></span>

<span data-ttu-id="6c467-144">Depois de criar o cliente, o Visual Studio cria o arquivo de configuração **App.config** no projeto **GettingStartedClient,** que deve ser semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c467-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="6c467-145">Na seção [ \<system.serviceModel>,](../configure-apps/file-schema/wcf/system-servicemodel.md) observe o [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) elemento>ponto final.</span><span class="sxs-lookup"><span data-stu-id="6c467-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="6c467-146">O elemento \*\* &lt;ponto final&gt; \*\* define o ponto final que o cliente usa para acessar o serviço da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="6c467-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="6c467-147">Endereço: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="6c467-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="6c467-148">O endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6c467-148">The address of the endpoint.</span></span>
- <span data-ttu-id="6c467-149">Contrato de `ServiceReference1.ICalculator`serviço: .</span><span class="sxs-lookup"><span data-stu-id="6c467-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="6c467-150">O contrato de prestação de serviços trata da comunicação entre o cliente WCF e o serviço.</span><span class="sxs-lookup"><span data-stu-id="6c467-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="6c467-151">O Visual Studio gerou este contrato quando você usou sua função **Add Service Reference.**</span><span class="sxs-lookup"><span data-stu-id="6c467-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="6c467-152">É essencialmente uma cópia do contrato que você definiu no projeto GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="6c467-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="6c467-153">Vinculação: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="6c467-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="6c467-154">A vinculação especifica HTTP como o transporte, segurança interoperável e outros detalhes de configuração.</span><span class="sxs-lookup"><span data-stu-id="6c467-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6c467-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6c467-155">Next steps</span></span>

<span data-ttu-id="6c467-156">Neste tutorial, você aprendeu a:</span><span class="sxs-lookup"><span data-stu-id="6c467-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6c467-157">Crie e configure um projeto de aplicativo de console para o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="6c467-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="6c467-158">Adicione uma referência de serviço ao serviço WCF para gerar a classe proxy e os arquivos de configuração para o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="6c467-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="6c467-159">Avance para o próximo tutorial para saber como usar o cliente gerado.</span><span class="sxs-lookup"><span data-stu-id="6c467-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6c467-160">Tutorial: Use um cliente WCF</span><span class="sxs-lookup"><span data-stu-id="6c467-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
