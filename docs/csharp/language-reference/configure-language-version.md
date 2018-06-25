---
title: Selecionar a versão da linguagem C# – Guia do C#
description: Configure o compilador para executar a validação de sintaxe usando uma versão específica de compilador
ms.date: 05/24/2018
ms.openlocfilehash: 2056a99544d0cac94bc7cc79e8cd8793b1bcff78
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566303"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="b58a1-103">Selecionar a versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b58a1-103">Select the C# language version</span></span>

<span data-ttu-id="b58a1-104">O compilador C# usa como padrão a última versão principal da linguagem que foi liberada.</span><span class="sxs-lookup"><span data-stu-id="b58a1-104">The C# compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="b58a1-105">Você pode optar por compilar qualquer projeto usando uma nova versão de ponto da linguagem.</span><span class="sxs-lookup"><span data-stu-id="b58a1-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="b58a1-106">A escolha de uma versão mais recente da linguagem permite que o projeto use as últimas funcionalidades da linguagem.</span><span class="sxs-lookup"><span data-stu-id="b58a1-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="b58a1-107">Em outros cenários, talvez você precise validar se um projeto é compilado por completo ao usar uma versão mais antiga da linguagem.</span><span class="sxs-lookup"><span data-stu-id="b58a1-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="b58a1-108">Essa funcionalidade separa a decisão de instalar novas versões do SDK e das ferramentas no ambiente de desenvolvimento da decisão de incorporar novas funcionalidades da linguagem em um projeto.</span><span class="sxs-lookup"><span data-stu-id="b58a1-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="b58a1-109">Instale o último SDK e as últimas ferramentas no computador de build.</span><span class="sxs-lookup"><span data-stu-id="b58a1-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="b58a1-110">Cada projeto pode ser configurado para usar uma versão específica da linguagem de seu build.</span><span class="sxs-lookup"><span data-stu-id="b58a1-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="b58a1-111">Há várias maneiras de definir a versão da linguagem:</span><span class="sxs-lookup"><span data-stu-id="b58a1-111">There are several ways to set the language version:</span></span>

- <span data-ttu-id="b58a1-112">Depender de uma [ação rápida do Visual Studio](#visual-studio-quick-action).</span><span class="sxs-lookup"><span data-stu-id="b58a1-112">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="b58a1-113">Definir a versão da linguagem na [interface do usuário do Visual Studio](#set-the-language-version-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b58a1-113">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="b58a1-114">Editar manualmente o arquivo [**.csproj**](#edit-the-csproj-file).</span><span class="sxs-lookup"><span data-stu-id="b58a1-114">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="b58a1-115">Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="b58a1-115">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="b58a1-116">Configurar a opção [`-langversion` do compilador](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="b58a1-116">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="b58a1-117">Ação rápida do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b58a1-117">Visual Studio quick action</span></span>

<span data-ttu-id="b58a1-118">O Visual Studio ajuda você a determinar a versão da linguagem necessária.</span><span class="sxs-lookup"><span data-stu-id="b58a1-118">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="b58a1-119">Se você usar uma funcionalidade de linguagem que não está disponível para a versão atualmente configurada, o Visual Studio mostrará uma correção potencial para atualizar a versão da linguagem do projeto.</span><span class="sxs-lookup"><span data-stu-id="b58a1-119">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="b58a1-120">Definir a versão da linguagem no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b58a1-120">Set the language version in Visual Studio</span></span>

<span data-ttu-id="b58a1-121">Você pode definir a versão no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b58a1-121">You can set the version in Visual Studio.</span></span> <span data-ttu-id="b58a1-122">Clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b58a1-122">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="b58a1-123">Selecione a guia **Build** e o botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="b58a1-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="b58a1-124">Na lista suspensa, selecione a versão.</span><span class="sxs-lookup"><span data-stu-id="b58a1-124">In the dropdown, select the version.</span></span> <span data-ttu-id="b58a1-125">A seguinte imagem mostra a "última" configuração:</span><span class="sxs-lookup"><span data-stu-id="b58a1-125">The following image shows the "latest" setting:</span></span>

![Captura de tela de configurações avançadas de build nas quais é possível especificar a versão da linguagem](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="b58a1-127">Se você usar o IDE do Visual Studio para atualizar os arquivos csproj, o IDE criará nós separados para cada configuração de build.</span><span class="sxs-lookup"><span data-stu-id="b58a1-127">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="b58a1-128">Normalmente, você definirá o valor da mesma forma em todas as configurações de build, mas precisará defini-lo explicitamente para cada configuração de build ou selecionar "Todas as Configurações" ao modificar essa configuração.</span><span class="sxs-lookup"><span data-stu-id="b58a1-128">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="b58a1-129">Você verá o seguinte no arquivo csproj:</span><span class="sxs-lookup"><span data-stu-id="b58a1-129">You'll see the following in your csproj file:</span></span>
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a><span data-ttu-id="b58a1-130">Editar o arquivo csproj</span><span class="sxs-lookup"><span data-stu-id="b58a1-130">Edit the csproj file</span></span>

<span data-ttu-id="b58a1-131">Você pode definir a versão da linguagem no arquivo **.csproj**.</span><span class="sxs-lookup"><span data-stu-id="b58a1-131">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="b58a1-132">Adicione um elemento como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b58a1-132">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="b58a1-133">O valor `latest` usa a última versão secundária da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="b58a1-133">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="b58a1-134">Os valores válidos são:</span><span class="sxs-lookup"><span data-stu-id="b58a1-134">Valid values are:</span></span>

|<span data-ttu-id="b58a1-135">Valor</span><span class="sxs-lookup"><span data-stu-id="b58a1-135">Value</span></span>|<span data-ttu-id="b58a1-136">Significado</span><span class="sxs-lookup"><span data-stu-id="b58a1-136">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="b58a1-137">default</span><span class="sxs-lookup"><span data-stu-id="b58a1-137">default</span></span>|<span data-ttu-id="b58a1-138">O compilador aceita toda a sintaxe de linguagem válida da versão principal mais recente à qual dá suporte.</span><span class="sxs-lookup"><span data-stu-id="b58a1-138">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="b58a1-139">ISO-1</span><span class="sxs-lookup"><span data-stu-id="b58a1-139">ISO-1</span></span>|<span data-ttu-id="b58a1-140">O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2003 C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="b58a1-140">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
|<span data-ttu-id="b58a1-141">ISO-2</span><span class="sxs-lookup"><span data-stu-id="b58a1-141">ISO-2</span></span>|<span data-ttu-id="b58a1-142">O compilador aceita somente a sintaxe incluída no ISO/IEC 23270:2006 C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="b58a1-142">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="b58a1-143">3</span><span class="sxs-lookup"><span data-stu-id="b58a1-143">3</span></span>|<span data-ttu-id="b58a1-144">O compilador aceita somente a sintaxe incluída no C# 3.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-144">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="b58a1-145">4</span><span class="sxs-lookup"><span data-stu-id="b58a1-145">4</span></span>|<span data-ttu-id="b58a1-146">O compilador aceita somente a sintaxe incluída no C# 4.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-146">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="b58a1-147">5</span><span class="sxs-lookup"><span data-stu-id="b58a1-147">5</span></span>|<span data-ttu-id="b58a1-148">O compilador aceita somente a sintaxe incluída no C# 5.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-148">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="b58a1-149">6</span><span class="sxs-lookup"><span data-stu-id="b58a1-149">6</span></span>|<span data-ttu-id="b58a1-150">O compilador aceita somente a sintaxe incluída no C# 6.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-150">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="b58a1-151">7</span><span class="sxs-lookup"><span data-stu-id="b58a1-151">7</span></span>|<span data-ttu-id="b58a1-152">O compilador aceita somente a sintaxe incluída no C# 7.0 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-152">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="b58a1-153">7.1</span><span class="sxs-lookup"><span data-stu-id="b58a1-153">7.1</span></span>|<span data-ttu-id="b58a1-154">O compilador aceita somente a sintaxe incluída no C# 7.1 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="b58a1-155">7.2</span><span class="sxs-lookup"><span data-stu-id="b58a1-155">7.2</span></span>|<span data-ttu-id="b58a1-156">O compilador aceita somente a sintaxe incluída no C# 7.2 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-156">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="b58a1-157">7.3</span><span class="sxs-lookup"><span data-stu-id="b58a1-157">7.3</span></span>|<span data-ttu-id="b58a1-158">O compilador aceita somente a sintaxe incluída no C# 7.3 ou inferior.</span><span class="sxs-lookup"><span data-stu-id="b58a1-158">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="b58a1-159">mais recente</span><span class="sxs-lookup"><span data-stu-id="b58a1-159">latest</span></span>|<span data-ttu-id="b58a1-160">O compilador aceita toda a sintaxe de linguagem à qual dá suporte.</span><span class="sxs-lookup"><span data-stu-id="b58a1-160">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="b58a1-161">As cadeias de caracteres especiais `default` e `latest` são resolvidas nas últimas versões da linguagem principal (C# 7.0) e secundária (C# 7.3) instaladas no computador de build, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b58a1-161">The special strings `default` and `latest` resolve to the latest major (C# 7.0) and minor (C# 7.3) language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="b58a1-162">Configurar vários projetos</span><span class="sxs-lookup"><span data-stu-id="b58a1-162">Configure multiple projects</span></span>

<span data-ttu-id="b58a1-163">Crie um arquivo **Directory.build.props** que contém o elemento `<LangVersion>` para configurar vários diretórios.</span><span class="sxs-lookup"><span data-stu-id="b58a1-163">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="b58a1-164">Normalmente, você faz isso no diretório da solução.</span><span class="sxs-lookup"><span data-stu-id="b58a1-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="b58a1-165">Adicione o seguinte a um arquivo **Directory.build.props** no diretório de solução:</span><span class="sxs-lookup"><span data-stu-id="b58a1-165">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="b58a1-166">Agora, os builds de cada subdiretório do diretório que contém esse arquivo usarão a sintaxe C# versão 7.3.</span><span class="sxs-lookup"><span data-stu-id="b58a1-166">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="b58a1-167">Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build.md).</span><span class="sxs-lookup"><span data-stu-id="b58a1-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build.md).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="b58a1-168">Definir a opção langversion do compilador</span><span class="sxs-lookup"><span data-stu-id="b58a1-168">Set the langversion compiler option</span></span>

<span data-ttu-id="b58a1-169">Você pode usar a opção `-langversion` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b58a1-169">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="b58a1-170">Para obter mais informações, confira o artigo sobre a opção [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) do compilador.</span><span class="sxs-lookup"><span data-stu-id="b58a1-170">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b58a1-171">Veja uma lista dos valores válidos digitando `csc -langversion:?`.</span><span class="sxs-lookup"><span data-stu-id="b58a1-171">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
