---
title: Ferramenta Microsoft WCF Web Service Reference Provider
description: "Uma visão geral da ferramenta Microsoft WCF Web Service Reference Provider que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta Adicionar Referência de Serviço para projetos do .NET Framework."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 210f0a9bbf393055ebcd582d3accb3d77b1c9539
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2018
---
# <a name="microsoft-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="96acd-103">Ferramenta Microsoft WCF Web Service Reference Provider</span><span class="sxs-lookup"><span data-stu-id="96acd-103">Microsoft WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="96acd-104">Ao longo dos anos, muitos desenvolvedores do Visual Studio têm apreciado a produtividade que a ferramenta [**Adicionar Referência de Serviço**](../../visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) fornecida quando seus projetos do .NET Framework precisam acessar serviços Web.</span><span class="sxs-lookup"><span data-stu-id="96acd-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](../../visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="96acd-105">A ferramenta **WCF Web Service Reference** é uma extensão de serviço conectado do Visual Studio que fornece uma experiência semelhante à funcionalidade Adicionar Referência de Serviço para projetos do .NET Core e ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="96acd-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="96acd-106">Essa ferramenta recupera metadados de um serviço Web na solução atual, em um local de rede ou de um arquivo WSDL, e gera um arquivo de origem compatível com o .NET Core que contém o código de proxy de cliente do WCF (Windows Communication Foundation) que você pode usar para acessar esse serviço Web.</span><span class="sxs-lookup"><span data-stu-id="96acd-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96acd-107">Você só deve fazer referência a serviços de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="96acd-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="96acd-108">A adição de referências de uma fonte não confiável pode comprometer a segurança.</span><span class="sxs-lookup"><span data-stu-id="96acd-108">Adding references from an untrusted source may compromise security.</span></span> 

## <a name="how-to-use-the-extension"></a><span data-ttu-id="96acd-109">Como usar a extensão</span><span class="sxs-lookup"><span data-stu-id="96acd-109">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="96acd-110">A opção **WCF Web Service Reference** é aplicável a projetos criados com o uso dos seguintes modelos de projeto:</span><span class="sxs-lookup"><span data-stu-id="96acd-110">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
> * <span data-ttu-id="96acd-111">**Visual C#** > **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="96acd-111">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="96acd-112">**Visual C#** > **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="96acd-112">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="96acd-113">**Visual C#** > **Web** > **Aplicativo Web ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="96acd-113">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="96acd-114">Ao usar o modelo de projeto **Aplicativo Web ASP.NET Core** como um exemplo, este artigo o orienta na adição de uma referência de serviço WCF ao projeto:</span><span class="sxs-lookup"><span data-stu-id="96acd-114">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="96acd-115">No Gerenciador de Soluções, clique duas vezes no nó **Serviços Conectados** do projeto (para um projeto do .NET Core ou .NET Standard, essa opção está disponível quando você clica com o botão direito do mouse no nó **Dependências** do projeto no Gerenciador de Soluções).</span><span class="sxs-lookup"><span data-stu-id="96acd-115">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

<span data-ttu-id="96acd-116">A página **Serviços Conectados** é exibida, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="96acd-116">The **Connected Services** page appears as shown in the following image:</span></span>

![Guia Serviços Conectados](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="96acd-118">Na página **Serviços Conectados**, clique em **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="96acd-118">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="96acd-119">Isso apresenta o assistente **Configurar a WCF Web Service Reference**:</span><span class="sxs-lookup"><span data-stu-id="96acd-119">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

![Guia Ponto de Extremidade de Serviço](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="96acd-121">Selecione um serviço.</span><span class="sxs-lookup"><span data-stu-id="96acd-121">Select a service.</span></span>

    <span data-ttu-id="96acd-122">3a.</span><span class="sxs-lookup"><span data-stu-id="96acd-122">3a.</span></span> <span data-ttu-id="96acd-123">Há várias opções de pesquisa de serviços disponíveis no assistente **Configurar a WCF Web Service Reference**:</span><span class="sxs-lookup"><span data-stu-id="96acd-123">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>
    
     * <span data-ttu-id="96acd-124">Para pesquisar serviços definidos na solução atual, clique no botão **Descobrir**.</span><span class="sxs-lookup"><span data-stu-id="96acd-124">To search for services defined in the current solution, click the **Discover** button.</span></span> 
     * <span data-ttu-id="96acd-125">Para pesquisar serviços hospedados em um endereço especificado, insira uma URL de serviço na caixa **Endereço** e clique no botão **Ir**.</span><span class="sxs-lookup"><span data-stu-id="96acd-125">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="96acd-126">Para selecionar um arquivo WSDL que contenha as informações de metadados do serviço Web, clique no botão **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="96acd-126">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span> 
     
    <span data-ttu-id="96acd-127">3b.</span><span class="sxs-lookup"><span data-stu-id="96acd-127">3b.</span></span> <span data-ttu-id="96acd-128">Selecione o serviço na lista de resultados da pesquisa na caixa **Serviços**.</span><span class="sxs-lookup"><span data-stu-id="96acd-128">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="96acd-129">Se necessário, insira o namespace para o código gerado na caixa de texto **Namespace** correspondente.</span><span class="sxs-lookup"><span data-stu-id="96acd-129">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>
    
    <span data-ttu-id="96acd-130">3c.</span><span class="sxs-lookup"><span data-stu-id="96acd-130">3c.</span></span> <span data-ttu-id="96acd-131">Clique no botão **Avançar** para abrir as páginas **Opções de Tipo de Dados** e **Opções do Cliente**.</span><span class="sxs-lookup"><span data-stu-id="96acd-131">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="96acd-132">Como alternativa, clique no botão **Concluir** para usar as opções padrão.</span><span class="sxs-lookup"><span data-stu-id="96acd-132">Alternatively, click the **Finish** button to use the default options.</span></span>


4. <span data-ttu-id="96acd-133">O formulário **Opções de Tipo de Dados** permite que você refine as definições de configuração de referência do serviço gerado:</span><span class="sxs-lookup"><span data-stu-id="96acd-133">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

![Guia Opções de tipo de dados](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> <span data-ttu-id="96acd-135">A opção da caixa de seleção **Usar novamente os tipos em assemblies consultados** é útil quando os tipos de dados necessários para a geração de código da referência de serviço são definidos em um dos assemblies referenciados do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="96acd-135">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="96acd-136">É importante reutilizar esses tipos de dados existentes para evitar problemas de conflito de tipo de tempo de compilação ou problemas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="96acd-136">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

<span data-ttu-id="96acd-137">Pode haver um atraso enquanto as informações de tipo são carregadas, dependendo do número de dependências do projeto e de outros fatores de desempenho do sistema.</span><span class="sxs-lookup"><span data-stu-id="96acd-137">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="96acd-138">O botão **Concluir** será desabilitado durante o carregamento, a menos que a caixa de seleção **Usar novamente os tipos em assemblies consultados** esteja desmarcada.</span><span class="sxs-lookup"><span data-stu-id="96acd-138">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="96acd-139">Clique em **Concluir** quando terminar.</span><span class="sxs-lookup"><span data-stu-id="96acd-139">Click **Finish** when you are done.</span></span>


<span data-ttu-id="96acd-140">Enquanto exibe o andamento, a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="96acd-140">While displaying progress, the tool:</span></span>

* <span data-ttu-id="96acd-141">Baixa metadados do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="96acd-141">Downloads metadata from the WCF service.</span></span> 
* <span data-ttu-id="96acd-142">Gera o código de referência de serviço em um arquivo chamado *reference.cs* e o adiciona ao seu projeto no nó **Serviços Conectados**.</span><span class="sxs-lookup"><span data-stu-id="96acd-142">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span> 
* <span data-ttu-id="96acd-143">Atualiza o arquivo de projeto (.csproj) com as referências de pacote NuGet necessárias para compilar e executar na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="96acd-143">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Janela de progresso](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="96acd-145">Quando esses processos forem concluídos, você poderá criar uma instância do tipo de cliente do WCF gerado e invocar as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="96acd-145">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="96acd-146">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="96acd-146">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="96acd-147">Perguntas e comentários</span><span class="sxs-lookup"><span data-stu-id="96acd-147">Feedback & questions</span></span>
<span data-ttu-id="96acd-148">Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="96acd-148">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="96acd-149">Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="96acd-149">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="96acd-150">Notas de Versão</span><span class="sxs-lookup"><span data-stu-id="96acd-150">Release notes</span></span>
* <span data-ttu-id="96acd-151">Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="96acd-151">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span> 
