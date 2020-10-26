---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/01/2020
ms.openlocfilehash: 4a4c8e2806fee663b5f6aa255a6f24250a072a85
ms.sourcegitcommit: 532b03d5bbab764d63356193b04cd2281bc01239
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2020
ms.locfileid: "92526617"
---
# <a name="dotnet-new"></a><span data-ttu-id="695d1-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="695d1-103">dotnet new</span></span>

<span data-ttu-id="695d1-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="695d1-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="695d1-105">Nome</span><span class="sxs-lookup"><span data-stu-id="695d1-105">Name</span></span>

<span data-ttu-id="695d1-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="695d1-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="695d1-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="695d1-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="695d1-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="695d1-108">Description</span></span>

<span data-ttu-id="695d1-109">O `dotnet new` comando cria um projeto do .NET Core ou outros artefatos com base em um modelo.</span><span class="sxs-lookup"><span data-stu-id="695d1-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="695d1-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="695d1-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="695d1-111">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="695d1-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="695d1-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="695d1-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="695d1-113">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="695d1-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="695d1-114">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="695d1-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="695d1-115">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="695d1-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="695d1-116">Você pode executar `dotnet new --list` ou `dotnet new -l` para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="695d1-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="695d1-117">Se o `TEMPLATE` valor não for uma correspondência exata no texto na coluna **modelos** ou **nome curto** da tabela retornada, uma correspondência de subcadeia de caracteres será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="695d1-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="695d1-118">A partir do SDK do .NET Core 3,0, a CLI procura modelos em NuGet.org quando você invoca o `dotnet new` comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="695d1-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="695d1-119">Se a CLI não encontrar uma correspondência de modelo ao invocar `dotnet new` , nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="695d1-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="695d1-120">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="695d1-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="695d1-121">Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="695d1-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="695d1-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="695d1-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="695d1-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="695d1-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="695d1-124">Clique no link nome curto para ver as opções de modelo específicas.</span><span class="sxs-lookup"><span data-stu-id="695d1-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="695d1-125">Modelos</span><span class="sxs-lookup"><span data-stu-id="695d1-125">Templates</span></span>                                    | <span data-ttu-id="695d1-126">Nome curto</span><span class="sxs-lookup"><span data-stu-id="695d1-126">Short name</span></span>                      | <span data-ttu-id="695d1-127">Linguagem</span><span class="sxs-lookup"><span data-stu-id="695d1-127">Language</span></span>     | <span data-ttu-id="695d1-128">Marcações</span><span class="sxs-lookup"><span data-stu-id="695d1-128">Tags</span></span>                                  | <span data-ttu-id="695d1-129">Incluída</span><span class="sxs-lookup"><span data-stu-id="695d1-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="695d1-130">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="695d1-130">Console Application</span></span>                          | [<span data-ttu-id="695d1-131">MMC</span><span class="sxs-lookup"><span data-stu-id="695d1-131">console</span></span>](#console)             | <span data-ttu-id="695d1-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="695d1-132">[C#], F#, VB</span></span> | <span data-ttu-id="695d1-133">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="695d1-133">Common/Console</span></span>                        | <span data-ttu-id="695d1-134">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-134">1.0</span></span>        |
| <span data-ttu-id="695d1-135">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="695d1-135">Class library</span></span>                                | [<span data-ttu-id="695d1-136">classlib</span><span class="sxs-lookup"><span data-stu-id="695d1-136">classlib</span></span>](#classlib)           | <span data-ttu-id="695d1-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="695d1-137">[C#], F#, VB</span></span> | <span data-ttu-id="695d1-138">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="695d1-138">Common/Library</span></span>                        | <span data-ttu-id="695d1-139">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-139">1.0</span></span>        |
| <span data-ttu-id="695d1-140">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-140">WPF Application</span></span>                              | [<span data-ttu-id="695d1-141">WFP</span><span class="sxs-lookup"><span data-stu-id="695d1-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="695d1-142">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="695d1-142">[C#], VB</span></span>     | <span data-ttu-id="695d1-143">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-143">Common/WPF</span></span>                            | <span data-ttu-id="695d1-144">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="695d1-144">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="695d1-145">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-145">WPF Class library</span></span>                            | [<span data-ttu-id="695d1-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="695d1-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="695d1-147">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="695d1-147">[C#], VB</span></span>     | <span data-ttu-id="695d1-148">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-148">Common/WPF</span></span>                            | <span data-ttu-id="695d1-149">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="695d1-149">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="695d1-150">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="695d1-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="695d1-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="695d1-152">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="695d1-152">[C#], VB</span></span>     | <span data-ttu-id="695d1-153">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-153">Common/WPF</span></span>                            | <span data-ttu-id="695d1-154">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="695d1-154">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="695d1-155">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="695d1-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="695d1-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="695d1-157">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="695d1-157">[C#], VB</span></span>     | <span data-ttu-id="695d1-158">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="695d1-158">Common/WPF</span></span>                            | <span data-ttu-id="695d1-159">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="695d1-159">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="695d1-160">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="695d1-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="695d1-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="695d1-161">winforms</span></span>](#winforms)           | <span data-ttu-id="695d1-162">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="695d1-162">[C#], VB</span></span>     | <span data-ttu-id="695d1-163">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="695d1-163">Common/WinForms</span></span>                       | <span data-ttu-id="695d1-164">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="695d1-164">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="695d1-165">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="695d1-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="695d1-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="695d1-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="695d1-167">[C#], VB</span><span class="sxs-lookup"><span data-stu-id="695d1-167">[C#], VB</span></span>     | <span data-ttu-id="695d1-168">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="695d1-168">Common/WinForms</span></span>                       | <span data-ttu-id="695d1-169">3,0 (5,0 para VB)</span><span class="sxs-lookup"><span data-stu-id="695d1-169">3.0 (5.0 for VB)</span></span>|
| <span data-ttu-id="695d1-170">Serviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="695d1-170">Worker Service</span></span>                               | [<span data-ttu-id="695d1-171">funcionários</span><span class="sxs-lookup"><span data-stu-id="695d1-171">worker</span></span>](#web-others)           | <span data-ttu-id="695d1-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-172">[C#]</span></span>         | <span data-ttu-id="695d1-173">Comum/de trabalho/Web</span><span class="sxs-lookup"><span data-stu-id="695d1-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="695d1-174">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-174">3.0</span></span>        |
| <span data-ttu-id="695d1-175">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="695d1-175">Unit Test Project</span></span>                            | [<span data-ttu-id="695d1-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="695d1-176">mstest</span></span>](#test)                 | <span data-ttu-id="695d1-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="695d1-177">[C#], F#, VB</span></span> | <span data-ttu-id="695d1-178">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="695d1-178">Test/MSTest</span></span>                           | <span data-ttu-id="695d1-179">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-179">1.0</span></span>        |
| <span data-ttu-id="695d1-180">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="695d1-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="695d1-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-181">nunit</span></span>](#nunit)                 | <span data-ttu-id="695d1-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="695d1-182">[C#], F#, VB</span></span> | <span data-ttu-id="695d1-183">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-183">Test/NUnit</span></span>                            | <span data-ttu-id="695d1-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="695d1-184">2.1.400</span></span>    |
| <span data-ttu-id="695d1-185">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="695d1-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="695d1-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="695d1-186">[C#], F#, VB</span></span> | <span data-ttu-id="695d1-187">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-187">Test/NUnit</span></span>                            | <span data-ttu-id="695d1-188">2.2</span><span class="sxs-lookup"><span data-stu-id="695d1-188">2.2</span></span>        |
| <span data-ttu-id="695d1-189">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="695d1-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-190">xunit</span></span>](#test)                  | <span data-ttu-id="695d1-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="695d1-191">[C#], F#, VB</span></span> | <span data-ttu-id="695d1-192">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-192">Test/xUnit</span></span>                            | <span data-ttu-id="695d1-193">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-193">1.0</span></span>        |
| <span data-ttu-id="695d1-194">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="695d1-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="695d1-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-195">[C#]</span></span>         | <span data-ttu-id="695d1-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="695d1-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="695d1-197">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-197">3.0</span></span>        |
| <span data-ttu-id="695d1-198">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="695d1-198">Razor Page</span></span>                                   | [<span data-ttu-id="695d1-199">page</span><span class="sxs-lookup"><span data-stu-id="695d1-199">page</span></span>](#page)                   | <span data-ttu-id="695d1-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-200">[C#]</span></span>         | <span data-ttu-id="695d1-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="695d1-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="695d1-202">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-202">2.0</span></span>        |
| <span data-ttu-id="695d1-203">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="695d1-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="695d1-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="695d1-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="695d1-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-205">[C#]</span></span>         | <span data-ttu-id="695d1-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="695d1-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="695d1-207">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-207">2.0</span></span>        |
| <span data-ttu-id="695d1-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="695d1-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="695d1-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-209">[C#]</span></span>         | <span data-ttu-id="695d1-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="695d1-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="695d1-211">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-211">2.0</span></span>        |
| <span data-ttu-id="695d1-212">Blazor Aplicativo de servidor</span><span class="sxs-lookup"><span data-stu-id="695d1-212">Blazor Server App</span></span>                            | [<span data-ttu-id="695d1-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="695d1-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="695d1-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-214">[C#]</span></span>         | <span data-ttu-id="695d1-215">SiteBlazor</span><span class="sxs-lookup"><span data-stu-id="695d1-215">Web/Blazor</span></span>                            | <span data-ttu-id="695d1-216">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-216">3.0</span></span>        |
| <span data-ttu-id="695d1-217">BlazorDo WebAssembly aplicativo</span><span class="sxs-lookup"><span data-stu-id="695d1-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="695d1-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-218">[C#]</span></span>         | <span data-ttu-id="695d1-219">SiteBlazor/WebAssembly</span><span class="sxs-lookup"><span data-stu-id="695d1-219">Web/Blazor/WebAssembly</span></span>                | <span data-ttu-id="695d1-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="695d1-220">3.1.300</span></span>    |
| <span data-ttu-id="695d1-221">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="695d1-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="695d1-222">site</span><span class="sxs-lookup"><span data-stu-id="695d1-222">web</span></span>](#web)                     | <span data-ttu-id="695d1-223">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="695d1-223">[C#], F#</span></span>     | <span data-ttu-id="695d1-224">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="695d1-224">Web/Empty</span></span>                             | <span data-ttu-id="695d1-225">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-225">1.0</span></span>        |
| <span data-ttu-id="695d1-226">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="695d1-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="695d1-227">MVC</span><span class="sxs-lookup"><span data-stu-id="695d1-227">mvc</span></span>](#web-options)             | <span data-ttu-id="695d1-228">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="695d1-228">[C#], F#</span></span>     | <span data-ttu-id="695d1-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="695d1-229">Web/MVC</span></span>                               | <span data-ttu-id="695d1-230">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-230">1.0</span></span>        |
| <span data-ttu-id="695d1-231">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="695d1-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="695d1-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="695d1-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="695d1-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-233">[C#]</span></span>         | <span data-ttu-id="695d1-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="695d1-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="695d1-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="695d1-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="695d1-236">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="695d1-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="695d1-237">angular</span><span class="sxs-lookup"><span data-stu-id="695d1-237">angular</span></span>](#spa)                 | <span data-ttu-id="695d1-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-238">[C#]</span></span>         | <span data-ttu-id="695d1-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="695d1-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="695d1-240">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-240">2.0</span></span>        |
| <span data-ttu-id="695d1-241">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="695d1-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="695d1-242">reagir</span><span class="sxs-lookup"><span data-stu-id="695d1-242">react</span></span>](#spa)                   | <span data-ttu-id="695d1-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-243">[C#]</span></span>         | <span data-ttu-id="695d1-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="695d1-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="695d1-245">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-245">2.0</span></span>        |
| <span data-ttu-id="695d1-246">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="695d1-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="695d1-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="695d1-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="695d1-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-248">[C#]</span></span>         | <span data-ttu-id="695d1-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="695d1-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="695d1-250">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-250">2.0</span></span>        |
| <span data-ttu-id="695d1-251">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="695d1-251">Razor Class Library</span></span>                          | [<span data-ttu-id="695d1-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="695d1-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="695d1-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-253">[C#]</span></span>         | <span data-ttu-id="695d1-254">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="695d1-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="695d1-255">2.1</span><span class="sxs-lookup"><span data-stu-id="695d1-255">2.1</span></span>        |
| <span data-ttu-id="695d1-256">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="695d1-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="695d1-257">webAPI</span><span class="sxs-lookup"><span data-stu-id="695d1-257">webapi</span></span>](#webapi)               | <span data-ttu-id="695d1-258">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="695d1-258">[C#], F#</span></span>     | <span data-ttu-id="695d1-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="695d1-259">Web/WebAPI</span></span>                            | <span data-ttu-id="695d1-260">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-260">1.0</span></span>        |
| <span data-ttu-id="695d1-261">ASP.NET Core serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="695d1-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="695d1-262">grpc</span><span class="sxs-lookup"><span data-stu-id="695d1-262">grpc</span></span>](#web-others)             | <span data-ttu-id="695d1-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="695d1-263">[C#]</span></span>         | <span data-ttu-id="695d1-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="695d1-264">Web/gRPC</span></span>                              | <span data-ttu-id="695d1-265">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-265">3.0</span></span>        |
| <span data-ttu-id="695d1-266">arquivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="695d1-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="695d1-267">Config</span><span class="sxs-lookup"><span data-stu-id="695d1-267">Config</span></span>                                | <span data-ttu-id="695d1-268">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-268">3.0</span></span>        |
| <span data-ttu-id="695d1-269">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="695d1-269">global.json file</span></span>                             | [<span data-ttu-id="695d1-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="695d1-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="695d1-271">Config</span><span class="sxs-lookup"><span data-stu-id="695d1-271">Config</span></span>                                | <span data-ttu-id="695d1-272">2.0</span><span class="sxs-lookup"><span data-stu-id="695d1-272">2.0</span></span>        |
| <span data-ttu-id="695d1-273">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="695d1-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="695d1-274">Config</span><span class="sxs-lookup"><span data-stu-id="695d1-274">Config</span></span>                                | <span data-ttu-id="695d1-275">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-275">1.0</span></span>        |
| <span data-ttu-id="695d1-276">Arquivo de manifesto da ferramenta local dotnet</span><span class="sxs-lookup"><span data-stu-id="695d1-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="695d1-277">Config</span><span class="sxs-lookup"><span data-stu-id="695d1-277">Config</span></span>                                | <span data-ttu-id="695d1-278">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-278">3.0</span></span>        |
| <span data-ttu-id="695d1-279">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="695d1-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="695d1-280">Config</span><span class="sxs-lookup"><span data-stu-id="695d1-280">Config</span></span>                                | <span data-ttu-id="695d1-281">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-281">1.0</span></span>        |
| <span data-ttu-id="695d1-282">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="695d1-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="695d1-283">Solução</span><span class="sxs-lookup"><span data-stu-id="695d1-283">Solution</span></span>                              | <span data-ttu-id="695d1-284">1.0</span><span class="sxs-lookup"><span data-stu-id="695d1-284">1.0</span></span>        |
| <span data-ttu-id="695d1-285">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="695d1-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="695d1-286">proto</span><span class="sxs-lookup"><span data-stu-id="695d1-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="695d1-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="695d1-287">Web/gRPC</span></span>                              | <span data-ttu-id="695d1-288">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="695d1-289">Opções</span><span class="sxs-lookup"><span data-stu-id="695d1-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="695d1-290">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="695d1-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="695d1-291">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="695d1-292">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="695d1-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="695d1-293">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="695d1-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="695d1-294">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="695d1-294">Prints out help for the command.</span></span> <span data-ttu-id="695d1-295">Ele pode ser invocado para o `dotnet new` próprio comando ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="695d1-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="695d1-296">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="695d1-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="695d1-297">Instala um pacote de modelos do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="695d1-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="695d1-298">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="695d1-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="695d1-299">Por padrão, `dotnet new` \* o passa para a versão, que representa a versão de pacote estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="695d1-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="695d1-300">Veja um exemplo na seção [exemplos](#examples) .</span><span class="sxs-lookup"><span data-stu-id="695d1-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="695d1-301">Se uma versão do modelo já tiver sido instalada quando você executar esse comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="695d1-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="695d1-302">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="695d1-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="695d1-303">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="695d1-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="695d1-304">Se nenhum nome for especificado, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="695d1-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="695d1-305">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="695d1-305">The language of the template to create.</span></span> <span data-ttu-id="695d1-306">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="695d1-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="695d1-307">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="695d1-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="695d1-308">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="695d1-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="695d1-309">Nesses casos, coloque o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="695d1-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="695d1-310">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="695d1-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="695d1-311">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="695d1-311">The name for the created output.</span></span> <span data-ttu-id="695d1-312">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="695d1-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="695d1-313">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="695d1-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="695d1-314">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="695d1-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="695d1-315">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="695d1-315">Location to place the generated output.</span></span> <span data-ttu-id="695d1-316">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="695d1-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="695d1-317">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="695d1-317">Filters templates based on available types.</span></span> <span data-ttu-id="695d1-318">Os valores predefinidos são `project` e `item` .</span><span class="sxs-lookup"><span data-stu-id="695d1-318">Predefined values are `project` and `item`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="695d1-319">Desinstala um pacote de modelos no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="695d1-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="695d1-320">Quando o `<PATH|NUGET_ID>` valor não for especificado, todos os pacotes de modelos instalados atualmente e seus modelos associados serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="695d1-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="695d1-321">Ao especificar `NUGET_ID` , não inclua o número de versão.</span><span class="sxs-lookup"><span data-stu-id="695d1-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="695d1-322">Se você não especificar um parâmetro para essa opção, o comando listará os modelos instalados e os detalhes sobre eles.</span><span class="sxs-lookup"><span data-stu-id="695d1-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="695d1-323">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="695d1-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="695d1-324">Por exemplo, *C:/Users/ \<USER> /Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que a contém não irá.</span><span class="sxs-lookup"><span data-stu-id="695d1-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="695d1-325">Não inclua uma barra de diretório final de encerramento no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="695d1-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="695d1-326">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="695d1-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="695d1-327">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="695d1-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="695d1-328">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="695d1-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="695d1-329">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="695d1-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="695d1-330">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="695d1-330">Template options</span></span>

<span data-ttu-id="695d1-331">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="695d1-331">Each project template may have additional options available.</span></span> <span data-ttu-id="695d1-332">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="695d1-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="695d1-333">console</span><span class="sxs-lookup"><span data-stu-id="695d1-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="695d1-334">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-335">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="695d1-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="695d1-336">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-337">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-337">SDK version</span></span> | <span data-ttu-id="695d1-338">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-339">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-340">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="695d1-341">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="695d1-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="695d1-342">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="695d1-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="695d1-343">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="695d1-343">Not supported for F#.</span></span> <span data-ttu-id="695d1-344">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="695d1-345">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="695d1-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-346">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="695d1-347">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-347">Available since .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="695d1-348">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-348">\*\*_</span></span>

### <a name="classlib"></a><span data-ttu-id="695d1-349">classlib</span><span class="sxs-lookup"><span data-stu-id="695d1-349">classlib</span></span>

- <span data-ttu-id="695d1-350">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-350">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="695d1-351">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-351">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-352">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="695d1-352">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="695d1-353">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="695d1-353">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="695d1-354">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="695d1-354">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="695d1-355">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="695d1-355">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="695d1-356">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="695d1-356">Not supported for F#.</span></span> <span data-ttu-id="695d1-357">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-357">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="695d1-358">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="695d1-358">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-359">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-359">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-360">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-360">\*\*_</span></span>

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> <span data-ttu-id="695d1-361">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="695d1-361">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- <span data-ttu-id="695d1-362">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-362">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="695d1-363">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-363">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-364">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="695d1-364">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="695d1-365">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="695d1-365">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="695d1-366">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="695d1-366">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="695d1-367">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="695d1-367">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="695d1-368">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="695d1-368">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-369">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-369">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-370">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-370">\*\*_</span></span>

### <a name="winforms-winformslib"></a><a name="winforms"></a> <span data-ttu-id="695d1-371">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="695d1-371">winforms, winformslib</span></span>

- <span data-ttu-id="695d1-372">_*`--langVersion <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-372">_*`--langVersion <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="695d1-373">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="695d1-373">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="695d1-374">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="695d1-374">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="695d1-375">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="695d1-375">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-376">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-376">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-377">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-377">\*\*_</span></span>

### <a name="worker-grpc"></a><a name="web-others"></a> <span data-ttu-id="695d1-378">trabalho, grpc</span><span class="sxs-lookup"><span data-stu-id="695d1-378">worker, grpc</span></span>

- <span data-ttu-id="695d1-379">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-379">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="695d1-380">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-380">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-381">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="695d1-381">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="695d1-382">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="695d1-382">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="695d1-383">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-383">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-384">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-384">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-385">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-385">\*\*_</span></span>

### <a name="mstest-xunit"></a><a name="test"></a> <span data-ttu-id="695d1-386">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-386">mstest, xunit</span></span>

- <span data-ttu-id="695d1-387">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-387">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="695d1-388">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-389">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="695d1-389">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="695d1-390">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-390">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-391">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-391">SDK version</span></span> | <span data-ttu-id="695d1-392">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-392">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-393">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-393">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-394">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-394">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="695d1-395">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="695d1-395">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-396">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-396">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-397">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-397">\*\*_</span></span>

### <a name="nunit"></a><span data-ttu-id="695d1-398">NUnit</span><span class="sxs-lookup"><span data-stu-id="695d1-398">nunit</span></span>

- <span data-ttu-id="695d1-399">_*`-f|--framework <FRAMEWORK>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-399">_*`-f|--framework <FRAMEWORK>`*\*</span></span>

  <span data-ttu-id="695d1-400">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-400">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="695d1-401">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-401">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-402">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-402">SDK version</span></span> | <span data-ttu-id="695d1-403">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-403">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-404">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-404">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-405">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-405">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="695d1-406">2.2</span><span class="sxs-lookup"><span data-stu-id="695d1-406">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="695d1-407">2.1</span><span class="sxs-lookup"><span data-stu-id="695d1-407">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="695d1-408">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="695d1-408">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-409">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-409">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-410">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-410">\*\*_</span></span>

### <a name="page"></a><span data-ttu-id="695d1-411">página</span><span class="sxs-lookup"><span data-stu-id="695d1-411">page</span></span>

- <span data-ttu-id="695d1-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-412">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="695d1-413">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-413">Namespace for the generated code.</span></span> <span data-ttu-id="695d1-414">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="695d1-414">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="695d1-415">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="695d1-415">Creates the page without a PageModel.</span></span>

<span data-ttu-id="695d1-416">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-416">\*\*_</span></span>

### <a name="viewimports-proto"></a><a name="namespace"></a> <span data-ttu-id="695d1-417">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="695d1-417">viewimports, proto</span></span>

- <span data-ttu-id="695d1-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-418">_*`-na|--namespace <NAMESPACE_NAME>`*\*</span></span>

  <span data-ttu-id="695d1-419">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-419">Namespace for the generated code.</span></span> <span data-ttu-id="695d1-420">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="695d1-420">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="695d1-421">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-421">\*\*_</span></span>

### <a name="blazorserver"></a><span data-ttu-id="695d1-422">blazorserver</span><span class="sxs-lookup"><span data-stu-id="695d1-422">blazorserver</span></span>

- <span data-ttu-id="695d1-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-423">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="695d1-424">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="695d1-424">The type of authentication to use.</span></span> <span data-ttu-id="695d1-425">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="695d1-425">The possible values are:</span></span>

  - <span data-ttu-id="695d1-426">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="695d1-426">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="695d1-427">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="695d1-427">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="695d1-428">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="695d1-428">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="695d1-429">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="695d1-429">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="695d1-430">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="695d1-430">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="695d1-431">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="695d1-431">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="695d1-432">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-432">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="695d1-433">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-433">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-434">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="695d1-434">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="695d1-435">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-435">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="695d1-436">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-436">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="695d1-437">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-437">The reset password policy ID for this project.</span></span> <span data-ttu-id="695d1-438">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-438">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="695d1-439">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-439">The edit profile policy ID for this project.</span></span> <span data-ttu-id="695d1-440">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-440">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="695d1-441">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-441">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="695d1-442">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-442">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="695d1-443">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="695d1-443">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="695d1-444">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-444">The Client ID for this project.</span></span> <span data-ttu-id="695d1-445">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-445">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="695d1-446">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="695d1-446">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="695d1-447">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="695d1-447">The domain for the directory tenant.</span></span> <span data-ttu-id="695d1-448">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-448">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-449">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="695d1-449">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="695d1-450">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-450">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="695d1-451">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-451">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="695d1-452">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="695d1-452">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="695d1-453">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="695d1-453">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="695d1-454">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-454">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-455">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="695d1-455">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="695d1-456">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="695d1-456">Allows this application read-access to the directory.</span></span> <span data-ttu-id="695d1-457">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-457">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="695d1-458">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-458">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="695d1-459">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="695d1-459">Turns off HTTPS.</span></span> <span data-ttu-id="695d1-460">Essa opção só se aplica se `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` não estiverem sendo usados para `--auth` .</span><span class="sxs-lookup"><span data-stu-id="695d1-460">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="695d1-461">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="695d1-461">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="695d1-462">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-462">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-463">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-463">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-464">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-464">\*\*_</span></span>

### <a name="web"></a><span data-ttu-id="695d1-465">web</span><span class="sxs-lookup"><span data-stu-id="695d1-465">web</span></span>

- <span data-ttu-id="695d1-466">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-466">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="695d1-467">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-467">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="695d1-468">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-468">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-469">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-469">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="695d1-470">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-470">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-471">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-471">SDK version</span></span> | <span data-ttu-id="695d1-472">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-472">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-473">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-473">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-474">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-474">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="695d1-475">2.1</span><span class="sxs-lookup"><span data-stu-id="695d1-475">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="695d1-476">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-476">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="695d1-477">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="695d1-477">Turns off HTTPS.</span></span>

<span data-ttu-id="695d1-478">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-478">\*\*_</span></span>

### <a name="mvc-webapp"></a><a name="web-options"></a> <span data-ttu-id="695d1-479">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="695d1-479">mvc, webapp</span></span>

- <span data-ttu-id="695d1-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-480">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="695d1-481">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="695d1-481">The type of authentication to use.</span></span> <span data-ttu-id="695d1-482">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="695d1-482">The possible values are:</span></span>

  - <span data-ttu-id="695d1-483">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="695d1-483">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="695d1-484">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="695d1-484">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="695d1-485">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="695d1-485">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="695d1-486">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="695d1-486">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="695d1-487">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="695d1-487">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="695d1-488">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="695d1-488">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="695d1-489">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-489">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="695d1-490">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-490">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-491">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="695d1-491">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="695d1-492">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-492">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="695d1-493">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-493">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="695d1-494">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-494">The reset password policy ID for this project.</span></span> <span data-ttu-id="695d1-495">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-495">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="695d1-496">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-496">The edit profile policy ID for this project.</span></span> <span data-ttu-id="695d1-497">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-497">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="695d1-498">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-498">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="695d1-499">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-499">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="695d1-500">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="695d1-500">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="695d1-501">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-501">The Client ID for this project.</span></span> <span data-ttu-id="695d1-502">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-502">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="695d1-503">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="695d1-503">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="695d1-504">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="695d1-504">The domain for the directory tenant.</span></span> <span data-ttu-id="695d1-505">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-505">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-506">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="695d1-506">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="695d1-507">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-507">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="695d1-508">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-508">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="695d1-509">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="695d1-509">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="695d1-510">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="695d1-510">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="695d1-511">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-511">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-512">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="695d1-512">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="695d1-513">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="695d1-513">Allows this application read-access to the directory.</span></span> <span data-ttu-id="695d1-514">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-514">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="695d1-515">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-515">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="695d1-516">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="695d1-516">Turns off HTTPS.</span></span> <span data-ttu-id="695d1-517">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="695d1-517">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="695d1-518">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="695d1-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="695d1-519">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="695d1-520">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-521">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="695d1-521">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="695d1-522">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-523">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-523">SDK version</span></span> | <span data-ttu-id="695d1-524">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-525">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-526">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-526">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="695d1-527">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-527">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="695d1-528">Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-528">Includes BrowserLink in the project.</span></span> <span data-ttu-id="695d1-529">Opção não disponível no SDK do .NET Core 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="695d1-529">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="695d1-530">Determina se o projeto está configurado para usar a [compilação de tempo de execução do Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações de depuração.</span><span class="sxs-lookup"><span data-stu-id="695d1-530">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="695d1-531">Opção disponível desde o SDK do 3.1.201 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="695d1-531">Option available since .NET Core 3.1.201 SDK.</span></span>

<span data-ttu-id="695d1-532">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-532">\*\*_</span></span>

### <a name="angular-react"></a><a name="spa"></a> <span data-ttu-id="695d1-533">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="695d1-533">angular, react</span></span>

- <span data-ttu-id="695d1-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-534">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="695d1-535">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="695d1-535">The type of authentication to use.</span></span> <span data-ttu-id="695d1-536">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="695d1-536">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="695d1-537">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="695d1-537">The possible values are:</span></span>

  - <span data-ttu-id="695d1-538">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="695d1-538">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="695d1-539">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="695d1-539">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="695d1-540">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-540">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="695d1-541">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="695d1-542">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="695d1-542">Turns off HTTPS.</span></span> <span data-ttu-id="695d1-543">Essa opção se aplica somente se a autenticação for `None` .</span><span class="sxs-lookup"><span data-stu-id="695d1-543">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="695d1-544">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="695d1-544">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="695d1-545">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-545">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-546">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="695d1-546">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="695d1-547">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-547">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-548">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-548">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="695d1-549">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-549">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-550">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-550">SDK version</span></span> | <span data-ttu-id="695d1-551">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-551">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-552">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-552">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-553">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-553">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="695d1-554">2.1</span><span class="sxs-lookup"><span data-stu-id="695d1-554">2.1</span></span>         | `netcoreapp2.0` |

<span data-ttu-id="695d1-555">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-555">\*\*_</span></span>

### <a name="reactredux"></a><span data-ttu-id="695d1-556">reactredux</span><span class="sxs-lookup"><span data-stu-id="695d1-556">reactredux</span></span>

- <span data-ttu-id="695d1-557">_*`--exclude-launch-settings`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-557">_*`--exclude-launch-settings`*\*</span></span>

  <span data-ttu-id="695d1-558">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-558">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="695d1-559">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-559">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-560">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-560">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="695d1-561">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-561">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-562">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-562">SDK version</span></span> | <span data-ttu-id="695d1-563">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-563">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-564">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-564">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-565">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-565">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="695d1-566">2.1</span><span class="sxs-lookup"><span data-stu-id="695d1-566">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="695d1-567">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-567">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="695d1-568">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="695d1-568">Turns off HTTPS.</span></span>

<span data-ttu-id="695d1-569">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-569">\*\*_</span></span>

### <a name="razorclasslib"></a><span data-ttu-id="695d1-570">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="695d1-570">razorclasslib</span></span>

- <span data-ttu-id="695d1-571">_*`--no-restore`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-571">_*`--no-restore`*\*</span></span>

  <span data-ttu-id="695d1-572">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-572">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="695d1-573">Dá suporte à adição de páginas e exibições do Razor tradicionais, além dos componentes dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="695d1-573">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="695d1-574">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="695d1-574">Available since .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="695d1-575">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-575">\*\*_</span></span>
  
### <a name="webapi"></a><span data-ttu-id="695d1-576">webapi</span><span class="sxs-lookup"><span data-stu-id="695d1-576">webapi</span></span>

- <span data-ttu-id="695d1-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-577">_*`-au|--auth <AUTHENTICATION_TYPE>`*\*</span></span>

  <span data-ttu-id="695d1-578">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="695d1-578">The type of authentication to use.</span></span> <span data-ttu-id="695d1-579">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="695d1-579">The possible values are:</span></span>

  - <span data-ttu-id="695d1-580">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="695d1-580">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="695d1-581">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="695d1-581">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="695d1-582">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="695d1-582">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="695d1-583">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="695d1-583">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="695d1-584">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-584">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="695d1-585">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-585">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="695d1-586">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="695d1-586">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="695d1-587">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-587">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="695d1-588">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="695d1-588">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="695d1-589">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-589">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="695d1-590">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-590">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="695d1-591">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="695d1-591">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="695d1-592">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-592">The Client ID for this project.</span></span> <span data-ttu-id="695d1-593">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-593">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="695d1-594">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="695d1-594">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="695d1-595">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="695d1-595">The domain for the directory tenant.</span></span> <span data-ttu-id="695d1-596">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-596">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="695d1-597">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="695d1-597">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="695d1-598">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="695d1-598">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="695d1-599">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="695d1-599">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="695d1-600">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="695d1-600">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="695d1-601">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="695d1-601">Allows this application read-access to the directory.</span></span> <span data-ttu-id="695d1-602">Aplica-se somente à `SingleOrg` autenticação.</span><span class="sxs-lookup"><span data-stu-id="695d1-602">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="695d1-603">Exclui *launchSettings.js* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="695d1-603">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="695d1-604">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="695d1-604">Turns off HTTPS.</span></span> <span data-ttu-id="695d1-605">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="695d1-605">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="695d1-606">Essa opção só se aplica se `IndividualB2C` ou `SingleOrg` não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="695d1-606">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="695d1-607">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="695d1-607">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="695d1-608">Aplica-se somente à `IndividualB2C` autenticação.</span><span class="sxs-lookup"><span data-stu-id="695d1-608">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="695d1-609">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="695d1-609">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="695d1-610">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="695d1-610">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="695d1-611">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="695d1-611">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="695d1-612">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="695d1-612">SDK version</span></span> | <span data-ttu-id="695d1-613">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="695d1-613">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="695d1-614">3.1</span><span class="sxs-lookup"><span data-stu-id="695d1-614">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="695d1-615">3.0</span><span class="sxs-lookup"><span data-stu-id="695d1-615">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="695d1-616">2.1</span><span class="sxs-lookup"><span data-stu-id="695d1-616">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="695d1-617">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="695d1-617">Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="695d1-618">\*\*_</span><span class="sxs-lookup"><span data-stu-id="695d1-618">\*\*_</span></span>

### <a name="globaljson"></a><span data-ttu-id="695d1-619">globaljson</span><span class="sxs-lookup"><span data-stu-id="695d1-619">globaljson</span></span>

- <span data-ttu-id="695d1-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span><span class="sxs-lookup"><span data-stu-id="695d1-620">_*`--sdk-version <VERSION_NUMBER>`*\*</span></span>

  <span data-ttu-id="695d1-621">Especifica a versão do SDK do .NET Core a ser usada na *global.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="695d1-621">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="695d1-622">Exemplos</span><span class="sxs-lookup"><span data-stu-id="695d1-622">Examples</span></span>

- <span data-ttu-id="695d1-623">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="695d1-623">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="695d1-624">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="695d1-624">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="695d1-625">Crie um projeto de biblioteca de classe .NET Standard no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="695d1-625">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="695d1-626">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="695d1-626">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="695d1-627">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="695d1-627">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="695d1-628">Listar todos os modelos disponíveis para modelos de aplicativo de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="695d1-628">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="695d1-629">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="695d1-629">List all templates matching the *we* substring.</span></span> <span data-ttu-id="695d1-630">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="695d1-630">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="695d1-631">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="695d1-631">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="695d1-632">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="695d1-632">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="695d1-633">Instale a versão 2,0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="695d1-633">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="695d1-634">Liste os modelos instalados e os detalhes sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="695d1-634">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="695d1-635">Crie um *global.jsno* diretório atual definindo a versão do SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="695d1-635">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="695d1-636">Confira também</span><span class="sxs-lookup"><span data-stu-id="695d1-636">See also</span></span>

- [<span data-ttu-id="695d1-637">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="695d1-637">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="695d1-638">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="695d1-638">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="695d1-639">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="695d1-639">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="695d1-640">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="695d1-640">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
