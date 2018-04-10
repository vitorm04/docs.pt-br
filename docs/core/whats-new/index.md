---
title: Novidades do .NET Core 2.0
description: Conheça os novos recursos encontrados no .NET Core.
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 749f0502b5c80ed3d6b81d2036e7591e3f1fe08a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="cd7f0-104">Novidades do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-104">What's new in .NET Core</span></span>

<span data-ttu-id="cd7f0-105">O .NET Core 2.0 contém melhorias e novos recursos nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-105">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="cd7f0-106">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="cd7f0-106">Tooling</span></span>](#tooling)
- [<span data-ttu-id="cd7f0-107">Suporte a idiomas</span><span class="sxs-lookup"><span data-stu-id="cd7f0-107">Language support</span></span>](#language-support)
- [<span data-ttu-id="cd7f0-108">Aprimoramentos da plataforma</span><span class="sxs-lookup"><span data-stu-id="cd7f0-108">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="cd7f0-109">Alterações na API</span><span class="sxs-lookup"><span data-stu-id="cd7f0-109">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="cd7f0-110">Integração com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd7f0-110">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="cd7f0-111">Aprimoramentos de documentação</span><span class="sxs-lookup"><span data-stu-id="cd7f0-111">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="cd7f0-112">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="cd7f0-112">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="cd7f0-113">dotnet restore é executado implicitamente</span><span class="sxs-lookup"><span data-stu-id="cd7f0-113">dotnet restore runs implicitly</span></span>

<span data-ttu-id="cd7f0-114">Em versões anteriores do .NET Core, era preciso executar o comando [dotnet restore](../tools/dotnet-restore.md) para baixar dependências logo após a criação de um novo projeto com o comando [dotnet new](../tools/dotnet-new.md), bem como sempre que uma nova dependência era adicionada ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-114">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="cd7f0-115">Você também pode desabilitar a invocação automática do `dotnet restore` transmitindo a opção `--no-restore` para os comandos `new`, `run`, `build`, `publish`, `pack` e `test`.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-115">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="cd7f0-116">Redirecionar para o .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd7f0-116">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="cd7f0-117">Se o SDK do .NET Core 2.0 estiver instalado, os projetos destinados ao .NET Core 1.x poderão ser redirecionados para o .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-117">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="cd7f0-118">Para redirecionar para o .NET Core 2.0, edite o arquivo do projeto alterando o valor do elemento `<TargetFramework>` (ou o elemento `<TargetFrameworks>` se você tiver mais de um destino no seu arquivo de projeto) de 1.x para 2.0:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-118">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="cd7f0-119">Você também pode redirecionar bibliotecas do .NET Standard para o .NET Standard 2.0 da mesma maneira:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-119">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="cd7f0-120">Para mais informações sobre como migrar seu projeto para o .NET Core 2.0, confira [Migrar do ASP.NET Core 1.x para o ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="cd7f0-120">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="cd7f0-121">Suporte a linguagens</span><span class="sxs-lookup"><span data-stu-id="cd7f0-121">Language support</span></span>

<span data-ttu-id="cd7f0-122">Além do suporte a C# e F#, o .NET Core 2.0 também suporta Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-122">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="cd7f0-123">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd7f0-123">Visual Basic</span></span>

<span data-ttu-id="cd7f0-124">Com a versão 2.0, o .NET Core agora oferece suporte para o Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-124">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="cd7f0-125">Você pode usar o Visual Basic para criar os seguintes tipos de projeto:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-125">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="cd7f0-126">Aplicativo de console do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-126">.NET Core console apps</span></span>
- <span data-ttu-id="cd7f0-127">Bibliotecas de classe do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-127">.NET Core class libraries</span></span>
- <span data-ttu-id="cd7f0-128">Bibliotecas de classe do .NET Standard</span><span class="sxs-lookup"><span data-stu-id="cd7f0-128">.NET Standard class libraries</span></span>
- <span data-ttu-id="cd7f0-129">Projetos de testes de unidade do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-129">.NET Core unit test projects</span></span>
- <span data-ttu-id="cd7f0-130">Projetos de testes de xUnit do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-130">.NET Core xUnit test projects</span></span>

<span data-ttu-id="cd7f0-131">Por exemplo, para criar um aplicativo "Olá, Mundo" do Visual Basic, siga as seguintes etapas da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-131">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="cd7f0-132">Abra uma janela do console, crie um diretório para seu projeto e torne-o o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-132">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="cd7f0-133">Insira o comando `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-133">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="cd7f0-134">O comando cria um arquivo de projeto com uma extensão de arquivo `.vbproj`, junto com um arquivo de código-fonte do Visual Basic chamado *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-134">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="cd7f0-135">Este arquivo contém o código-fonte para gravar a cadeia de caracteres "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="cd7f0-135">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="cd7f0-136">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-136">to the console window.</span></span>

1.  <span data-ttu-id="cd7f0-137">Insira o comando `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-137">Enter the command `dotnet run`.</span></span> <span data-ttu-id="cd7f0-138">As [ferramentas .NET Core CLI](../tools/index.md) compilam e executam automaticamente o aplicativo, que exibe a mensagem "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="cd7f0-138">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="cd7f0-139">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-139">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="cd7f0-140">Suporte para C# 7.1</span><span class="sxs-lookup"><span data-stu-id="cd7f0-140">Support for C# 7.1</span></span>

<span data-ttu-id="cd7f0-141">O .NET Core 2.0 suporta C# 7.1, que adiciona uma série de novos recursos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-141">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="cd7f0-142">O método `Main`, o ponto de entrada do aplicativo, pode ser marcado com a palavra-chave [async](../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="cd7f0-142">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="cd7f0-143">Nomes de tuplas inferidos.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-143">Inferred tuple names.</span></span>
- <span data-ttu-id="cd7f0-144">Expressões padrão.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-144">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="cd7f0-145">Aprimoramentos da plataforma</span><span class="sxs-lookup"><span data-stu-id="cd7f0-145">Platform improvements</span></span>

<span data-ttu-id="cd7f0-146">O .NET Core 2.0 inclui uma série de recursos que facilitam a instalação do .NET Core e o uso dele em sistemas operacionais com suporte.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-146">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="cd7f0-147">O .NET Core para Linux é uma implementação única</span><span class="sxs-lookup"><span data-stu-id="cd7f0-147">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="cd7f0-148">O .NET Core 2.0 oferece uma implementação única do Linux que funciona em várias distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-148">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="cd7f0-149">O .NET Core 1.x requer que você baixe uma implementação do Linux específica para distribuição.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-149">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="cd7f0-150">Você também pode desenvolver aplicativos destinados ao Linux como um sistema operacional único.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-150">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="cd7f0-151">O .NET Core 1.x requer que você direcione cada distribuição do Linux separadamente.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-151">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="cd7f0-152">Suporte para as bibliotecas criptográficas da Apple</span><span class="sxs-lookup"><span data-stu-id="cd7f0-152">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="cd7f0-153">O .NET Core 1.x no macOS exigia a biblioteca criptográfica do kit de ferramentas OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-153">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="cd7f0-154">O .NET Core 2.0 usa as bibliotecas criptográficas da Apple e não requer o OpenSSL, portanto, não é mais preciso instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-154">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="cd7f0-155">Alterações de API e suporte à biblioteca</span><span class="sxs-lookup"><span data-stu-id="cd7f0-155">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="cd7f0-156">Suporte para .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="cd7f0-156">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="cd7f0-157">O .NET Standard define um conjunto com versões das APIs que devem estar disponíveis em implementações .NET que estejam de acordo com a versão standard.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-157">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="cd7f0-158">O .NET Standard é destinado a desenvolvedores de bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-158">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="cd7f0-159">O objetivo dele é garantir a funcionalidade que está disponível para uma biblioteca destinada a uma versão do .NET Standard em cada implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-159">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="cd7f0-160">O .NET Core 1.x dá suporte ao .NET Standard versão 1.6; o .NET Core 2.0 dá suporte à versão mais recente, o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-160">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="cd7f0-161">Para obter mais informações, confira [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="cd7f0-161">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="cd7f0-162">O .NET Standard 2.0 inclui 20.000 APIs a mais do que havia disponível no .NET Standard 1.6.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-162">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="cd7f0-163">A maior parte dessa área de superfície expandida resulta da incorporação de APIs que são comuns ao .NET Framework e Xamarin no .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-163">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="cd7f0-164">As bibliotecas de classe .NET Standard 2.0 também podem fazer referência às bibliotecas de classe do .NET Framework, desde que elas chamem APIs que estão presentes no .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-164">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="cd7f0-165">Nenhuma recompilação das bibliotecas do .NET Framework é necessária.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-165">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="cd7f0-166">Para obter uma lista com as APIs que foram adicionadas ao .NET Standard desde a última versão, o .NET Standard 1.6, confira [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="cd7f0-166">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="cd7f0-167">Área de superfície expandida</span><span class="sxs-lookup"><span data-stu-id="cd7f0-167">Expanded surface area</span></span>

<span data-ttu-id="cd7f0-168">O número total de APIs disponíveis no .NET Core 2.0 mais que dobrou em comparação com o .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-168">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="cd7f0-169">E com o [Pacote de Compatibilidade do Windows](../porting/windows-compat-pack.md), a portabilidade do .NET Framework também se tornou muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-169">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="cd7f0-170">Suporte a bibliotecas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cd7f0-170">Support for .NET Framework libraries</span></span>

<span data-ttu-id="cd7f0-171">O código .NET Core pode fazer referência a bibliotecas existentes do .NET Framework, incluindo pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-171">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="cd7f0-172">Observe que as bibliotecas devem usar APIs que são encontradas no .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-172">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="cd7f0-173">integração com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cd7f0-173">Visual Studio integration</span></span>

<span data-ttu-id="cd7f0-174">O Visual Studio 2017 versão 15.3 e, em alguns casos, o Visual Studio para Mac oferece vários aprimoramentos significativos para os desenvolvedores do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-174">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="cd7f0-175">Redirecionamento de aplicativos .NET Core e bibliotecas do .NET Standard</span><span class="sxs-lookup"><span data-stu-id="cd7f0-175">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="cd7f0-176">Se o SDK do .NET Core 2.0 estiver instalado, você poderá redirecionar projetos do .NET Core 1.x para o .NET Core 2.0 e bibliotecas do .NET Standard 1.x para o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-176">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="cd7f0-177">Para redirecionar seu projeto no Visual Studio, abra a guia **Aplicativo** da caixa de diálogo de propriedades do projeto e altere o valor **Estrutura de destino** para **.NET Core 2.0** ou **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-177">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="cd7f0-178">Você também pode alterar clicando com o botão direito do mouse no projeto e selecionando a opção **Editar \*arquivo .csproj**.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-178">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="cd7f0-179">Para obter mais informações, confira a seção [Ferramentas](#tooling) neste tópico.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-179">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="cd7f0-180">Suporte a Live Unit Testing para .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-180">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="cd7f0-181">Sempre que você modifica o código, o Live Unit Testing executa os testes de unidade afetados automaticamente em segundo plano e exibe os resultados e a cobertura de código de forma dinâmica no ambiente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-181">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="cd7f0-182">O .NET Core 2.0 agora oferece suporte ao Live Unit Testing.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-182">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="cd7f0-183">Anteriormente, o Live Unit Testing estava disponível somente para aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-183">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="cd7f0-184">Para obter mais informações, confira [Live Unit Testing com o Visual Studio 2017](/visualstudio/test/live-unit-testing) e [Perguntas Frequentes sobre o Live Unit Testing](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="cd7f0-184">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="cd7f0-185">Melhor suporte a várias estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="cd7f0-185">Better support for multiple target frameworks</span></span>

<span data-ttu-id="cd7f0-186">Se você estiver criando um projeto para várias estruturas de destino, selecione a plataforma de destino no menu de nível superior.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-186">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="cd7f0-187">Na imagem a seguir, um projeto denominado SCD1 destinado ao Mac OS X 10.11 (`osx.10.11-x64`) de 64 bits e ao Windows 10/Windows Server 2016 (`win10-x64`) de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-187">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="cd7f0-188">Selecione a estrutura de destino antes de selecionar o botão do projeto, neste caso para executar um build de depuração.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-188">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Selecionar a estrutura de destino ao criar um projeto](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="cd7f0-190">Suporte lado a lado para SDKs do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd7f0-190">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="cd7f0-191">Agora você pode instalar o SDK do .NET Core independentemente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-191">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="cd7f0-192">Isso possibilita que uma única versão do Visual Studio crie projetos destinados a diferentes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-192">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="cd7f0-193">Anteriormente, o Visual Studio e o SDK do .NET Core foram acoplados; uma versão específica do SDK acompanhava uma versão específica do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-193">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="cd7f0-194">Aprimoramentos de documentação</span><span class="sxs-lookup"><span data-stu-id="cd7f0-194">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="cd7f0-195">Arquitetura do Aplicativo .NET</span><span class="sxs-lookup"><span data-stu-id="cd7f0-195">.NET Application Architecture</span></span>

<span data-ttu-id="cd7f0-196">A [Arquitetura do Aplicativo .NET](https://www.microsoft.com/net/learn/architecture) proporciona o acesso a um conjunto de livros eletrônicos que oferecem diretrizes, práticas recomendadas e aplicativos de exemplo ao usar o .NET para compilar:</span><span class="sxs-lookup"><span data-stu-id="cd7f0-196">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="cd7f0-197">Contêineres de Microsserviços e Docker.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-197">Microservices and Docker containers.</span></span>
- <span data-ttu-id="cd7f0-198">Aplicativos Web com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-198">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="cd7f0-199">Aplicativos móveis com Xamarin.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-199">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="cd7f0-200">Aplicativos que são implantados na nuvem com o Azure.</span><span class="sxs-lookup"><span data-stu-id="cd7f0-200">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd7f0-201">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd7f0-201">See also</span></span>
 [<span data-ttu-id="cd7f0-202">Novidades do ASP.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="cd7f0-202">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
