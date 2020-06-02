---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 04/10/2020
ms.openlocfilehash: 39301ad95761848b60b45cb5c18ede937f70c32c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283969"
---
# <a name="dotnet-new"></a><span data-ttu-id="2cce5-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2cce5-103">dotnet new</span></span>

<span data-ttu-id="2cce5-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="2cce5-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2cce5-105">Nome</span><span class="sxs-lookup"><span data-stu-id="2cce5-105">Name</span></span>

<span data-ttu-id="2cce5-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2cce5-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2cce5-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="2cce5-108">Description</span><span class="sxs-lookup"><span data-stu-id="2cce5-108">Description</span></span>

<span data-ttu-id="2cce5-109">O `dotnet new` comando cria um projeto do .NET Core ou outros artefatos com base em um modelo.</span><span class="sxs-lookup"><span data-stu-id="2cce5-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="2cce5-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="2cce5-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="2cce5-111">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="2cce5-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="2cce5-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2cce5-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="2cce5-113">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="2cce5-114">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="2cce5-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="2cce5-115">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="2cce5-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="2cce5-116">Você pode executar `dotnet new --list` ou `dotnet new -l` para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="2cce5-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="2cce5-117">Se o `TEMPLATE` valor não for uma correspondência exata no texto na coluna **modelos** ou **nome curto** da tabela retornada, uma correspondência de subcadeia de caracteres será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="2cce5-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="2cce5-118">A partir do SDK do .NET Core 3,0, a CLI procura modelos em NuGet.org quando você invoca o `dotnet new` comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="2cce5-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="2cce5-119">Se a CLI não encontrar uma correspondência de modelo ao invocar `dotnet new` , nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="2cce5-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="2cce5-120">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="2cce5-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="2cce5-121">Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="2cce5-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="2cce5-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2cce5-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="2cce5-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="2cce5-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="2cce5-124">Clique no link nome curto para ver as opções de modelo específicas.</span><span class="sxs-lookup"><span data-stu-id="2cce5-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="2cce5-125">Modelos</span><span class="sxs-lookup"><span data-stu-id="2cce5-125">Templates</span></span>                                    | <span data-ttu-id="2cce5-126">Nome curto</span><span class="sxs-lookup"><span data-stu-id="2cce5-126">Short name</span></span>                      | <span data-ttu-id="2cce5-127">Language</span><span class="sxs-lookup"><span data-stu-id="2cce5-127">Language</span></span>     | <span data-ttu-id="2cce5-128">Marcações</span><span class="sxs-lookup"><span data-stu-id="2cce5-128">Tags</span></span>                                  | <span data-ttu-id="2cce5-129">Incluída</span><span class="sxs-lookup"><span data-stu-id="2cce5-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="2cce5-130">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="2cce5-130">Console Application</span></span>                          | [<span data-ttu-id="2cce5-131">MMC</span><span class="sxs-lookup"><span data-stu-id="2cce5-131">console</span></span>](#console)             | <span data-ttu-id="2cce5-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2cce5-132">[C#], F#, VB</span></span> | <span data-ttu-id="2cce5-133">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="2cce5-133">Common/Console</span></span>                        | <span data-ttu-id="2cce5-134">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-134">1.0</span></span>        |
| <span data-ttu-id="2cce5-135">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2cce5-135">Class library</span></span>                                | [<span data-ttu-id="2cce5-136">classlib</span><span class="sxs-lookup"><span data-stu-id="2cce5-136">classlib</span></span>](#classlib)           | <span data-ttu-id="2cce5-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2cce5-137">[C#], F#, VB</span></span> | <span data-ttu-id="2cce5-138">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="2cce5-138">Common/Library</span></span>                        | <span data-ttu-id="2cce5-139">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-139">1.0</span></span>        |
| <span data-ttu-id="2cce5-140">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-140">WPF Application</span></span>                              | [<span data-ttu-id="2cce5-141">WFP</span><span class="sxs-lookup"><span data-stu-id="2cce5-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="2cce5-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-142">[C#]</span></span>         | <span data-ttu-id="2cce5-143">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-143">Common/WPF</span></span>                            | <span data-ttu-id="2cce5-144">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-144">3.0</span></span>        |
| <span data-ttu-id="2cce5-145">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-145">WPF Class library</span></span>                            | [<span data-ttu-id="2cce5-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="2cce5-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="2cce5-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-147">[C#]</span></span>         | <span data-ttu-id="2cce5-148">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-148">Common/WPF</span></span>                            | <span data-ttu-id="2cce5-149">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-149">3.0</span></span>        |
| <span data-ttu-id="2cce5-150">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="2cce5-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="2cce5-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="2cce5-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-152">[C#]</span></span>         | <span data-ttu-id="2cce5-153">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-153">Common/WPF</span></span>                            | <span data-ttu-id="2cce5-154">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-154">3.0</span></span>        |
| <span data-ttu-id="2cce5-155">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="2cce5-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="2cce5-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="2cce5-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-157">[C#]</span></span>         | <span data-ttu-id="2cce5-158">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="2cce5-158">Common/WPF</span></span>                            | <span data-ttu-id="2cce5-159">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-159">3.0</span></span>        |
| <span data-ttu-id="2cce5-160">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="2cce5-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="2cce5-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="2cce5-161">winforms</span></span>](#winforms)           | <span data-ttu-id="2cce5-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-162">[C#]</span></span>         | <span data-ttu-id="2cce5-163">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="2cce5-163">Common/WinForms</span></span>                       | <span data-ttu-id="2cce5-164">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-164">3.0</span></span>        |
| <span data-ttu-id="2cce5-165">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="2cce5-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="2cce5-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="2cce5-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="2cce5-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-167">[C#]</span></span>         | <span data-ttu-id="2cce5-168">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="2cce5-168">Common/WinForms</span></span>                       | <span data-ttu-id="2cce5-169">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-169">3.0</span></span>        |
| <span data-ttu-id="2cce5-170">Serviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="2cce5-170">Worker Service</span></span>                               | [<span data-ttu-id="2cce5-171">funcionários</span><span class="sxs-lookup"><span data-stu-id="2cce5-171">worker</span></span>](#web-others)           | <span data-ttu-id="2cce5-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-172">[C#]</span></span>         | <span data-ttu-id="2cce5-173">Comum/de trabalho/Web</span><span class="sxs-lookup"><span data-stu-id="2cce5-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="2cce5-174">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-174">3.0</span></span>        |
| <span data-ttu-id="2cce5-175">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="2cce5-175">Unit Test Project</span></span>                            | [<span data-ttu-id="2cce5-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="2cce5-176">mstest</span></span>](#test)                 | <span data-ttu-id="2cce5-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2cce5-177">[C#], F#, VB</span></span> | <span data-ttu-id="2cce5-178">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="2cce5-178">Test/MSTest</span></span>                           | <span data-ttu-id="2cce5-179">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-179">1.0</span></span>        |
| <span data-ttu-id="2cce5-180">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="2cce5-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="2cce5-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="2cce5-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2cce5-182">[C#], F#, VB</span></span> | <span data-ttu-id="2cce5-183">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-183">Test/NUnit</span></span>                            | <span data-ttu-id="2cce5-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="2cce5-184">2.1.400</span></span>    |
| <span data-ttu-id="2cce5-185">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="2cce5-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="2cce5-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2cce5-186">[C#], F#, VB</span></span> | <span data-ttu-id="2cce5-187">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-187">Test/NUnit</span></span>                            | <span data-ttu-id="2cce5-188">2.2</span><span class="sxs-lookup"><span data-stu-id="2cce5-188">2.2</span></span>        |
| <span data-ttu-id="2cce5-189">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="2cce5-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-190">xunit</span></span>](#test)                  | <span data-ttu-id="2cce5-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="2cce5-191">[C#], F#, VB</span></span> | <span data-ttu-id="2cce5-192">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-192">Test/xUnit</span></span>                            | <span data-ttu-id="2cce5-193">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-193">1.0</span></span>        |
| <span data-ttu-id="2cce5-194">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="2cce5-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="2cce5-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-195">[C#]</span></span>         | <span data-ttu-id="2cce5-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2cce5-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="2cce5-197">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-197">3.0</span></span>        |
| <span data-ttu-id="2cce5-198">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="2cce5-198">Razor Page</span></span>                                   | [<span data-ttu-id="2cce5-199">Web</span><span class="sxs-lookup"><span data-stu-id="2cce5-199">page</span></span>](#page)                   | <span data-ttu-id="2cce5-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-200">[C#]</span></span>         | <span data-ttu-id="2cce5-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2cce5-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="2cce5-202">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-202">2.0</span></span>        |
| <span data-ttu-id="2cce5-203">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="2cce5-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="2cce5-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="2cce5-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="2cce5-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-205">[C#]</span></span>         | <span data-ttu-id="2cce5-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2cce5-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="2cce5-207">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-207">2.0</span></span>        |
| <span data-ttu-id="2cce5-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="2cce5-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="2cce5-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-209">[C#]</span></span>         | <span data-ttu-id="2cce5-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2cce5-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="2cce5-211">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-211">2.0</span></span>        |
| <span data-ttu-id="2cce5-212">Aplicativo de servidor mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="2cce5-212">Blazor Server App</span></span>                            | [<span data-ttu-id="2cce5-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="2cce5-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="2cce5-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-214">[C#]</span></span>         | <span data-ttu-id="2cce5-215">Web/mais e mais</span><span class="sxs-lookup"><span data-stu-id="2cce5-215">Web/Blazor</span></span>                            | <span data-ttu-id="2cce5-216">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-216">3.0</span></span>        |
| <span data-ttu-id="2cce5-217">Aplicativo Webassembly mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="2cce5-217">Blazor WebAssembly App</span></span>                       | `blazorwasm`                    | <span data-ttu-id="2cce5-218">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-218">[C#]</span></span>         | <span data-ttu-id="2cce5-219">Web/mais incrivelmente/Webassembly</span><span class="sxs-lookup"><span data-stu-id="2cce5-219">Web/Blazor/WebAssembly</span></span>                            | <span data-ttu-id="2cce5-220">3.1.300</span><span class="sxs-lookup"><span data-stu-id="2cce5-220">3.1.300</span></span>    |
| <span data-ttu-id="2cce5-221">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="2cce5-221">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="2cce5-222">site</span><span class="sxs-lookup"><span data-stu-id="2cce5-222">web</span></span>](#web)                     | <span data-ttu-id="2cce5-223">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2cce5-223">[C#], F#</span></span>     | <span data-ttu-id="2cce5-224">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="2cce5-224">Web/Empty</span></span>                             | <span data-ttu-id="2cce5-225">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-225">1.0</span></span>        |
| <span data-ttu-id="2cce5-226">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="2cce5-226">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="2cce5-227">MVC</span><span class="sxs-lookup"><span data-stu-id="2cce5-227">mvc</span></span>](#web-options)             | <span data-ttu-id="2cce5-228">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2cce5-228">[C#], F#</span></span>     | <span data-ttu-id="2cce5-229">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="2cce5-229">Web/MVC</span></span>                               | <span data-ttu-id="2cce5-230">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-230">1.0</span></span>        |
| <span data-ttu-id="2cce5-231">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2cce5-231">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="2cce5-232">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="2cce5-232">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="2cce5-233">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-233">[C#]</span></span>         | <span data-ttu-id="2cce5-234">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="2cce5-234">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="2cce5-235">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-235">2.2, 2.0</span></span>   |
| <span data-ttu-id="2cce5-236">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="2cce5-236">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="2cce5-237">angular</span><span class="sxs-lookup"><span data-stu-id="2cce5-237">angular</span></span>](#spa)                 | <span data-ttu-id="2cce5-238">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-238">[C#]</span></span>         | <span data-ttu-id="2cce5-239">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2cce5-239">Web/MVC/SPA</span></span>                           | <span data-ttu-id="2cce5-240">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-240">2.0</span></span>        |
| <span data-ttu-id="2cce5-241">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="2cce5-241">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="2cce5-242">reagir</span><span class="sxs-lookup"><span data-stu-id="2cce5-242">react</span></span>](#spa)                   | <span data-ttu-id="2cce5-243">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-243">[C#]</span></span>         | <span data-ttu-id="2cce5-244">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2cce5-244">Web/MVC/SPA</span></span>                           | <span data-ttu-id="2cce5-245">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-245">2.0</span></span>        |
| <span data-ttu-id="2cce5-246">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="2cce5-246">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="2cce5-247">reactredux</span><span class="sxs-lookup"><span data-stu-id="2cce5-247">reactredux</span></span>](#reactredux)       | <span data-ttu-id="2cce5-248">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-248">[C#]</span></span>         | <span data-ttu-id="2cce5-249">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="2cce5-249">Web/MVC/SPA</span></span>                           | <span data-ttu-id="2cce5-250">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-250">2.0</span></span>        |
| <span data-ttu-id="2cce5-251">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2cce5-251">Razor Class Library</span></span>                          | [<span data-ttu-id="2cce5-252">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="2cce5-252">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="2cce5-253">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-253">[C#]</span></span>         | <span data-ttu-id="2cce5-254">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="2cce5-254">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="2cce5-255">2.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-255">2.1</span></span>        |
| <span data-ttu-id="2cce5-256">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2cce5-256">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="2cce5-257">webAPI</span><span class="sxs-lookup"><span data-stu-id="2cce5-257">webapi</span></span>](#webapi)               | <span data-ttu-id="2cce5-258">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="2cce5-258">[C#], F#</span></span>     | <span data-ttu-id="2cce5-259">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="2cce5-259">Web/WebAPI</span></span>                            | <span data-ttu-id="2cce5-260">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-260">1.0</span></span>        |
| <span data-ttu-id="2cce5-261">ASP.NET Core serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="2cce5-261">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="2cce5-262">grpc</span><span class="sxs-lookup"><span data-stu-id="2cce5-262">grpc</span></span>](#web-others)             | <span data-ttu-id="2cce5-263">[C#]</span><span class="sxs-lookup"><span data-stu-id="2cce5-263">[C#]</span></span>         | <span data-ttu-id="2cce5-264">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="2cce5-264">Web/gRPC</span></span>                              | <span data-ttu-id="2cce5-265">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-265">3.0</span></span>        |
| <span data-ttu-id="2cce5-266">arquivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="2cce5-266">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="2cce5-267">Config</span><span class="sxs-lookup"><span data-stu-id="2cce5-267">Config</span></span>                                | <span data-ttu-id="2cce5-268">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-268">3.0</span></span>        |
| <span data-ttu-id="2cce5-269">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="2cce5-269">global.json file</span></span>                             | [<span data-ttu-id="2cce5-270">globaljson</span><span class="sxs-lookup"><span data-stu-id="2cce5-270">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="2cce5-271">Config</span><span class="sxs-lookup"><span data-stu-id="2cce5-271">Config</span></span>                                | <span data-ttu-id="2cce5-272">2,0</span><span class="sxs-lookup"><span data-stu-id="2cce5-272">2.0</span></span>        |
| <span data-ttu-id="2cce5-273">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="2cce5-273">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="2cce5-274">Config</span><span class="sxs-lookup"><span data-stu-id="2cce5-274">Config</span></span>                                | <span data-ttu-id="2cce5-275">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-275">1.0</span></span>        |
| <span data-ttu-id="2cce5-276">Arquivo de manifesto da ferramenta local dotnet</span><span class="sxs-lookup"><span data-stu-id="2cce5-276">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="2cce5-277">Config</span><span class="sxs-lookup"><span data-stu-id="2cce5-277">Config</span></span>                                | <span data-ttu-id="2cce5-278">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-278">3.0</span></span>        |
| <span data-ttu-id="2cce5-279">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="2cce5-279">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="2cce5-280">Config</span><span class="sxs-lookup"><span data-stu-id="2cce5-280">Config</span></span>                                | <span data-ttu-id="2cce5-281">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-281">1.0</span></span>        |
| <span data-ttu-id="2cce5-282">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="2cce5-282">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="2cce5-283">Solução</span><span class="sxs-lookup"><span data-stu-id="2cce5-283">Solution</span></span>                              | <span data-ttu-id="2cce5-284">1.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-284">1.0</span></span>        |
| <span data-ttu-id="2cce5-285">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="2cce5-285">Protocol Buffer File</span></span>                         | [<span data-ttu-id="2cce5-286">proto</span><span class="sxs-lookup"><span data-stu-id="2cce5-286">proto</span></span>](#namespace)             |              | <span data-ttu-id="2cce5-287">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="2cce5-287">Web/gRPC</span></span>                              | <span data-ttu-id="2cce5-288">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-288">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="2cce5-289">Opções</span><span class="sxs-lookup"><span data-stu-id="2cce5-289">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="2cce5-290">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="2cce5-290">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="2cce5-291">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-291">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="2cce5-292">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="2cce5-292">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="2cce5-293">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="2cce5-293">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2cce5-294">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="2cce5-294">Prints out help for the command.</span></span> <span data-ttu-id="2cce5-295">Ele pode ser invocado para o `dotnet new` próprio comando ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="2cce5-295">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="2cce5-296">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-296">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="2cce5-297">Instala um pacote de modelos do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2cce5-297">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2cce5-298">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-298">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="2cce5-299">Por padrão, `dotnet new` \* o passa para a versão, que representa a versão de pacote estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="2cce5-299">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="2cce5-300">Veja um exemplo na seção [exemplos](#examples) .</span><span class="sxs-lookup"><span data-stu-id="2cce5-300">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="2cce5-301">Se uma versão do modelo já tiver sido instalada quando você executar esse comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-301">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="2cce5-302">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="2cce5-302">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="2cce5-303">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-303">Lists templates containing the specified name.</span></span> <span data-ttu-id="2cce5-304">Se nenhum nome for especificado, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="2cce5-304">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="2cce5-305">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-305">The language of the template to create.</span></span> <span data-ttu-id="2cce5-306">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="2cce5-306">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="2cce5-307">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="2cce5-307">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2cce5-308">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="2cce5-308">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="2cce5-309">Nesses casos, coloque o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="2cce5-309">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="2cce5-310">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-310">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="2cce5-311">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-311">The name for the created output.</span></span> <span data-ttu-id="2cce5-312">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-312">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="2cce5-313">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="2cce5-313">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="2cce5-314">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="2cce5-314">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="2cce5-315">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-315">Location to place the generated output.</span></span> <span data-ttu-id="2cce5-316">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2cce5-316">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="2cce5-317">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2cce5-317">Filters templates based on available types.</span></span> <span data-ttu-id="2cce5-318">Os valores predefinidos são `project` , `item` e `other` .</span><span class="sxs-lookup"><span data-stu-id="2cce5-318">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="2cce5-319">Desinstala um pacote de modelos no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="2cce5-319">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="2cce5-320">Quando o `<PATH|NUGET_ID>` valor não for especificado, todos os pacotes de modelos instalados atualmente e seus modelos associados serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="2cce5-320">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="2cce5-321">Ao especificar `NUGET_ID` , não inclua o número de versão.</span><span class="sxs-lookup"><span data-stu-id="2cce5-321">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="2cce5-322">Se você não especificar um parâmetro para essa opção, o comando listará os modelos instalados e os detalhes sobre eles.</span><span class="sxs-lookup"><span data-stu-id="2cce5-322">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2cce5-323">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="2cce5-323">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="2cce5-324">Por exemplo, *C:/Users/ \<USER> /Documents/templates/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que a contém não irá.</span><span class="sxs-lookup"><span data-stu-id="2cce5-324">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="2cce5-325">Não inclua uma barra de diretório final de encerramento no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="2cce5-325">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="2cce5-326">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="2cce5-326">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="2cce5-327">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-327">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="2cce5-328">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="2cce5-328">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="2cce5-329">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-329">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="2cce5-330">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="2cce5-330">Template options</span></span>

<span data-ttu-id="2cce5-331">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2cce5-331">Each project template may have additional options available.</span></span> <span data-ttu-id="2cce5-332">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="2cce5-332">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="2cce5-333">console</span><span class="sxs-lookup"><span data-stu-id="2cce5-333">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-334">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-334">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-335">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-335">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="2cce5-336">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-336">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-337">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-337">SDK version</span></span> | <span data-ttu-id="2cce5-338">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-338">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-339">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-339">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-340">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-340">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2cce5-341">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-341">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2cce5-342">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2cce5-342">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="2cce5-343">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="2cce5-343">Not supported for F#.</span></span> <span data-ttu-id="2cce5-344">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-344">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2cce5-345">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2cce5-345">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-346">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-346">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="2cce5-347">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-347">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="2cce5-348">classlib</span><span class="sxs-lookup"><span data-stu-id="2cce5-348">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-349">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-349">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-350">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2cce5-350">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="2cce5-351">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-351">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2cce5-352">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-352">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2cce5-353">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2cce5-353">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="2cce5-354">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="2cce5-354">Not supported for F#.</span></span> <span data-ttu-id="2cce5-355">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-355">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2cce5-356">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2cce5-356">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-357">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-357">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="2cce5-358">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="2cce5-358">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-359">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-359">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-360">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-360">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="2cce5-361">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2cce5-361">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2cce5-362">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-362">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2cce5-363">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2cce5-363">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="2cce5-364">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2cce5-364">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-365">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-365">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="2cce5-366">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="2cce5-366">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="2cce5-367">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-367">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="2cce5-368">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="2cce5-368">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="2cce5-369">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="2cce5-369">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-370">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-370">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="2cce5-371">trabalho, grpc</span><span class="sxs-lookup"><span data-stu-id="2cce5-371">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-372">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-372">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-373">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-373">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="2cce5-374">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2cce5-374">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-375">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-375">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-376">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-376">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="2cce5-377">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-377">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-378">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-378">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-379">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-379">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="2cce5-380">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-380">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-381">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-381">SDK version</span></span> | <span data-ttu-id="2cce5-382">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-382">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-383">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-383">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-384">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-384">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="2cce5-385">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2cce5-385">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-386">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-386">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="2cce5-387">NUnit</span><span class="sxs-lookup"><span data-stu-id="2cce5-387">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-388">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-388">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="2cce5-389">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-389">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-390">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-390">SDK version</span></span> | <span data-ttu-id="2cce5-391">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-391">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-392">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-392">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-393">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-393">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2cce5-394">2.2</span><span class="sxs-lookup"><span data-stu-id="2cce5-394">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="2cce5-395">2.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-395">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="2cce5-396">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2cce5-396">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-397">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-397">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="2cce5-398">página</span><span class="sxs-lookup"><span data-stu-id="2cce5-398">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="2cce5-399">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-399">Namespace for the generated code.</span></span> <span data-ttu-id="2cce5-400">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-400">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="2cce5-401">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="2cce5-401">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="2cce5-402">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="2cce5-402">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="2cce5-403">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-403">Namespace for the generated code.</span></span> <span data-ttu-id="2cce5-404">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-404">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="2cce5-405">blazorserver</span><span class="sxs-lookup"><span data-stu-id="2cce5-405">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="2cce5-406">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-406">The type of authentication to use.</span></span> <span data-ttu-id="2cce5-407">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2cce5-407">The possible values are:</span></span>

  - <span data-ttu-id="2cce5-408">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2cce5-408">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2cce5-409">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2cce5-409">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="2cce5-410">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2cce5-410">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2cce5-411">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2cce5-411">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="2cce5-412">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2cce5-412">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="2cce5-413">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2cce5-413">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2cce5-414">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-414">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2cce5-415">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-415">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-416">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-416">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2cce5-417">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-417">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2cce5-418">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-418">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="2cce5-419">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-419">The reset password policy ID for this project.</span></span> <span data-ttu-id="2cce5-420">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-420">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="2cce5-421">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-421">The edit profile policy ID for this project.</span></span> <span data-ttu-id="2cce5-422">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-422">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2cce5-423">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-423">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2cce5-424">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-424">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2cce5-425">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-425">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2cce5-426">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-426">The Client ID for this project.</span></span> <span data-ttu-id="2cce5-427">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-427">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2cce5-428">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-428">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2cce5-429">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2cce5-429">The domain for the directory tenant.</span></span> <span data-ttu-id="2cce5-430">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-430">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-431">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-431">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2cce5-432">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-432">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2cce5-433">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-433">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2cce5-434">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-434">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="2cce5-435">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2cce5-435">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2cce5-436">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-436">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-437">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-437">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2cce5-438">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2cce5-438">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2cce5-439">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-439">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-440">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-440">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="2cce5-441">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2cce5-441">Turns off HTTPS.</span></span> <span data-ttu-id="2cce5-442">Essa opção só se aplica se `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` não estiverem sendo usados para `--auth` .</span><span class="sxs-lookup"><span data-stu-id="2cce5-442">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2cce5-443">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2cce5-443">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2cce5-444">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-444">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-445">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-445">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="2cce5-446">web</span><span class="sxs-lookup"><span data-stu-id="2cce5-446">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-447">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-447">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-448">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-448">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-449">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-449">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2cce5-450">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-450">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-451">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-451">SDK version</span></span> | <span data-ttu-id="2cce5-452">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-452">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-453">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-453">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-454">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-454">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2cce5-455">2.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-455">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="2cce5-456">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-456">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="2cce5-457">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2cce5-457">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="2cce5-458">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="2cce5-458">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="2cce5-459">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-459">The type of authentication to use.</span></span> <span data-ttu-id="2cce5-460">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2cce5-460">The possible values are:</span></span>

  - <span data-ttu-id="2cce5-461">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2cce5-461">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2cce5-462">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2cce5-462">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="2cce5-463">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2cce5-463">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2cce5-464">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2cce5-464">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="2cce5-465">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="2cce5-465">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="2cce5-466">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2cce5-466">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2cce5-467">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-467">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2cce5-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-468">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-469">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-469">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2cce5-470">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-470">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2cce5-471">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-471">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="2cce5-472">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-472">The reset password policy ID for this project.</span></span> <span data-ttu-id="2cce5-473">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-473">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="2cce5-474">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-474">The edit profile policy ID for this project.</span></span> <span data-ttu-id="2cce5-475">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-475">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2cce5-476">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-476">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2cce5-477">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-477">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="2cce5-478">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-478">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2cce5-479">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-479">The Client ID for this project.</span></span> <span data-ttu-id="2cce5-480">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-480">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="2cce5-481">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-481">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2cce5-482">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2cce5-482">The domain for the directory tenant.</span></span> <span data-ttu-id="2cce5-483">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-483">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-484">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-484">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2cce5-485">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-485">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2cce5-486">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-486">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2cce5-487">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-487">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="2cce5-488">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="2cce5-488">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="2cce5-489">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-489">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-490">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-490">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2cce5-491">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2cce5-491">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2cce5-492">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-492">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-493">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-493">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="2cce5-494">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2cce5-494">Turns off HTTPS.</span></span> <span data-ttu-id="2cce5-495">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="2cce5-495">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2cce5-496">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2cce5-496">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2cce5-497">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-497">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-498">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-498">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-499">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-499">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="2cce5-500">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-500">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-501">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-501">SDK version</span></span> | <span data-ttu-id="2cce5-502">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-502">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-503">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-503">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-504">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-504">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="2cce5-505">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-505">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="2cce5-506">Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-506">Includes BrowserLink in the project.</span></span> <span data-ttu-id="2cce5-507">Opção não disponível no SDK do .NET Core 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="2cce5-507">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="2cce5-508">Determina se o projeto está configurado para usar a [compilação de tempo de execução do Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações de depuração.</span><span class="sxs-lookup"><span data-stu-id="2cce5-508">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="2cce5-509">Opção disponível desde o SDK do 3.1.201 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2cce5-509">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="2cce5-510">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="2cce5-510">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="2cce5-511">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-511">The type of authentication to use.</span></span> <span data-ttu-id="2cce5-512">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-512">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="2cce5-513">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2cce5-513">The possible values are:</span></span>

  - <span data-ttu-id="2cce5-514">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2cce5-514">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2cce5-515">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="2cce5-515">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-516">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-516">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-517">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-517">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="2cce5-518">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2cce5-518">Turns off HTTPS.</span></span> <span data-ttu-id="2cce5-519">Essa opção se aplica somente se a autenticação for `None` .</span><span class="sxs-lookup"><span data-stu-id="2cce5-519">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2cce5-520">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2cce5-520">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2cce5-521">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-521">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-522">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-522">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-523">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-523">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-524">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-524">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2cce5-525">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-525">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-526">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-526">SDK version</span></span> | <span data-ttu-id="2cce5-527">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-527">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-528">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-528">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-529">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-529">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2cce5-530">2.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-530">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="2cce5-531">reactredux</span><span class="sxs-lookup"><span data-stu-id="2cce5-531">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-532">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-532">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-533">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-533">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-534">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-534">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2cce5-535">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-535">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-536">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-536">SDK version</span></span> | <span data-ttu-id="2cce5-537">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-537">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-538">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-538">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-539">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-539">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2cce5-540">2.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-540">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="2cce5-541">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="2cce5-542">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2cce5-542">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="2cce5-543">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="2cce5-543">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="2cce5-544">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-544">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="2cce5-545">Dá suporte à adição de páginas e exibições do Razor tradicionais, além dos componentes dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2cce5-545">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="2cce5-546">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2cce5-546">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="2cce5-547">webapi</span><span class="sxs-lookup"><span data-stu-id="2cce5-547">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="2cce5-548">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-548">The type of authentication to use.</span></span> <span data-ttu-id="2cce5-549">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="2cce5-549">The possible values are:</span></span>

  - <span data-ttu-id="2cce5-550">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="2cce5-550">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="2cce5-551">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="2cce5-551">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="2cce5-552">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="2cce5-552">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="2cce5-553">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="2cce5-553">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="2cce5-554">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-554">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="2cce5-555">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-555">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="2cce5-556">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-556">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="2cce5-557">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-557">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="2cce5-558">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-558">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="2cce5-559">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-559">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="2cce5-560">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-560">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2cce5-561">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-561">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="2cce5-562">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-562">The Client ID for this project.</span></span> <span data-ttu-id="2cce5-563">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2cce5-564">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-564">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="2cce5-565">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="2cce5-565">The domain for the directory tenant.</span></span> <span data-ttu-id="2cce5-566">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-566">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="2cce5-567">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-567">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="2cce5-568">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="2cce5-568">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="2cce5-569">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-569">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="2cce5-570">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-570">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="2cce5-571">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="2cce5-571">Allows this application read-access to the directory.</span></span> <span data-ttu-id="2cce5-572">Aplica-se somente à `SingleOrg` autenticação.</span><span class="sxs-lookup"><span data-stu-id="2cce5-572">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="2cce5-573">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="2cce5-573">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="2cce5-574">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2cce5-574">Turns off HTTPS.</span></span> <span data-ttu-id="2cce5-575">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="2cce5-575">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="2cce5-576">Essa opção só se aplica se `IndividualB2C` ou `SingleOrg` não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="2cce5-576">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="2cce5-577">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="2cce5-577">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="2cce5-578">Aplica-se somente à `IndividualB2C` autenticação.</span><span class="sxs-lookup"><span data-stu-id="2cce5-578">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2cce5-579">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="2cce5-579">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="2cce5-580">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="2cce5-580">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="2cce5-581">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="2cce5-581">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="2cce5-582">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="2cce5-582">SDK version</span></span> | <span data-ttu-id="2cce5-583">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="2cce5-583">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="2cce5-584">3.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-584">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="2cce5-585">3.0</span><span class="sxs-lookup"><span data-stu-id="2cce5-585">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="2cce5-586">2.1</span><span class="sxs-lookup"><span data-stu-id="2cce5-586">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="2cce5-587">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="2cce5-587">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="2cce5-588">globaljson</span><span class="sxs-lookup"><span data-stu-id="2cce5-588">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="2cce5-589">Especifica a versão do SDK do .NET Core a ser usada no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2cce5-589">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="2cce5-590">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2cce5-590">Examples</span></span>

- <span data-ttu-id="2cce5-591">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="2cce5-591">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="2cce5-592">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="2cce5-592">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="2cce5-593">Crie um projeto de biblioteca de classe .NET Standard no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="2cce5-593">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="2cce5-594">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="2cce5-594">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="2cce5-595">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="2cce5-595">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="2cce5-596">Listar todos os modelos disponíveis para modelos de aplicativo de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="2cce5-596">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="2cce5-597">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="2cce5-597">List all templates matching the *we* substring.</span></span> <span data-ttu-id="2cce5-598">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="2cce5-598">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="2cce5-599">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="2cce5-599">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="2cce5-600">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="2cce5-600">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="2cce5-601">Instale a versão 2,0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="2cce5-601">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="2cce5-602">Liste os modelos instalados e os detalhes sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="2cce5-602">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="2cce5-603">Crie um *global. JSON* no diretório atual definindo a versão do SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="2cce5-603">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="2cce5-604">Veja também</span><span class="sxs-lookup"><span data-stu-id="2cce5-604">See also</span></span>

- [<span data-ttu-id="2cce5-605">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="2cce5-605">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="2cce5-606">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="2cce5-606">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="2cce5-607">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="2cce5-607">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="2cce5-608">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="2cce5-608">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
