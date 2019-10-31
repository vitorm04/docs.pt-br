---
title: Adicionar WCF Web Service Reference
description: Uma visão geral da ferramenta Microsoft WCF Web Service Reference Provider que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta Adicionar Referência de Serviço para projetos do .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: feecf374e1af48f349495c13ea91b810c6b0a1c3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191902"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="f97e0-103">Usar a ferramenta WCF Web Service Reference Provider</span><span class="sxs-lookup"><span data-stu-id="f97e0-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="f97e0-104">Ao longo dos anos, muitos desenvolvedores do Visual Studio têm apreciado a produtividade que a ferramenta [**Adicionar Referência de Serviço**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) fornecida quando seus projetos do .NET Framework precisam acessar serviços Web.</span><span class="sxs-lookup"><span data-stu-id="f97e0-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="f97e0-105">A ferramenta **WCF Web Service Reference** é uma extensão de serviço conectado do Visual Studio que fornece uma experiência semelhante à funcionalidade Adicionar Referência de Serviço para projetos do .NET Core e ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f97e0-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="f97e0-106">Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL, e gera um arquivo de origem compatível com o .NET Core que contém o código de proxy de cliente do WCF (Windows Communication Foundation) que você pode usar para acessar esse serviço Web.</span><span class="sxs-lookup"><span data-stu-id="f97e0-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f97e0-107">Você só deve fazer referência a serviços de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="f97e0-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="f97e0-108">A adição de referências de uma fonte não confiável pode comprometer a segurança.</span><span class="sxs-lookup"><span data-stu-id="f97e0-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f97e0-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f97e0-109">Prerequisites</span></span>

- <span data-ttu-id="f97e0-110">[Visual Studio 2017 versão 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f97e0-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="f97e0-111">Como usar a extensão</span><span class="sxs-lookup"><span data-stu-id="f97e0-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="f97e0-112">A opção **WCF Web Service Reference** é aplicável a projetos criados com o uso dos seguintes modelos de projeto:</span><span class="sxs-lookup"><span data-stu-id="f97e0-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="f97e0-113">**Visual C#**  >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="f97e0-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="f97e0-114">**Visual C#**  >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="f97e0-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="f97e0-115">**Visual C#**  > **Web** > **Aplicativo Web ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="f97e0-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="f97e0-116">Ao usar o modelo de projeto **Aplicativo Web ASP.NET Core** como um exemplo, este artigo o orienta na adição de uma referência de serviço WCF ao projeto:</span><span class="sxs-lookup"><span data-stu-id="f97e0-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="f97e0-117">No Gerenciador de Soluções, clique duas vezes no nó **Serviços Conectados** do projeto (para um projeto do .NET Core ou .NET Standard, essa opção está disponível quando você clica com o botão direito do mouse no nó **Dependências** do projeto no Gerenciador de Soluções).</span><span class="sxs-lookup"><span data-stu-id="f97e0-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="f97e0-118">A página **Serviços Conectados** é exibida, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="f97e0-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Guia Serviços Conectados do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="f97e0-120">Na página **Serviços Conectados**, clique em **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="f97e0-121">Isso apresenta o assistente **Configurar a WCF Web Service Reference**:</span><span class="sxs-lookup"><span data-stu-id="f97e0-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Guia Ponto de Extremidade do Serviço do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="f97e0-123">Selecione um serviço.</span><span class="sxs-lookup"><span data-stu-id="f97e0-123">Select a service.</span></span>

    <span data-ttu-id="f97e0-124">3a.</span><span class="sxs-lookup"><span data-stu-id="f97e0-124">3a.</span></span> <span data-ttu-id="f97e0-125">Há várias opções de pesquisa de serviços disponíveis no assistente **Configurar a WCF Web Service Reference**:</span><span class="sxs-lookup"><span data-stu-id="f97e0-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="f97e0-126">Para pesquisar serviços definidos na solução atual, clique no botão **Descobrir**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="f97e0-127">Para pesquisar serviços hospedados em um endereço especificado, insira uma URL de serviço na caixa **Endereço** e clique no botão **Ir**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="f97e0-128">Para selecionar um arquivo WSDL que contenha as informações de metadados do serviço Web, clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="f97e0-129">3b.</span><span class="sxs-lookup"><span data-stu-id="f97e0-129">3b.</span></span> <span data-ttu-id="f97e0-130">Selecione o serviço na lista de resultados da pesquisa na caixa **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="f97e0-131">Se necessário, insira o namespace para o código gerado na caixa de texto **Namespace** correspondente.</span><span class="sxs-lookup"><span data-stu-id="f97e0-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="f97e0-132">3c.</span><span class="sxs-lookup"><span data-stu-id="f97e0-132">3c.</span></span> <span data-ttu-id="f97e0-133">Clique no botão **Avançar** para abrir as páginas **Opções de Tipo de Dados** e **Opções do Cliente**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="f97e0-134">Como alternativa, clique no botão **Concluir** para usar as opções padrão.</span><span class="sxs-lookup"><span data-stu-id="f97e0-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="f97e0-135">O formulário **Opções de Tipo de Dados** permite que você refine as definições de configuração de referência do serviço gerado:</span><span class="sxs-lookup"><span data-stu-id="f97e0-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Guia Opções de tipo de dados do Visual Studio para .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="f97e0-137">A opção da caixa de seleção **Usar novamente os tipos em assemblies consultados** é útil quando os tipos de dados necessários para a geração de código da referência de serviço são definidos em um dos assemblies referenciados do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f97e0-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="f97e0-138">É importante reutilizar esses tipos de dados existentes para evitar problemas de conflito de tipo de tempo de compilação ou problemas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f97e0-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="f97e0-139">Pode haver um atraso enquanto as informações de tipo são carregadas, dependendo do número de dependências do projeto e de outros fatores de desempenho do sistema.</span><span class="sxs-lookup"><span data-stu-id="f97e0-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="f97e0-140">O botão **Concluir** será desabilitado durante o carregamento, a menos que a caixa de seleção **Usar novamente os tipos em assemblies consultados** esteja desmarcada.</span><span class="sxs-lookup"><span data-stu-id="f97e0-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="f97e0-141">Clique em **Concluir** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="f97e0-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="f97e0-142">Enquanto exibe o andamento, a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="f97e0-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="f97e0-143">Baixa metadados do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="f97e0-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="f97e0-144">Gera o código de referência de serviço em um arquivo chamado *reference.cs* e o adiciona ao seu projeto no nó **Serviços Conectados**.</span><span class="sxs-lookup"><span data-stu-id="f97e0-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="f97e0-145">Atualiza o arquivo de projeto (.csproj) com as referências de pacote NuGet necessárias para compilar e executar na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="f97e0-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Janela Progresso do Studio Visual](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="f97e0-147">Quando esses processos forem concluídos, você poderá criar uma instância do tipo de cliente do WCF gerado e invocar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="f97e0-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="f97e0-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f97e0-148">See also</span></span>

- [<span data-ttu-id="f97e0-149">Introdução aos aplicativos Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f97e0-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="f97e0-150">Serviços de Windows Communication Foundation e WCF Data Services no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f97e0-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="f97e0-151">Recursos com suporte do WCF no .NET Core</span><span class="sxs-lookup"><span data-stu-id="f97e0-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="f97e0-152">Perguntas e comentários</span><span class="sxs-lookup"><span data-stu-id="f97e0-152">Feedback & questions</span></span>

<span data-ttu-id="f97e0-153">Se você tiver dúvidas ou comentários, denuncie-o na [comunidade de desenvolvedores](https://developercommunity.visualstudio.com/) usando o [relatório uma ferramenta problemática](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) .</span><span class="sxs-lookup"><span data-stu-id="f97e0-153">If you have any questions or feedback, report it at [Developer Community](https://developercommunity.visualstudio.com/) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="f97e0-154">Notas de Versão</span><span class="sxs-lookup"><span data-stu-id="f97e0-154">Release notes</span></span>

- <span data-ttu-id="f97e0-155">Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="f97e0-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
