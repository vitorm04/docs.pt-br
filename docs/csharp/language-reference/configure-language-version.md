---
title: Controle de versão da linguagem C# – Guia de C#
description: Saiba mais sobre como a versão da linguagem C# é determinada com base no seu projeto e os motivos por trás dessa escolha. Saiba como substituir o padrão manualmente.
ms.date: 05/20/2020
ms.openlocfilehash: bbe5b12e378cf47b7c9b2c8576088e949e526a9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803001"
---
# <a name="c-language-versioning"></a><span data-ttu-id="3e30c-104">Controle de versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3e30c-104">C# language versioning</span></span>

<span data-ttu-id="3e30c-105">O compilador do C# mais recente determina uma versão da linguagem padrão com base nas estruturas de destino do projeto.</span><span class="sxs-lookup"><span data-stu-id="3e30c-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="3e30c-106">O Visual Studio não fornece uma interface do usuário para alterar o valor, mas você pode alterá-lo editando o arquivo *csproj* .</span><span class="sxs-lookup"><span data-stu-id="3e30c-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="3e30c-107">A escolha do padrão garante que você use a versão de idioma mais recente compatível com a estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="3e30c-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="3e30c-108">Você se beneficia do acesso aos recursos de linguagem mais recentes compatíveis com o destino do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3e30c-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="3e30c-109">Essa opção padrão também garante que você não use uma linguagem que exija tipos ou comportamento de tempo de execução não disponível em sua estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="3e30c-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="3e30c-110">Escolher uma versão de idioma mais recente do que o padrão pode causar dificuldade para diagnosticar erros de tempo de compilação e Runtime.</span><span class="sxs-lookup"><span data-stu-id="3e30c-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="3e30c-111">As regras neste artigo se aplicam ao compilador fornecido com o Visual Studio 2019 ou o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3e30c-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="3e30c-112">Os compiladores do C# que fazem parte da instalação do Visual Studio 2017 ou de versões anteriores do SDK do .NET Core são direcionados ao C# 7.0 por padrão.</span><span class="sxs-lookup"><span data-stu-id="3e30c-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="3e30c-113">O C# 8,0 (e superior) tem suporte apenas no .NET Core 3. x e em versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="3e30c-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="3e30c-114">Muitos dos recursos mais recentes exigem recursos de biblioteca e tempo de execução introduzidos no .NET Core 3. x:</span><span class="sxs-lookup"><span data-stu-id="3e30c-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="3e30c-115">A [implementação de interface padrão](../whats-new/csharp-8.md#default-interface-methods) requer novos recursos no .net Core 3,0 CLR.</span><span class="sxs-lookup"><span data-stu-id="3e30c-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="3e30c-116">Os [fluxos assíncronos](../whats-new/csharp-8.md#asynchronous-streams) exigem os novos tipos <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e30c-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="3e30c-117">[Índices e intervalos](../whats-new/csharp-8.md#indices-and-ranges) exigem os novos tipos <xref:System.Index?displayProperty=nameWithType> e <xref:System.Range?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e30c-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="3e30c-118">Os [tipos de referência anuláveis](../whats-new/csharp-8.md#nullable-reference-types) fazem uso de vários [atributos](attributes/nullable-analysis.md) para fornecer avisos melhores.</span><span class="sxs-lookup"><span data-stu-id="3e30c-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="3e30c-119">Esses atributos foram adicionados no .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3e30c-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="3e30c-120">Outras estruturas de destino não foram anotadas com nenhum desses atributos.</span><span class="sxs-lookup"><span data-stu-id="3e30c-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="3e30c-121">Isso significa que os avisos anuláveis podem não refletir com precisão possíveis problemas.</span><span class="sxs-lookup"><span data-stu-id="3e30c-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="3e30c-122">Padrões</span><span class="sxs-lookup"><span data-stu-id="3e30c-122">Defaults</span></span>

<span data-ttu-id="3e30c-123">O compilador determina um padrão com base nestas regras:</span><span class="sxs-lookup"><span data-stu-id="3e30c-123">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="3e30c-124">Estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="3e30c-124">Target framework</span></span> | <span data-ttu-id="3e30c-125">version</span><span class="sxs-lookup"><span data-stu-id="3e30c-125">version</span></span> | <span data-ttu-id="3e30c-126">Padrão da versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3e30c-126">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="3e30c-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e30c-127">.NET Core</span></span>        | <span data-ttu-id="3e30c-128">3.x</span><span class="sxs-lookup"><span data-stu-id="3e30c-128">3.x</span></span>     | <span data-ttu-id="3e30c-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="3e30c-129">C# 8.0</span></span>                      |
| <span data-ttu-id="3e30c-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e30c-130">.NET Core</span></span>        | <span data-ttu-id="3e30c-131">2. x</span><span class="sxs-lookup"><span data-stu-id="3e30c-131">2.x</span></span>     | <span data-ttu-id="3e30c-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="3e30c-132">C# 7.3</span></span>                      |
| <span data-ttu-id="3e30c-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3e30c-133">.NET Standard</span></span>    | <span data-ttu-id="3e30c-134">2.1</span><span class="sxs-lookup"><span data-stu-id="3e30c-134">2.1</span></span>     | <span data-ttu-id="3e30c-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="3e30c-135">C# 8.0</span></span>                      |
| <span data-ttu-id="3e30c-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3e30c-136">.NET Standard</span></span>    | <span data-ttu-id="3e30c-137">2.0</span><span class="sxs-lookup"><span data-stu-id="3e30c-137">2.0</span></span>     | <span data-ttu-id="3e30c-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="3e30c-138">C# 7.3</span></span>                      |
| <span data-ttu-id="3e30c-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="3e30c-139">.NET Standard</span></span>    | <span data-ttu-id="3e30c-140">1.x</span><span class="sxs-lookup"><span data-stu-id="3e30c-140">1.x</span></span>     | <span data-ttu-id="3e30c-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="3e30c-141">C# 7.3</span></span>                      |
| <span data-ttu-id="3e30c-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e30c-142">.NET Framework</span></span>   | <span data-ttu-id="3e30c-143">all</span><span class="sxs-lookup"><span data-stu-id="3e30c-143">all</span></span>     | <span data-ttu-id="3e30c-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="3e30c-144">C# 7.3</span></span>                      |

<span data-ttu-id="3e30c-145">Quando seu projeto se destina a uma estrutura de visualização que tem uma versão da linguagem correspondente da visualização, a versão de linguagem usada é a de visualização.</span><span class="sxs-lookup"><span data-stu-id="3e30c-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="3e30c-146">Você usa os recursos mais recentes com essa visualização em qualquer ambiente, sem afetar projetos direcionados a uma versão lançada do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e30c-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="3e30c-147">Substituir um padrão</span><span class="sxs-lookup"><span data-stu-id="3e30c-147">Override a default</span></span>

<span data-ttu-id="3e30c-148">Se precisar especificar sua versão do C# explicitamente, poderá fazer isso de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="3e30c-148">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="3e30c-149">Edite manualmente o [arquivo de projeto](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="3e30c-149">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="3e30c-150">Definir a versão da linguagem [para vários projetos em um subdiretório](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="3e30c-150">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="3e30c-151">Configure a [ `-langversion` opção do compilador](compiler-options/langversion-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3e30c-151">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="3e30c-152">Editar o arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="3e30c-152">Edit the project file</span></span>

<span data-ttu-id="3e30c-153">É possível definir a versão da linguagem em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="3e30c-153">You can set the language version in your project file.</span></span> <span data-ttu-id="3e30c-154">Por exemplo, se você quiser explicitamente acesso às versões prévias dos recursos, adicione um elemento como este:</span><span class="sxs-lookup"><span data-stu-id="3e30c-154">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="3e30c-155">O valor `preview` usa a versão prévia mais recente da linguagem C# compatível com seu compilador.</span><span class="sxs-lookup"><span data-stu-id="3e30c-155">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="3e30c-156">Configurar vários projetos</span><span class="sxs-lookup"><span data-stu-id="3e30c-156">Configure multiple projects</span></span>

<span data-ttu-id="3e30c-157">Para configurar vários projetos, você pode criar um arquivo **Directory. Build. props** que contém o `<LangVersion>` elemento.</span><span class="sxs-lookup"><span data-stu-id="3e30c-157">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="3e30c-158">Normalmente, você faz isso no diretório da solução.</span><span class="sxs-lookup"><span data-stu-id="3e30c-158">You typically do that in your solution directory.</span></span> <span data-ttu-id="3e30c-159">Adicione o seguinte a um arquivo **Directory. Build. props** no diretório da solução:</span><span class="sxs-lookup"><span data-stu-id="3e30c-159">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="3e30c-160">As compilações em todos os subdiretórios do diretório que contém esse arquivo usarão a versão preview C#.</span><span class="sxs-lookup"><span data-stu-id="3e30c-160">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="3e30c-161">Para obter mais informações, confira o artigo sobre como [personalizar o build](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="3e30c-161">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="3e30c-162">Referência à versão da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3e30c-162">C# language version reference</span></span>

<span data-ttu-id="3e30c-163">A tabela a seguir mostra todas as versões atuais da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="3e30c-163">The following table shows all current C# language versions.</span></span> <span data-ttu-id="3e30c-164">Seu compilador pode não entender necessariamente todos os valores se for mais antigo.</span><span class="sxs-lookup"><span data-stu-id="3e30c-164">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="3e30c-165">Se você instalar o .NET Core 3,0 ou posterior, terá acesso a todos os itens listados.</span><span class="sxs-lookup"><span data-stu-id="3e30c-165">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="3e30c-166">Abra o [prompt de comando do desenvolvedor para o Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)e execute o comando a seguir para ver a lista de versões de idioma disponíveis em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3e30c-166">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="3e30c-167">Questionando a opção de compilação [-langversion](compiler-options/langversion-compiler-option.md) como essa, imprimirá algo semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3e30c-167">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
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
