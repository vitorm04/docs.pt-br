---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba mais sobre como a versão da linguagem C# é determinada com base no seu projeto e os motivos por trás dessa escolha. Saiba como substituir o padrão manualmente.
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: 24797c564890b034683d2989010bc694aabc423c
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811945"
---
# <a name="c-language-versioning"></a><span data-ttu-id="2a5b1-104">Controle de versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2a5b1-104">C# language versioning</span></span>

<span data-ttu-id="2a5b1-105">O compilador do C# mais recente determina uma versão da linguagem padrão com base nas estruturas de destino do projeto.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="2a5b1-106">O Visual Studio não fornece uma interface do usuário para alterar o valor, mas você pode alterá-lo editando o arquivo *csproj* .</span><span class="sxs-lookup"><span data-stu-id="2a5b1-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="2a5b1-107">A escolha do padrão garante que você use a versão de idioma mais recente compatível com a estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="2a5b1-108">Você se beneficia do acesso aos recursos de linguagem mais recentes compatíveis com o destino do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="2a5b1-109">Essa opção padrão também garante que você não use uma linguagem que exija tipos ou comportamento de tempo de execução não disponível em sua estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="2a5b1-110">Escolher uma versão de idioma mais recente do que o padrão pode causar dificuldade para diagnosticar erros de tempo de compilação e Runtime.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="2a5b1-111">As regras neste artigo se aplicam ao compilador fornecido com o Visual Studio 2019 ou o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="2a5b1-112">Os compiladores do C# que fazem parte da instalação do Visual Studio 2017 ou de versões anteriores do SDK do .NET Core são direcionados ao C# 7.0 por padrão.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="2a5b1-113">O C# 8,0 (e superior) tem suporte apenas no .NET Core 3. x e em versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="2a5b1-114">Muitos dos recursos mais recentes exigem recursos de biblioteca e tempo de execução introduzidos no .NET Core 3. x:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="2a5b1-115">A [implementação de interface padrão](../whats-new/csharp-8.md#default-interface-methods) requer novos recursos no .net Core 3,0 CLR.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="2a5b1-116">Os [fluxos assíncronos](../whats-new/csharp-8.md#asynchronous-streams) exigem os novos tipos <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2a5b1-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="2a5b1-117">[Índices e intervalos](../whats-new/csharp-8.md#indices-and-ranges) exigem os novos tipos <xref:System.Index?displayProperty=nameWithType> e <xref:System.Range?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2a5b1-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="2a5b1-118">Os [tipos de referência anuláveis](../whats-new/csharp-8.md#nullable-reference-types) fazem uso de vários [atributos](attributes/nullable-analysis.md) para fornecer avisos melhores.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="2a5b1-119">Esses atributos foram adicionados no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="2a5b1-120">Outras estruturas de destino não foram anotadas com nenhum desses atributos.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="2a5b1-121">Isso significa que os avisos anuláveis podem não refletir com precisão possíveis problemas.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="2a5b1-122">Padrões</span><span class="sxs-lookup"><span data-stu-id="2a5b1-122">Defaults</span></span>

<span data-ttu-id="2a5b1-123">O compilador determina um padrão com base nestas regras:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-123">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="2a5b1-124">Estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="2a5b1-124">Target framework</span></span> | <span data-ttu-id="2a5b1-125">version</span><span class="sxs-lookup"><span data-stu-id="2a5b1-125">version</span></span> | <span data-ttu-id="2a5b1-126">Padrão da versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2a5b1-126">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="2a5b1-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a5b1-127">.NET Core</span></span>        | <span data-ttu-id="2a5b1-128">3.x</span><span class="sxs-lookup"><span data-stu-id="2a5b1-128">3.x</span></span>     | <span data-ttu-id="2a5b1-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="2a5b1-129">C# 8.0</span></span>                      |
| <span data-ttu-id="2a5b1-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a5b1-130">.NET Core</span></span>        | <span data-ttu-id="2a5b1-131">2. x</span><span class="sxs-lookup"><span data-stu-id="2a5b1-131">2.x</span></span>     | <span data-ttu-id="2a5b1-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="2a5b1-132">C# 7.3</span></span>                      |
| <span data-ttu-id="2a5b1-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a5b1-133">.NET Standard</span></span>    | <span data-ttu-id="2a5b1-134">2.1</span><span class="sxs-lookup"><span data-stu-id="2a5b1-134">2.1</span></span>     | <span data-ttu-id="2a5b1-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="2a5b1-135">C# 8.0</span></span>                      |
| <span data-ttu-id="2a5b1-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a5b1-136">.NET Standard</span></span>    | <span data-ttu-id="2a5b1-137">2.0</span><span class="sxs-lookup"><span data-stu-id="2a5b1-137">2.0</span></span>     | <span data-ttu-id="2a5b1-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="2a5b1-138">C# 7.3</span></span>                      |
| <span data-ttu-id="2a5b1-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a5b1-139">.NET Standard</span></span>    | <span data-ttu-id="2a5b1-140">1.x</span><span class="sxs-lookup"><span data-stu-id="2a5b1-140">1.x</span></span>     | <span data-ttu-id="2a5b1-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="2a5b1-141">C# 7.3</span></span>                      |
| <span data-ttu-id="2a5b1-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2a5b1-142">.NET Framework</span></span>   | <span data-ttu-id="2a5b1-143">all</span><span class="sxs-lookup"><span data-stu-id="2a5b1-143">all</span></span>     | <span data-ttu-id="2a5b1-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="2a5b1-144">C# 7.3</span></span>                      |

<span data-ttu-id="2a5b1-145">Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="2a5b1-146">Você usa os recursos mais recentes com essa visualização em qualquer ambiente, sem afetar projetos direcionados a uma versão lançada do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!TIP]
> <span data-ttu-id="2a5b1-147">Para saber qual versão de idioma você está usando no momento, coloque `#error version` (diferencia maiúsculas de minúsculas) em seu código.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-147">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="2a5b1-148">Isso faz com que o compilador produza um diagnóstico, CS8304, com uma mensagem que contém a versão do compilador que está sendo usada e a versão atual do idioma selecionado.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-148">This makes the compiler produce a diagnostic, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="2a5b1-149">Substituir um padrão</span><span class="sxs-lookup"><span data-stu-id="2a5b1-149">Override a default</span></span>

<span data-ttu-id="2a5b1-150">Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-150">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="2a5b1-151">Edite manualmente o [arquivo de projeto](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="2a5b1-151">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="2a5b1-152">Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="2a5b1-152">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="2a5b1-153">Configure a [ `-langversion` opção do compilador](compiler-options/langversion-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2a5b1-153">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="2a5b1-154">Editar o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="2a5b1-154">Edit the project file</span></span>

<span data-ttu-id="2a5b1-155">É possível definir a versão da linguagem em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-155">You can set the language version in your project file.</span></span> <span data-ttu-id="2a5b1-156">Por exemplo, se você quiser explicitamente acesso às versões prévias dos recursos, adicione um elemento como este:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-156">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="2a5b1-157">O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-157">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="2a5b1-158">Configurar vários projetos</span><span class="sxs-lookup"><span data-stu-id="2a5b1-158">Configure multiple projects</span></span>

<span data-ttu-id="2a5b1-159">Para configurar vários projetos, você pode criar um arquivo **Directory. Build. props** que contém o `<LangVersion>` elemento.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-159">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="2a5b1-160">Normalmente, você faz isso no diretório da solução.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-160">You typically do that in your solution directory.</span></span> <span data-ttu-id="2a5b1-161">Adicione o seguinte a um arquivo **Directory. Build. props** no diretório da solução:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-161">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="2a5b1-162">As compilações em todos os subdiretórios do diretório que contém esse arquivo usarão a versão preview C#.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-162">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="2a5b1-163">Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="2a5b1-163">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="2a5b1-164">Referência à versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2a5b1-164">C# language version reference</span></span>

<span data-ttu-id="2a5b1-165">A tabela a seguir mostra todas as versões atuais da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-165">The following table shows all current C# language versions.</span></span> <span data-ttu-id="2a5b1-166">Seu compilador pode não entender necessariamente todos os valores se for mais antigo.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-166">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="2a5b1-167">Se você instalar o .NET Core 3,0 ou posterior, terá acesso a todos os itens listados.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-167">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="2a5b1-168">Abra o [prompt de comando do desenvolvedor para o Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)e execute o comando a seguir para ver a lista de versões de idioma disponíveis em seu computador.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-168">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="2a5b1-169">Questionando a opção de compilação [-langversion](compiler-options/langversion-compiler-option.md) como essa, imprimirá algo semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-169">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
