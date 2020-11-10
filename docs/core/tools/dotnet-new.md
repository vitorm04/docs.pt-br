---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
no-loc:
- 'Blazor'
- 'WebAssembly'
ms.date: 09/04/2020
ms.openlocfilehash: 2ee06c37cd950f3b9771db2f30fe353435641d67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400585"
---
# <a name="dotnet-new"></a><span data-ttu-id="2dc64-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2dc64-103">dotnet new</span></span>

<span data-ttu-id="2dc64-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="2dc64-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2dc64-105">Name</span><span class="sxs-lookup"><span data-stu-id="2dc64-105">Name</span></span>

<span data-ttu-id="2dc64-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2dc64-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2dc64-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="2dc64-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2dc64-108">Description</span></span>

<span data-ttu-id="2dc64-109">O `dotnet new` comando cria um projeto do .NET Core ou outros artefatos com base em um modelo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="2dc64-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="2dc64-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="2dc64-111">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="2dc64-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="2dc64-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2dc64-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="2dc64-113">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="2dc64-114">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="2dc64-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="2dc64-115">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="2dc64-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="2dc64-116">Você pode executar `dotnet new --list` ou `dotnet new -l` para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="2dc64-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="2dc64-117">Se o `TEMPLATE` valor não for uma correspondência exata no texto na coluna **modelos** ou **nome curto** da tabela retornada, uma correspondência de subcadeia de caracteres será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="2dc64-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="2dc64-118">A partir do SDK do .NET Core 3,0, a CLI procura modelos em NuGet.org quando você invoca o `dotnet new` comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="2dc64-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="2dc64-119">Se a CLI não encontrar uma correspondência de modelo ao invocar `dotnet new` , nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="2dc64-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="2dc64-120">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="2dc64-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="2dc64-121">Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="2dc64-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2dc64-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="2dc64-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2dc64-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="2dc64-124">Clique no link nome curto para ver as opções de modelo específicas.</span><span class="sxs-lookup"><span data-stu-id="2dc64-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="2dc64-125">Modelos</span><span class="sxs-lookup"><span data-stu-id="2dc64-125">Templates</span></span>                                    | <span data-ttu-id="2dc64-126">Nome curto</span><span class="sxs-lookup"><span data-stu-id="2dc64-126">Short name</span></span>                      | <span data-ttu-id="2dc64-127">Idioma</span><span class="sxs-lookup"><span data-stu-id="2dc64-127">Language</span></span>     | <span data-ttu-id="2dc64-128">Marcações</span><span class="sxs-lookup"><span data-stu-id="2dc64-128">Tags</span></span>                                  | <span data-ttu-id="2dc64-129">Introduzida</span><span class="sxs-lookup"><span data-stu-id="2dc64-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="2dc64-130">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="2dc64-130">Console Application</span></span>                          | [<span data-ttu-id="2dc64-131">MMC</span><span class="sxs-lookup"><span data-stu-id="2dc64-131">console</span></span>](#console)             | <span data-ttu-id="2dc64-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-132">[C#], F#, VB</span></span> | <span data-ttu-id="2dc64-133">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="2dc64-133">Common/Console</span></span>                        | <span data-ttu-id="2dc64-134">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-134">1.0</span></span>        |
| <span data-ttu-id="2dc64-135">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2dc64-135">Class library</span></span>                                | [<span data-ttu-id="2dc64-136">classlib</span><span class="sxs-lookup"><span data-stu-id="2dc64-136">classlib</span></span>](#classlib)           | <span data-ttu-id="2dc64-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-137">[C#], F#, VB</span></span> | <span data-ttu-id="2dc64-138">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="2dc64-138">Common/Library</span></span>                        | <span data-ttu-id="2dc64-139">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-139">1.0</span></span>        |
| <span data-ttu-id="2dc64-140">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-140">WPF Application</span></span>                              | [<span data-ttu-id="2dc64-141">WFP</span><span class="sxs-lookup"><span data-stu-id="2dc64-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="2dc64-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-142">[C#], VB</span></span>     | <span data-ttu-id="2dc64-143">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-143">Common/WPF</span></span>                            | <span data-ttu-id="2dc64-144">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="2dc64-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="2dc64-145">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-145">WPF Class library</span></span>                            | [<span data-ttu-id="2dc64-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="2dc64-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="2dc64-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-147">[C#], VB</span></span>     | <span data-ttu-id="2dc64-148">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-148">Common/WPF</span></span>                            | <span data-ttu-id="2dc64-149">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="2dc64-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="2dc64-150">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="2dc64-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="2dc64-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="2dc64-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-152">[C#], VB</span></span>     | <span data-ttu-id="2dc64-153">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-153">Common/WPF</span></span>                            | <span data-ttu-id="2dc64-154">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="2dc64-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="2dc64-155">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="2dc64-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="2dc64-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="2dc64-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-157">[C#], VB</span></span>     | <span data-ttu-id="2dc64-158">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2dc64-158">Common/WPF</span></span>                            | <span data-ttu-id="2dc64-159">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="2dc64-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="2dc64-160">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="2dc64-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="2dc64-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="2dc64-161">winforms</span></span>](#winforms)           | <span data-ttu-id="2dc64-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-162">[C#], VB</span></span>     | <span data-ttu-id="2dc64-163">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="2dc64-163">Common/WinForms</span></span>                       | <span data-ttu-id="2dc64-164">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="2dc64-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="2dc64-165">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="2dc64-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="2dc64-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="2dc64-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="2dc64-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-167">[C#], VB</span></span>     | <span data-ttu-id="2dc64-168">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="2dc64-168">Common/WinForms</span></span>                       | <span data-ttu-id="2dc64-169">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="2dc64-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="2dc64-170">Serviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="2dc64-170">Worker Service</span></span>                               | [<span data-ttu-id="2dc64-171">funcionários</span><span class="sxs-lookup"><span data-stu-id="2dc64-171">worker</span></span>](#web-others)           | <span data-ttu-id="2dc64-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-172">[C#]</span></span>         | <span data-ttu-id="2dc64-173">Comum/de trabalho/Web</span><span class="sxs-lookup"><span data-stu-id="2dc64-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="2dc64-174">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-174">3.0</span></span>        |
| <span data-ttu-id="2dc64-175">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="2dc64-175">Unit Test Project</span></span>                            | [<span data-ttu-id="2dc64-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="2dc64-176">mstest</span></span>](#test)                 | <span data-ttu-id="2dc64-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-177">[C#], F#, VB</span></span> | <span data-ttu-id="2dc64-178">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="2dc64-178">Test/MSTest</span></span>                           | <span data-ttu-id="2dc64-179">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-179">1.0</span></span>        |
| <span data-ttu-id="2dc64-180">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="2dc64-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="2dc64-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="2dc64-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-182">[C#], F#, VB</span></span> | <span data-ttu-id="2dc64-183">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-183">Test/NUnit</span></span>                            | <span data-ttu-id="2dc64-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="2dc64-184">2.1.400</span></span>    |
| <span data-ttu-id="2dc64-185">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="2dc64-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="2dc64-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-186">[C#], F#, VB</span></span> | <span data-ttu-id="2dc64-187">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-187">Test/NUnit</span></span>                            | <span data-ttu-id="2dc64-188">2.2</span><span class="sxs-lookup"><span data-stu-id="2dc64-188">2.2</span></span>        |
| <span data-ttu-id="2dc64-189">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="2dc64-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-190">xunit</span></span>](#test)                  | <span data-ttu-id="2dc64-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2dc64-191">[C#], F#, VB</span></span> | <span data-ttu-id="2dc64-192">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-192">Test/xUnit</span></span>                            | <span data-ttu-id="2dc64-193">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-193">1.0</span></span>        |
| <span data-ttu-id="2dc64-194">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="2dc64-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="2dc64-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-195">[C#]</span></span>         | <span data-ttu-id="2dc64-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2dc64-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="2dc64-197">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-197">3.0</span></span>        |
| <span data-ttu-id="2dc64-198">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="2dc64-198">Razor Page</span></span>                                   | [<span data-ttu-id="2dc64-199">page</span><span class="sxs-lookup"><span data-stu-id="2dc64-199">page</span></span>](#page)                   | <span data-ttu-id="2dc64-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-200">[C#]</span></span>         | <span data-ttu-id="2dc64-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2dc64-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="2dc64-202">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-202">2.0</span></span>        |
| <span data-ttu-id="2dc64-203">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="2dc64-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="2dc64-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="2dc64-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="2dc64-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-205">[C#]</span></span>         | <span data-ttu-id="2dc64-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2dc64-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="2dc64-207">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-207">2.0</span></span>        |
| <span data-ttu-id="2dc64-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="2dc64-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="2dc64-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-209">[C#]</span></span>         | <span data-ttu-id="2dc64-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2dc64-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="2dc64-211">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-211">2.0</span></span>        |
| <span data-ttu-id="2dc64-212">Blazor Aplicativo de servidor</span><span class="sxs-lookup"><span data-stu-id="2dc64-212">Blazor Server App</span></span>                            | [<span data-ttu-id="2dc64-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="2dc64-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="2dc64-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-214">[C#]</span></span>         | <span data-ttu-id="2dc64-215">SiteBlazor</span><span class="sxs-lookup"><span data-stu-id="2dc64-215">Web/Blazor</span></span>                            | <span data-ttu-id="2dc64-216">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-216">3.0</span></span>        |
| <span data-ttu-id="2dc64-217">BlazorDo WebAssembly aplicativo</span><span class="sxs-lookup"><span data-stu-id="2dc64-217">Blazor WebAssembly App</span></span>                       | [<span data-ttu-id="2dc64-218">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="2dc64-218">blazorwasm</span></span>](#blazorwasm)       | <span data-ttu-id="2dc64-219">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-219">[C#]</span></span>         | <span data-ttu-id="2dc64-220">SiteBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="2dc64-220">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="2dc64-221">3.1.300</span><span class="sxs-lookup"><span data-stu-id="2dc64-221">3.1.300</span></span>    |
| <span data-ttu-id="2dc64-222">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="2dc64-222">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="2dc64-223">site</span><span class="sxs-lookup"><span data-stu-id="2dc64-223">web</span></span>](#web)                     | <span data-ttu-id="2dc64-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2dc64-224">[C#], F#</span></span>     | <span data-ttu-id="2dc64-225">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="2dc64-225">Web/Empty</span></span>                             | <span data-ttu-id="2dc64-226">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-226">1.0</span></span>        |
| <span data-ttu-id="2dc64-227">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="2dc64-227">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="2dc64-228">MVC</span><span class="sxs-lookup"><span data-stu-id="2dc64-228">mvc</span></span>](#web-options)             | <span data-ttu-id="2dc64-229">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2dc64-229">[C#], F#</span></span>     | <span data-ttu-id="2dc64-230">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="2dc64-230">Web/MVC</span></span>                               | <span data-ttu-id="2dc64-231">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-231">1.0</span></span>        |
| <span data-ttu-id="2dc64-232">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2dc64-232">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="2dc64-233">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="2dc64-233">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="2dc64-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-234">[C#]</span></span>         | <span data-ttu-id="2dc64-235">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="2dc64-235">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="2dc64-236">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="2dc64-236">2.2, 2.0</span></span>   |
| <span data-ttu-id="2dc64-237">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="2dc64-237">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="2dc64-238">angular</span><span class="sxs-lookup"><span data-stu-id="2dc64-238">angular</span></span>](#spa)                 | <span data-ttu-id="2dc64-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-239">[C#]</span></span>         | <span data-ttu-id="2dc64-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2dc64-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="2dc64-241">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-241">2.0</span></span>        |
| <span data-ttu-id="2dc64-242">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="2dc64-242">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="2dc64-243">reagir</span><span class="sxs-lookup"><span data-stu-id="2dc64-243">react</span></span>](#spa)                   | <span data-ttu-id="2dc64-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-244">[C#]</span></span>         | <span data-ttu-id="2dc64-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2dc64-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="2dc64-246">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-246">2.0</span></span>        |
| <span data-ttu-id="2dc64-247">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="2dc64-247">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="2dc64-248">reactredux</span><span class="sxs-lookup"><span data-stu-id="2dc64-248">reactredux</span></span>](#reactredux)       | <span data-ttu-id="2dc64-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-249">[C#]</span></span>         | <span data-ttu-id="2dc64-250">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2dc64-250">Web/MVC/SPA</span></span>                           | <span data-ttu-id="2dc64-251">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-251">2.0</span></span>        |
| <span data-ttu-id="2dc64-252">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2dc64-252">Razor Class Library</span></span>                          | [<span data-ttu-id="2dc64-253">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="2dc64-253">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="2dc64-254">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-254">[C#]</span></span>         | <span data-ttu-id="2dc64-255">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2dc64-255">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="2dc64-256">2.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-256">2.1</span></span>        |
| <span data-ttu-id="2dc64-257">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2dc64-257">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="2dc64-258">webAPI</span><span class="sxs-lookup"><span data-stu-id="2dc64-258">webapi</span></span>](#webapi)               | <span data-ttu-id="2dc64-259">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2dc64-259">[C#], F#</span></span>     | <span data-ttu-id="2dc64-260">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="2dc64-260">Web/WebAPI</span></span>                            | <span data-ttu-id="2dc64-261">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-261">1.0</span></span>        |
| <span data-ttu-id="2dc64-262">ASP.NET Core serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="2dc64-262">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="2dc64-263">grpc</span><span class="sxs-lookup"><span data-stu-id="2dc64-263">grpc</span></span>](#web-others)             | <span data-ttu-id="2dc64-264">[C#]</span><span class="sxs-lookup"><span data-stu-id="2dc64-264">[C#]</span></span>         | <span data-ttu-id="2dc64-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="2dc64-265">Web/gRPC</span></span>                              | <span data-ttu-id="2dc64-266">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-266">3.0</span></span>        |
| <span data-ttu-id="2dc64-267">arquivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="2dc64-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="2dc64-268">Config</span><span class="sxs-lookup"><span data-stu-id="2dc64-268">Config</span></span>                                | <span data-ttu-id="2dc64-269">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-269">3.0</span></span>        |
| <span data-ttu-id="2dc64-270">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="2dc64-270">global.json file</span></span>                             | [<span data-ttu-id="2dc64-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="2dc64-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="2dc64-272">Config</span><span class="sxs-lookup"><span data-stu-id="2dc64-272">Config</span></span>                                | <span data-ttu-id="2dc64-273">2.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-273">2.0</span></span>        |
| <span data-ttu-id="2dc64-274">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="2dc64-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="2dc64-275">Config</span><span class="sxs-lookup"><span data-stu-id="2dc64-275">Config</span></span>                                | <span data-ttu-id="2dc64-276">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-276">1.0</span></span>        |
| <span data-ttu-id="2dc64-277">Arquivo de manifesto da ferramenta local dotnet</span><span class="sxs-lookup"><span data-stu-id="2dc64-277">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="2dc64-278">Config</span><span class="sxs-lookup"><span data-stu-id="2dc64-278">Config</span></span>                                | <span data-ttu-id="2dc64-279">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-279">3.0</span></span>        |
| <span data-ttu-id="2dc64-280">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="2dc64-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="2dc64-281">Config</span><span class="sxs-lookup"><span data-stu-id="2dc64-281">Config</span></span>                                | <span data-ttu-id="2dc64-282">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-282">1.0</span></span>        |
| <span data-ttu-id="2dc64-283">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="2dc64-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="2dc64-284">Solução</span><span class="sxs-lookup"><span data-stu-id="2dc64-284">Solution</span></span>                              | <span data-ttu-id="2dc64-285">1.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-285">1.0</span></span>        |
| <span data-ttu-id="2dc64-286">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="2dc64-286">Protocol Buffer File</span></span>                         | [<span data-ttu-id="2dc64-287">proto</span><span class="sxs-lookup"><span data-stu-id="2dc64-287">proto</span></span>](#namespace)             |              | <span data-ttu-id="2dc64-288">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="2dc64-288">Web/gRPC</span></span>                              | <span data-ttu-id="2dc64-289">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-289">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="2dc64-290">Opções</span><span class="sxs-lookup"><span data-stu-id="2dc64-290">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="2dc64-291">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-291">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="2dc64-292">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-292">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="2dc64-293">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="2dc64-293">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="2dc64-294">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="2dc64-294">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2dc64-295">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="2dc64-295">Prints out help for the command.</span></span> <span data-ttu-id="2dc64-296">Ele pode ser invocado para o `dotnet new` próprio comando ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-296">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="2dc64-297">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-297">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="2dc64-298">Instala um pacote de modelos do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2dc64-298">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2dc64-299">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-299">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="2dc64-300">Por padrão, `dotnet new` \* o passa para a versão, que representa a versão de pacote estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="2dc64-300">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="2dc64-301">Veja um exemplo na seção [exemplos](#examples) .</span><span class="sxs-lookup"><span data-stu-id="2dc64-301">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="2dc64-302">Se uma versão do modelo já tiver sido instalada quando você executar esse comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-302">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="2dc64-303">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="2dc64-303">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="2dc64-304">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-304">Lists templates containing the specified name.</span></span> <span data-ttu-id="2dc64-305">Se nenhum nome for especificado, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="2dc64-305">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="2dc64-306">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-306">The language of the template to create.</span></span> <span data-ttu-id="2dc64-307">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="2dc64-307">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2dc64-308">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="2dc64-308">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2dc64-309">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="2dc64-309">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="2dc64-310">Nesses casos, coloque o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="2dc64-310">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="2dc64-311">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-311">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="2dc64-312">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-312">The name for the created output.</span></span> <span data-ttu-id="2dc64-313">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-313">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="2dc64-314">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="2dc64-314">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="2dc64-315">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="2dc64-315">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="2dc64-316">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-316">Location to place the generated output.</span></span> <span data-ttu-id="2dc64-317">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2dc64-317">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="2dc64-318">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2dc64-318">Filters templates based on available types.</span></span> <span data-ttu-id="2dc64-319">Os valores predefinidos são `project` e `item` .</span><span class="sxs-lookup"><span data-stu-id="2dc64-319">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="2dc64-320">Desinstala um pacote de modelos no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2dc64-320">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2dc64-321">Quando o `<PATH|NUGET_ID>` valor não for especificado, todos os pacotes de modelos instalados atualmente e seus modelos associados serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="2dc64-321">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="2dc64-322">Ao especificar `NUGET_ID` , não inclua o número de versão.</span><span class="sxs-lookup"><span data-stu-id="2dc64-322">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="2dc64-323">Se você não especificar um parâmetro para essa opção, o comando listará os modelos instalados e os detalhes sobre eles.</span><span class="sxs-lookup"><span data-stu-id="2dc64-323">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2dc64-324">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="2dc64-324">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="2dc64-325">Por exemplo, *C:/Users/ \<USER> /Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que a contém não irá.</span><span class="sxs-lookup"><span data-stu-id="2dc64-325">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="2dc64-326">Não inclua uma barra de diretório final de encerramento no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-326">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="2dc64-327">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="2dc64-327">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="2dc64-328">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-328">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="2dc64-329">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="2dc64-329">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="2dc64-330">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-330">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="2dc64-331">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="2dc64-331">Template options</span></span>

<span data-ttu-id="2dc64-332">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2dc64-332">Each project template may have additional options available.</span></span> <span data-ttu-id="2dc64-333">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="2dc64-333">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="2dc64-334">console</span><span class="sxs-lookup"><span data-stu-id="2dc64-334">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2dc64-335">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-335">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-336">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-336">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="2dc64-337">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-337">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-338">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-338">SDK version</span></span> | <span data-ttu-id="2dc64-339">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-339">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-340">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-340">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-341">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-341">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2dc64-342">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-342">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2dc64-343">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2dc64-343">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="2dc64-344">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="2dc64-344">Not supported for F#.</span></span> <span data-ttu-id="2dc64-345">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-345">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2dc64-346">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2dc64-346">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-347">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-347">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="2dc64-348">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-348">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="2dc64-349">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-349">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="2dc64-350">classlib</span><span class="sxs-lookup"><span data-stu-id="2dc64-350">classlib</span></span>

- <span data-ttu-id="2dc64-351">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-351">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="2dc64-352">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-352">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-353">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2dc64-353">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="2dc64-354">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-354">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2dc64-355">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-355">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2dc64-356">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2dc64-356">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="2dc64-357">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="2dc64-357">Not supported for F#.</span></span> <span data-ttu-id="2dc64-358">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-358">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2dc64-359">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2dc64-359">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-360">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-360">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-361">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-361">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="2dc64-362">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="2dc64-362">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="2dc64-363">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-363">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="2dc64-364">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-364">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-365">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-365">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="2dc64-366">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2dc64-366">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2dc64-367">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2dc64-368">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2dc64-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="2dc64-369">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2dc64-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-370">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-370">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-371">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-371">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="2dc64-372">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="2dc64-372">winforms, winformslib</span></span>

- <span data-ttu-id="2dc64-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-373">_ *`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="2dc64-374">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-374">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2dc64-375">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2dc64-375">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="2dc64-376">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2dc64-376">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-377">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-377">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-378">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-378">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="2dc64-379">trabalho, grpc</span><span class="sxs-lookup"><span data-stu-id="2dc64-379">worker, grpc</span></span>

- <span data-ttu-id="2dc64-380">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-380">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="2dc64-381">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-381">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-382">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-382">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="2dc64-383">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2dc64-383">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2dc64-384">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-384">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-385">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-385">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-386">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-386">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="2dc64-387">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-387">mstest, xunit</span></span>

- <span data-ttu-id="2dc64-388">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-388">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="2dc64-389">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-389">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-390">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-390">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="2dc64-391">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-391">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-392">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-392">SDK version</span></span> | <span data-ttu-id="2dc64-393">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-393">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-394">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-394">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-395">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-395">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="2dc64-396">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2dc64-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-397">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-397">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-398">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-398">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="2dc64-399">NUnit</span><span class="sxs-lookup"><span data-stu-id="2dc64-399">nunit</span></span>

- <span data-ttu-id="2dc64-400">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-400">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="2dc64-401">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-401">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="2dc64-402">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-402">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-403">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-403">SDK version</span></span> | <span data-ttu-id="2dc64-404">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-404">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-405">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-405">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-406">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-406">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2dc64-407">2.2</span><span class="sxs-lookup"><span data-stu-id="2dc64-407">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="2dc64-408">2.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-408">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="2dc64-409">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2dc64-409">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-410">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-410">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-411">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-411">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="2dc64-412">página</span><span class="sxs-lookup"><span data-stu-id="2dc64-412">page</span></span>

- <span data-ttu-id="2dc64-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-413">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="2dc64-414">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-414">Namespace for the generated code.</span></span> <span data-ttu-id="2dc64-415">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-415">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="2dc64-416">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="2dc64-416">Creates the page without a PageModel.</span></span>

<span data-ttu-id="2dc64-417">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-417">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="2dc64-418">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="2dc64-418">viewimports, proto</span></span>

- <span data-ttu-id="2dc64-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-419">_ *`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="2dc64-420">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-420">Namespace for the generated code.</span></span> <span data-ttu-id="2dc64-421">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-421">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="2dc64-422">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-422">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="2dc64-423">blazorserver</span><span class="sxs-lookup"><span data-stu-id="2dc64-423">blazorserver</span></span>

- <span data-ttu-id="2dc64-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-424">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="2dc64-425">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-425">The type of authentication to use.</span></span> <span data-ttu-id="2dc64-426">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2dc64-426">The possible values are:</span></span>

  - <span data-ttu-id="2dc64-427">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2dc64-427">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2dc64-428">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2dc64-428">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="2dc64-429">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2dc64-429">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2dc64-430">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2dc64-430">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="2dc64-431">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2dc64-431">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="2dc64-432">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2dc64-432">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-433">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-433">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2dc64-434">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-434">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-435">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-435">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2dc64-436">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-436">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2dc64-437">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-437">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="2dc64-438">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-438">The reset password policy ID for this project.</span></span> <span data-ttu-id="2dc64-439">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-439">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="2dc64-440">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-440">The edit profile policy ID for this project.</span></span> <span data-ttu-id="2dc64-441">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-441">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-442">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-442">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2dc64-443">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-443">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2dc64-444">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-444">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2dc64-445">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-445">The Client ID for this project.</span></span> <span data-ttu-id="2dc64-446">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-446">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2dc64-447">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-447">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2dc64-448">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-448">The domain for the directory tenant.</span></span> <span data-ttu-id="2dc64-449">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-449">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-450">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-450">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2dc64-451">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-451">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2dc64-452">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-452">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-453">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-453">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="2dc64-454">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2dc64-454">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2dc64-455">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-455">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-456">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-456">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2dc64-457">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-457">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2dc64-458">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-458">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2dc64-459">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-459">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-460">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-460">Turns off HTTPS.</span></span> <span data-ttu-id="2dc64-461">Essa opção só se aplica se `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` não estiverem sendo usados para `--auth` .</span><span class="sxs-lookup"><span data-stu-id="2dc64-461">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2dc64-462">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2dc64-462">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2dc64-463">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-463">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-464">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-464">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-465">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-465">\*\*_</span></span>

### <a name="blazorwasm"></a><span data-ttu-id="2dc64-466">blazorwasm</span><span class="sxs-lookup"><span data-stu-id="2dc64-466">blazorwasm</span></span>

- <span data-ttu-id="2dc64-467">_ *`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-467">_ *`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="2dc64-468">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="2dc64-469">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-469">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-470">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-470">SDK version</span></span> | <span data-ttu-id="2dc64-471">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-471">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-472">5.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-472">5.0</span></span>         | `net5.0`        |
  | <span data-ttu-id="2dc64-473">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-473">3.1</span></span>         | `netcoreapp3.1` |

- **`--no-restore`**

  <span data-ttu-id="2dc64-474">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-474">Doesn't execute an implicit restore during project creation.</span></span>

- **`-ho|--hosted`**

  <span data-ttu-id="2dc64-475">Inclui um host ASP.NET Core para o Blazor WebAssembly aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-475">Includes an ASP.NET Core host for the Blazor WebAssembly app.</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="2dc64-476">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-476">The type of authentication to use.</span></span> <span data-ttu-id="2dc64-477">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2dc64-477">The possible values are:</span></span>

  - <span data-ttu-id="2dc64-478">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2dc64-478">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2dc64-479">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2dc64-479">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="2dc64-480">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2dc64-480">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2dc64-481">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2dc64-481">`SingleOrg` - Organizational authentication for a single tenant.</span></span>

- **`--authority <AUTHORITY>`**

  <span data-ttu-id="2dc64-482">A autoridade do provedor de OIDC.</span><span class="sxs-lookup"><span data-stu-id="2dc64-482">The authority of the OIDC provider.</span></span> <span data-ttu-id="2dc64-483">Use com a autenticação do `Individual`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-483">Use with `Individual` authentication.</span></span> <span data-ttu-id="2dc64-484">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-484">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-485">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-485">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2dc64-486">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-486">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-487">O valor padrão é `https://aadB2CInstance.b2clogin.com/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-487">The default value is `https://aadB2CInstance.b2clogin.com/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2dc64-488">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-488">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2dc64-489">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-489">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-490">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-490">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2dc64-491">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-491">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-492">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-492">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2dc64-493">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-493">The Client ID for this project.</span></span> <span data-ttu-id="2dc64-494">Use o com o `IndividualB2C` , o `SingleOrg` ou a `Individual` autenticação em cenários autônomos.</span><span class="sxs-lookup"><span data-stu-id="2dc64-494">Use with `IndividualB2C`, `SingleOrg`, or `Individual` authentication in standalone scenarios.</span></span> <span data-ttu-id="2dc64-495">O valor padrão é `33333333-3333-3333-33333333333333333`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-495">The default value is `33333333-3333-3333-33333333333333333`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2dc64-496">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-496">The domain for the directory tenant.</span></span> <span data-ttu-id="2dc64-497">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-497">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-498">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-498">The default value is `qualified.domain.name`.</span></span>

- **`--app-id-uri <URI>`**

  <span data-ttu-id="2dc64-499">O URI da ID do aplicativo para a API do servidor que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-499">The App ID Uri for the server API you want to call.</span></span> <span data-ttu-id="2dc64-500">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-500">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-501">O valor padrão é `api.id.uri`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-501">The default value is `api.id.uri`.</span></span>

- **`--api-client-id <ID>`**

  <span data-ttu-id="2dc64-502">A ID do cliente para a API que o servidor hospeda.</span><span class="sxs-lookup"><span data-stu-id="2dc64-502">The Client ID for the API that the server hosts.</span></span> <span data-ttu-id="2dc64-503">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-503">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-504">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-504">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`-s|--default-scope <SCOPE>`**

  <span data-ttu-id="2dc64-505">O escopo da API que o cliente precisa solicitar para provisionar um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="2dc64-505">The API scope the client needs to request to provision an access token.</span></span> <span data-ttu-id="2dc64-506">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-506">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-507">O valor padrão é `user_impersonation`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-507">The default value is `user_impersonation`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2dc64-508">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-508">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2dc64-509">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-509">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-510">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-510">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2dc64-511">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-511">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2dc64-512">Aplica-se somente à `SingleOrg` autenticação.</span><span class="sxs-lookup"><span data-stu-id="2dc64-512">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2dc64-513">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-p|--pwa`**

  <span data-ttu-id="2dc64-514">produz um aplicativo Web progressivo (PWA) que dá suporte à instalação e ao uso offline.</span><span class="sxs-lookup"><span data-stu-id="2dc64-514">produces a Progressive Web Application (PWA) supporting installation and offline use.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-515">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-515">Turns off HTTPS.</span></span> <span data-ttu-id="2dc64-516">Essa opção se aplica somente se `Individual` , `IndividualB2C` ou `SingleOrg` não estiverem sendo usados para `--auth` .</span><span class="sxs-lookup"><span data-stu-id="2dc64-516">This option only applies if `Individual`, `IndividualB2C`, or `SingleOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2dc64-517">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2dc64-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2dc64-518">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--called-api-url <URL>`**

  <span data-ttu-id="2dc64-519">URL da API a ser chamada do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="2dc64-519">URL of the API to call from the web app.</span></span> <span data-ttu-id="2dc64-520">Aplica-se somente ao `SingleOrg` ou à `IndividualB2C` autenticação sem um host ASP.NET Core especificado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-520">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="2dc64-521">O valor padrão é `https://graph.microsoft.com/v1.0/me`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-521">The default value is `https://graph.microsoft.com/v1.0/me`.</span></span>

- **`--calls-graph`**

  <span data-ttu-id="2dc64-522">Especifica se o aplicativo Web chama Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="2dc64-522">Specifies if the web app calls Microsoft Graph.</span></span> <span data-ttu-id="2dc64-523">Aplica-se somente à `SingleOrg` autenticação.</span><span class="sxs-lookup"><span data-stu-id="2dc64-523">Only applies to `SingleOrg` authentication.</span></span>

- **`--called-api-scopes <SCOPES>`**

  <span data-ttu-id="2dc64-524">Escopos a serem solicitados a chamar a API do aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="2dc64-524">Scopes to request to call the API from the web app.</span></span> <span data-ttu-id="2dc64-525">Aplica-se somente ao `SingleOrg` ou à `IndividualB2C` autenticação sem um host ASP.NET Core especificado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-525">Only applies to `SingleOrg` or `IndividualB2C` authentication without an ASP.NET Core host specified.</span></span> <span data-ttu-id="2dc64-526">O padrão é `user.read`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-526">The default is `user.read`.</span></span>

<span data-ttu-id="2dc64-527">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-527">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="2dc64-528">web</span><span class="sxs-lookup"><span data-stu-id="2dc64-528">web</span></span>

- <span data-ttu-id="2dc64-529">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-529">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="2dc64-530">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2dc64-531">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-532">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2dc64-533">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-534">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-534">SDK version</span></span> | <span data-ttu-id="2dc64-535">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-536">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-537">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2dc64-538">2.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-538">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="2dc64-539">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-540">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-540">Turns off HTTPS.</span></span>

<span data-ttu-id="2dc64-541">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-541">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="2dc64-542">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="2dc64-542">mvc, webapp</span></span>

- <span data-ttu-id="2dc64-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-543">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="2dc64-544">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-544">The type of authentication to use.</span></span> <span data-ttu-id="2dc64-545">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2dc64-545">The possible values are:</span></span>

  - <span data-ttu-id="2dc64-546">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2dc64-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2dc64-547">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2dc64-547">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="2dc64-548">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2dc64-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2dc64-549">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2dc64-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="2dc64-550">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2dc64-550">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="2dc64-551">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2dc64-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-552">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2dc64-553">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-554">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2dc64-555">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2dc64-556">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-556">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="2dc64-557">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-557">The reset password policy ID for this project.</span></span> <span data-ttu-id="2dc64-558">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-558">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="2dc64-559">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-559">The edit profile policy ID for this project.</span></span> <span data-ttu-id="2dc64-560">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-560">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-561">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-561">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2dc64-562">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-562">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2dc64-563">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-563">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2dc64-564">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-564">The Client ID for this project.</span></span> <span data-ttu-id="2dc64-565">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-565">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2dc64-566">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-566">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2dc64-567">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-567">The domain for the directory tenant.</span></span> <span data-ttu-id="2dc64-568">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-568">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-569">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-569">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2dc64-570">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-570">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2dc64-571">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-571">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-572">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-572">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="2dc64-573">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2dc64-573">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2dc64-574">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-574">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-575">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-575">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2dc64-576">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-576">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2dc64-577">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-577">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2dc64-578">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-578">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-579">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-579">Turns off HTTPS.</span></span> <span data-ttu-id="2dc64-580">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="2dc64-580">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2dc64-581">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2dc64-581">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2dc64-582">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-582">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2dc64-583">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-583">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-584">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-584">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="2dc64-585">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-585">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-586">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-586">SDK version</span></span> | <span data-ttu-id="2dc64-587">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-587">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-588">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-588">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-589">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-589">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="2dc64-590">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-590">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="2dc64-591">Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-591">Includes BrowserLink in the project.</span></span> <span data-ttu-id="2dc64-592">Opção não disponível no SDK do .NET Core 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="2dc64-592">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="2dc64-593">Determina se o projeto está configurado para usar a [compilação de tempo de execução do Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações de depuração.</span><span class="sxs-lookup"><span data-stu-id="2dc64-593">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="2dc64-594">Opção disponível desde o SDK do 3.1.201 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2dc64-594">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="2dc64-595">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-595">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="2dc64-596">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="2dc64-596">angular, react</span></span>

- <span data-ttu-id="2dc64-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-597">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="2dc64-598">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-598">The type of authentication to use.</span></span> <span data-ttu-id="2dc64-599">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-599">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="2dc64-600">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2dc64-600">The possible values are:</span></span>

  - <span data-ttu-id="2dc64-601">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2dc64-601">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2dc64-602">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2dc64-602">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2dc64-603">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2dc64-604">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-604">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-605">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-605">Turns off HTTPS.</span></span> <span data-ttu-id="2dc64-606">Essa opção se aplica somente se a autenticação for `None` .</span><span class="sxs-lookup"><span data-stu-id="2dc64-606">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2dc64-607">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2dc64-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2dc64-608">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-608">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-609">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-609">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2dc64-610">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-610">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-611">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-611">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2dc64-612">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-612">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-613">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-613">SDK version</span></span> | <span data-ttu-id="2dc64-614">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-614">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-615">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-615">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-616">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-616">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2dc64-617">2.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-617">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="2dc64-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-618">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="2dc64-619">reactredux</span><span class="sxs-lookup"><span data-stu-id="2dc64-619">reactredux</span></span>

- <span data-ttu-id="2dc64-620">_ *`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-620">_ *`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="2dc64-621">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-621">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2dc64-622">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-622">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-623">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-623">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2dc64-624">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-624">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-625">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-625">SDK version</span></span> | <span data-ttu-id="2dc64-626">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-626">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-627">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-627">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-628">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-628">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2dc64-629">2.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-629">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="2dc64-630">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-630">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-631">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-631">Turns off HTTPS.</span></span>

<span data-ttu-id="2dc64-632">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-632">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="2dc64-633">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="2dc64-633">razorclasslib</span></span>

- <span data-ttu-id="2dc64-634">_ *`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-634">_ *`--no-restore`*\*</span></span>

  <span data-ttu-id="2dc64-635">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-635">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="2dc64-636">Dá suporte à adição de páginas e exibições do Razor tradicionais, além dos componentes dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2dc64-636">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="2dc64-637">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2dc64-637">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="2dc64-638">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-638">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="2dc64-639">webapi</span><span class="sxs-lookup"><span data-stu-id="2dc64-639">webapi</span></span>

- <span data-ttu-id="2dc64-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-640">_ *`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="2dc64-641">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-641">The type of authentication to use.</span></span> <span data-ttu-id="2dc64-642">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2dc64-642">The possible values are:</span></span>

  - <span data-ttu-id="2dc64-643">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2dc64-643">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2dc64-644">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2dc64-644">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2dc64-645">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2dc64-645">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="2dc64-646">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2dc64-646">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-647">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-647">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2dc64-648">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-648">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2dc64-649">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-649">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2dc64-650">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-650">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2dc64-651">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-651">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2dc64-652">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-652">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2dc64-653">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-653">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-654">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-654">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2dc64-655">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-655">The Client ID for this project.</span></span> <span data-ttu-id="2dc64-656">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-656">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-657">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-657">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2dc64-658">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-658">The domain for the directory tenant.</span></span> <span data-ttu-id="2dc64-659">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-659">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-660">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-660">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2dc64-661">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2dc64-661">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2dc64-662">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-662">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2dc64-663">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-663">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2dc64-664">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2dc64-664">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2dc64-665">Aplica-se somente à `SingleOrg` autenticação.</span><span class="sxs-lookup"><span data-stu-id="2dc64-665">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2dc64-666">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2dc64-666">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="2dc64-667">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2dc64-667">Turns off HTTPS.</span></span> <span data-ttu-id="2dc64-668">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="2dc64-668">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="2dc64-669">Essa opção só se aplica se `IndividualB2C` ou `SingleOrg` não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="2dc64-669">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2dc64-670">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2dc64-670">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2dc64-671">Aplica-se somente à `IndividualB2C` autenticação.</span><span class="sxs-lookup"><span data-stu-id="2dc64-671">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2dc64-672">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2dc64-672">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2dc64-673">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2dc64-673">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2dc64-674">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2dc64-674">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2dc64-675">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2dc64-675">SDK version</span></span> | <span data-ttu-id="2dc64-676">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2dc64-676">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2dc64-677">3.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-677">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2dc64-678">3.0</span><span class="sxs-lookup"><span data-stu-id="2dc64-678">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2dc64-679">2.1</span><span class="sxs-lookup"><span data-stu-id="2dc64-679">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="2dc64-680">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2dc64-680">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="2dc64-681">\*\*_</span><span class="sxs-lookup"><span data-stu-id="2dc64-681">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="2dc64-682">globaljson</span><span class="sxs-lookup"><span data-stu-id="2dc64-682">globaljson</span></span>

- <span data-ttu-id="2dc64-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="2dc64-683">_ *`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="2dc64-684">Especifica a versão do SDK do .NET Core a ser usada na *global.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="2dc64-684">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="2dc64-685">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2dc64-685">Examples</span></span>

- <span data-ttu-id="2dc64-686">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="2dc64-686">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="2dc64-687">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="2dc64-687">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="2dc64-688">Crie um projeto de biblioteca de classe .NET Standard no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="2dc64-688">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="2dc64-689">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="2dc64-689">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="2dc64-690">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="2dc64-690">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="2dc64-691">Listar todos os modelos disponíveis para modelos de aplicativo de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="2dc64-691">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="2dc64-692">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="2dc64-692">List all templates matching the *we* substring.</span></span> <span data-ttu-id="2dc64-693">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="2dc64-693">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="2dc64-694">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="2dc64-694">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="2dc64-695">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="2dc64-695">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="2dc64-696">Instale a versão 2,0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="2dc64-696">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="2dc64-697">Liste os modelos instalados e os detalhes sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="2dc64-697">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="2dc64-698">Crie um *global.jsno* diretório atual definindo a versão do SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="2dc64-698">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="2dc64-699">Confira também</span><span class="sxs-lookup"><span data-stu-id="2dc64-699">See also</span></span>

- [<span data-ttu-id="2dc64-700">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="2dc64-700">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="2dc64-701">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="2dc64-701">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="2dc64-702">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="2dc64-702">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="2dc64-703">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="2dc64-703">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
