---
title: Adicionar WCF Web Service Reference
description: Uma visão geral da ferramenta Microsoft WCF Web Service Reference Provider que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta Adicionar Referência de Serviço para projetos do .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 28eaae4a83d918f8a9e5376eb3c8d42843ffa027
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773953"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="4a665-103">Usar a ferramenta WCF Web Service Reference Provider</span><span class="sxs-lookup"><span data-stu-id="4a665-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="4a665-104">Ao longo dos anos, muitos desenvolvedores do Visual Studio têm apreciado a produtividade que a ferramenta [**Adicionar Referência de Serviço**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) fornecida quando seus projetos do .NET Framework precisam acessar serviços Web.</span><span class="sxs-lookup"><span data-stu-id="4a665-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="4a665-105">A ferramenta **WCF Web Service Reference** é uma extensão de serviço conectado do Visual Studio que fornece uma experiência semelhante à funcionalidade Adicionar Referência de Serviço para projetos do .NET Core e ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4a665-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="4a665-106">Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL, e gera um arquivo de origem compatível com o .NET Core que contém o código de proxy de cliente do WCF (Windows Communication Foundation) que você pode usar para acessar esse serviço Web.</span><span class="sxs-lookup"><span data-stu-id="4a665-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a665-107">Você só deve fazer referência a serviços de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="4a665-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="4a665-108">A adição de referências de uma fonte não confiável pode comprometer a segurança.</span><span class="sxs-lookup"><span data-stu-id="4a665-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a665-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4a665-109">Prerequisites</span></span>

- <span data-ttu-id="4a665-110">[Visual Studio 2017 versão 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="4a665-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="4a665-111">Como usar a extensão</span><span class="sxs-lookup"><span data-stu-id="4a665-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="4a665-112">A opção **WCF Web Service Reference** é aplicável a projetos criados com o uso dos seguintes modelos de projeto:</span><span class="sxs-lookup"><span data-stu-id="4a665-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="4a665-113">**Visual C#**  >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="4a665-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="4a665-114">**Visual C#**  >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="4a665-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="4a665-115">**Visual C#**  > **Web** > **Aplicativo Web ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="4a665-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="4a665-116">Ao usar o modelo de projeto **Aplicativo Web ASP.NET Core** como um exemplo, este artigo o orienta na adição de uma referência de serviço WCF ao projeto:</span><span class="sxs-lookup"><span data-stu-id="4a665-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="4a665-117">No Gerenciador de Soluções, clique duas vezes no nó **Serviços Conectados** do projeto (para um projeto do .NET Core ou .NET Standard, essa opção está disponível quando você clica com o botão direito do mouse no nó **Dependências** do projeto no Gerenciador de Soluções).</span><span class="sxs-lookup"><span data-stu-id="4a665-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="4a665-118">A página **Serviços Conectados** é exibida, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="4a665-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Guia Serviços Conectados do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="4a665-120">Na página **Serviços Conectados**, clique em **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="4a665-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="4a665-121">Isso apresenta o assistente **Configurar a WCF Web Service Reference**:</span><span class="sxs-lookup"><span data-stu-id="4a665-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Guia Ponto de Extremidade do Serviço do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="4a665-123">Selecione um serviço.</span><span class="sxs-lookup"><span data-stu-id="4a665-123">Select a service.</span></span>

    <span data-ttu-id="4a665-124">3a.</span><span class="sxs-lookup"><span data-stu-id="4a665-124">3a.</span></span> <span data-ttu-id="4a665-125">Há várias opções de pesquisa de serviços disponíveis no assistente **Configurar a WCF Web Service Reference**:</span><span class="sxs-lookup"><span data-stu-id="4a665-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="4a665-126">Para pesquisar serviços definidos na solução atual, clique no botão **Descobrir**.</span><span class="sxs-lookup"><span data-stu-id="4a665-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="4a665-127">Para pesquisar serviços hospedados em um endereço especificado, insira uma URL de serviço na caixa **Endereço** e clique no botão **Ir**.</span><span class="sxs-lookup"><span data-stu-id="4a665-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="4a665-128">Para selecionar um arquivo WSDL que contenha as informações de metadados do serviço Web, clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="4a665-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="4a665-129">3b.</span><span class="sxs-lookup"><span data-stu-id="4a665-129">3b.</span></span> <span data-ttu-id="4a665-130">Selecione o serviço na lista de resultados da pesquisa na caixa **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="4a665-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="4a665-131">Se necessário, insira o namespace para o código gerado na caixa de texto **Namespace** correspondente.</span><span class="sxs-lookup"><span data-stu-id="4a665-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="4a665-132">3c.</span><span class="sxs-lookup"><span data-stu-id="4a665-132">3c.</span></span> <span data-ttu-id="4a665-133">Clique no botão **Avançar** para abrir as páginas **Opções de Tipo de Dados** e **Opções do Cliente**.</span><span class="sxs-lookup"><span data-stu-id="4a665-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="4a665-134">Como alternativa, clique no botão **Concluir** para usar as opções padrão.</span><span class="sxs-lookup"><span data-stu-id="4a665-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="4a665-135">O formulário **Opções de Tipo de Dados** permite que você refine as definições de configuração de referência do serviço gerado:</span><span class="sxs-lookup"><span data-stu-id="4a665-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Guia Opções de tipo de dados do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="4a665-137">A opção da caixa de seleção **Usar novamente os tipos em assemblies consultados** é útil quando os tipos de dados necessários para a geração de código da referência de serviço são definidos em um dos assemblies referenciados do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4a665-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="4a665-138">É importante reutilizar esses tipos de dados existentes para evitar problemas de conflito de tipo de tempo de compilação ou problemas de runtime.</span><span class="sxs-lookup"><span data-stu-id="4a665-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="4a665-139">Pode haver um atraso enquanto as informações de tipo são carregadas, dependendo do número de dependências do projeto e de outros fatores de desempenho do sistema.</span><span class="sxs-lookup"><span data-stu-id="4a665-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="4a665-140">O botão **Concluir** será desabilitado durante o carregamento, a menos que a caixa de seleção **Usar novamente os tipos em assemblies consultados** esteja desmarcada.</span><span class="sxs-lookup"><span data-stu-id="4a665-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="4a665-141">Clique em **Concluir** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="4a665-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="4a665-142">Enquanto exibe o andamento, a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="4a665-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="4a665-143">Baixa metadados do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="4a665-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="4a665-144">Gera o código de referência de serviço em um arquivo chamado *reference.cs* e o adiciona ao seu projeto no nó **Serviços Conectados**.</span><span class="sxs-lookup"><span data-stu-id="4a665-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="4a665-145">Atualiza o arquivo de projeto (.csproj) com as referências de pacote NuGet necessárias para compilar e executar na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="4a665-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Janela Progresso do Studio Visual](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="4a665-147">Quando esses processos forem concluídos, você poderá criar uma instância do tipo de cliente do WCF gerado e invocar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="4a665-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a665-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4a665-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="4a665-149">Perguntas e comentários</span><span class="sxs-lookup"><span data-stu-id="4a665-149">Feedback & questions</span></span>

<span data-ttu-id="4a665-150">Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="4a665-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="4a665-151">Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="4a665-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="4a665-152">Notas de Versão</span><span class="sxs-lookup"><span data-stu-id="4a665-152">Release notes</span></span>

- <span data-ttu-id="4a665-153">Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="4a665-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
