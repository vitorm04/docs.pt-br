---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 04/10/2020
ms.openlocfilehash: 1544f519f2a5f6a1a6e042c1db720eff45f5d98c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442235"
---
# <a name="dotnet-new"></a><span data-ttu-id="80873-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="80873-103">dotnet new</span></span>

<span data-ttu-id="80873-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="80873-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="80873-105">Name</span><span class="sxs-lookup"><span data-stu-id="80873-105">Name</span></span>

<span data-ttu-id="80873-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="80873-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="80873-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="80873-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="80873-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="80873-108">Description</span></span>

<span data-ttu-id="80873-109">O `dotnet new` comando cria um projeto do .NET Core ou outros artefatos com base em um modelo.</span><span class="sxs-lookup"><span data-stu-id="80873-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="80873-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="80873-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="80873-111">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="80873-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="80873-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="80873-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="80873-113">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="80873-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="80873-114">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="80873-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="80873-115">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="80873-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="80873-116">Você pode executar `dotnet new --list` ou `dotnet new -l` para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="80873-116">You can run `dotnet new --list` or `dotnet new -l` to see a list of all installed templates.</span></span> <span data-ttu-id="80873-117">Se o `TEMPLATE` valor não for uma correspondência exata no texto na coluna **modelos** ou **nome curto** da tabela retornada, uma correspondência de subcadeia de caracteres será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="80873-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="80873-118">A partir do SDK do .NET Core 3,0, a CLI procura modelos em NuGet.org quando você invoca o `dotnet new` comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="80873-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="80873-119">Se a CLI não encontrar uma correspondência de modelo ao invocar `dotnet new` , nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="80873-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="80873-120">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="80873-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="80873-121">Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="80873-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="80873-122">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80873-122">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="80873-123">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="80873-123">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="80873-124">Clique no link nome curto para ver as opções de modelo específicas.</span><span class="sxs-lookup"><span data-stu-id="80873-124">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="80873-125">Modelos</span><span class="sxs-lookup"><span data-stu-id="80873-125">Templates</span></span>                                    | <span data-ttu-id="80873-126">Nome curto</span><span class="sxs-lookup"><span data-stu-id="80873-126">Short name</span></span>                      | <span data-ttu-id="80873-127">Linguagem</span><span class="sxs-lookup"><span data-stu-id="80873-127">Language</span></span>     | <span data-ttu-id="80873-128">Marcações</span><span class="sxs-lookup"><span data-stu-id="80873-128">Tags</span></span>                                  | <span data-ttu-id="80873-129">Incluída</span><span class="sxs-lookup"><span data-stu-id="80873-129">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="80873-130">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="80873-130">Console Application</span></span>                          | [<span data-ttu-id="80873-131">MMC</span><span class="sxs-lookup"><span data-stu-id="80873-131">console</span></span>](#console)             | <span data-ttu-id="80873-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="80873-132">[C#], F#, VB</span></span> | <span data-ttu-id="80873-133">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="80873-133">Common/Console</span></span>                        | <span data-ttu-id="80873-134">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-134">1.0</span></span>        |
| <span data-ttu-id="80873-135">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="80873-135">Class library</span></span>                                | [<span data-ttu-id="80873-136">classlib</span><span class="sxs-lookup"><span data-stu-id="80873-136">classlib</span></span>](#classlib)           | <span data-ttu-id="80873-137">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="80873-137">[C#], F#, VB</span></span> | <span data-ttu-id="80873-138">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="80873-138">Common/Library</span></span>                        | <span data-ttu-id="80873-139">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-139">1.0</span></span>        |
| <span data-ttu-id="80873-140">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="80873-140">WPF Application</span></span>                              | [<span data-ttu-id="80873-141">WFP</span><span class="sxs-lookup"><span data-stu-id="80873-141">wpf</span></span>](#wpf)                     | <span data-ttu-id="80873-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-142">[C#]</span></span>         | <span data-ttu-id="80873-143">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="80873-143">Common/WPF</span></span>                            | <span data-ttu-id="80873-144">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-144">3.0</span></span>        |
| <span data-ttu-id="80873-145">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="80873-145">WPF Class library</span></span>                            | [<span data-ttu-id="80873-146">wpflib</span><span class="sxs-lookup"><span data-stu-id="80873-146">wpflib</span></span>](#wpf)                  | <span data-ttu-id="80873-147">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-147">[C#]</span></span>         | <span data-ttu-id="80873-148">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="80873-148">Common/WPF</span></span>                            | <span data-ttu-id="80873-149">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-149">3.0</span></span>        |
| <span data-ttu-id="80873-150">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="80873-150">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="80873-151">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="80873-151">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="80873-152">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-152">[C#]</span></span>         | <span data-ttu-id="80873-153">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="80873-153">Common/WPF</span></span>                            | <span data-ttu-id="80873-154">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-154">3.0</span></span>        |
| <span data-ttu-id="80873-155">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="80873-155">WPF User Control Library</span></span>                     | [<span data-ttu-id="80873-156">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="80873-156">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="80873-157">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-157">[C#]</span></span>         | <span data-ttu-id="80873-158">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="80873-158">Common/WPF</span></span>                            | <span data-ttu-id="80873-159">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-159">3.0</span></span>        |
| <span data-ttu-id="80873-160">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="80873-160">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="80873-161">WinForms</span><span class="sxs-lookup"><span data-stu-id="80873-161">winforms</span></span>](#winforms)           | <span data-ttu-id="80873-162">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-162">[C#]</span></span>         | <span data-ttu-id="80873-163">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="80873-163">Common/WinForms</span></span>                       | <span data-ttu-id="80873-164">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-164">3.0</span></span>        |
| <span data-ttu-id="80873-165">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="80873-165">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="80873-166">winformslib</span><span class="sxs-lookup"><span data-stu-id="80873-166">winformslib</span></span>](#winforms)        | <span data-ttu-id="80873-167">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-167">[C#]</span></span>         | <span data-ttu-id="80873-168">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="80873-168">Common/WinForms</span></span>                       | <span data-ttu-id="80873-169">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-169">3.0</span></span>        |
| <span data-ttu-id="80873-170">Serviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="80873-170">Worker Service</span></span>                               | [<span data-ttu-id="80873-171">funcionários</span><span class="sxs-lookup"><span data-stu-id="80873-171">worker</span></span>](#web-others)           | <span data-ttu-id="80873-172">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-172">[C#]</span></span>         | <span data-ttu-id="80873-173">Comum/de trabalho/Web</span><span class="sxs-lookup"><span data-stu-id="80873-173">Common/Worker/Web</span></span>                     | <span data-ttu-id="80873-174">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-174">3.0</span></span>        |
| <span data-ttu-id="80873-175">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="80873-175">Unit Test Project</span></span>                            | [<span data-ttu-id="80873-176">MSTest</span><span class="sxs-lookup"><span data-stu-id="80873-176">mstest</span></span>](#test)                 | <span data-ttu-id="80873-177">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="80873-177">[C#], F#, VB</span></span> | <span data-ttu-id="80873-178">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="80873-178">Test/MSTest</span></span>                           | <span data-ttu-id="80873-179">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-179">1.0</span></span>        |
| <span data-ttu-id="80873-180">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="80873-180">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="80873-181">NUnit</span><span class="sxs-lookup"><span data-stu-id="80873-181">nunit</span></span>](#nunit)                  | <span data-ttu-id="80873-182">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="80873-182">[C#], F#, VB</span></span> | <span data-ttu-id="80873-183">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="80873-183">Test/NUnit</span></span>                            | <span data-ttu-id="80873-184">2.1.400</span><span class="sxs-lookup"><span data-stu-id="80873-184">2.1.400</span></span>    |
| <span data-ttu-id="80873-185">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="80873-185">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="80873-186">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="80873-186">[C#], F#, VB</span></span> | <span data-ttu-id="80873-187">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="80873-187">Test/NUnit</span></span>                            | <span data-ttu-id="80873-188">2.2</span><span class="sxs-lookup"><span data-stu-id="80873-188">2.2</span></span>        |
| <span data-ttu-id="80873-189">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="80873-189">xUnit Test Project</span></span>                           | [<span data-ttu-id="80873-190">xUnit</span><span class="sxs-lookup"><span data-stu-id="80873-190">xunit</span></span>](#test)                  | <span data-ttu-id="80873-191">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="80873-191">[C#], F#, VB</span></span> | <span data-ttu-id="80873-192">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="80873-192">Test/xUnit</span></span>                            | <span data-ttu-id="80873-193">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-193">1.0</span></span>        |
| <span data-ttu-id="80873-194">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="80873-194">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="80873-195">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-195">[C#]</span></span>         | <span data-ttu-id="80873-196">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80873-196">Web/ASP.NET</span></span>                           | <span data-ttu-id="80873-197">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-197">3.0</span></span>        |
| <span data-ttu-id="80873-198">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="80873-198">Razor Page</span></span>                                   | [<span data-ttu-id="80873-199">Web</span><span class="sxs-lookup"><span data-stu-id="80873-199">page</span></span>](#page)                   | <span data-ttu-id="80873-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-200">[C#]</span></span>         | <span data-ttu-id="80873-201">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80873-201">Web/ASP.NET</span></span>                           | <span data-ttu-id="80873-202">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-202">2.0</span></span>        |
| <span data-ttu-id="80873-203">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="80873-203">MVC ViewImports</span></span>                              | [<span data-ttu-id="80873-204">viewimports</span><span class="sxs-lookup"><span data-stu-id="80873-204">viewimports</span></span>](#namespace)       | <span data-ttu-id="80873-205">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-205">[C#]</span></span>         | <span data-ttu-id="80873-206">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80873-206">Web/ASP.NET</span></span>                           | <span data-ttu-id="80873-207">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-207">2.0</span></span>        |
| <span data-ttu-id="80873-208">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="80873-208">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="80873-209">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-209">[C#]</span></span>         | <span data-ttu-id="80873-210">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="80873-210">Web/ASP.NET</span></span>                           | <span data-ttu-id="80873-211">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-211">2.0</span></span>        |
| <span data-ttu-id="80873-212">Aplicativo de servidor mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="80873-212">Blazor Server App</span></span>                            | [<span data-ttu-id="80873-213">blazorserver</span><span class="sxs-lookup"><span data-stu-id="80873-213">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="80873-214">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-214">[C#]</span></span>         | <span data-ttu-id="80873-215">Web/mais e mais</span><span class="sxs-lookup"><span data-stu-id="80873-215">Web/Blazor</span></span>                            | <span data-ttu-id="80873-216">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-216">3.0</span></span>        |
| <span data-ttu-id="80873-217">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="80873-217">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="80873-218">site</span><span class="sxs-lookup"><span data-stu-id="80873-218">web</span></span>](#web)                     | <span data-ttu-id="80873-219">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="80873-219">[C#], F#</span></span>     | <span data-ttu-id="80873-220">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="80873-220">Web/Empty</span></span>                             | <span data-ttu-id="80873-221">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-221">1.0</span></span>        |
| <span data-ttu-id="80873-222">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="80873-222">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="80873-223">MVC</span><span class="sxs-lookup"><span data-stu-id="80873-223">mvc</span></span>](#web-options)             | <span data-ttu-id="80873-224">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="80873-224">[C#], F#</span></span>     | <span data-ttu-id="80873-225">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="80873-225">Web/MVC</span></span>                               | <span data-ttu-id="80873-226">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-226">1.0</span></span>        |
| <span data-ttu-id="80873-227">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="80873-227">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="80873-228">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="80873-228">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="80873-229">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-229">[C#]</span></span>         | <span data-ttu-id="80873-230">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="80873-230">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="80873-231">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="80873-231">2.2, 2.0</span></span>   |
| <span data-ttu-id="80873-232">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="80873-232">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="80873-233">angular</span><span class="sxs-lookup"><span data-stu-id="80873-233">angular</span></span>](#spa)                 | <span data-ttu-id="80873-234">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-234">[C#]</span></span>         | <span data-ttu-id="80873-235">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="80873-235">Web/MVC/SPA</span></span>                           | <span data-ttu-id="80873-236">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-236">2.0</span></span>        |
| <span data-ttu-id="80873-237">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="80873-237">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="80873-238">reagir</span><span class="sxs-lookup"><span data-stu-id="80873-238">react</span></span>](#spa)                   | <span data-ttu-id="80873-239">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-239">[C#]</span></span>         | <span data-ttu-id="80873-240">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="80873-240">Web/MVC/SPA</span></span>                           | <span data-ttu-id="80873-241">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-241">2.0</span></span>        |
| <span data-ttu-id="80873-242">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="80873-242">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="80873-243">reactredux</span><span class="sxs-lookup"><span data-stu-id="80873-243">reactredux</span></span>](#reactredux)       | <span data-ttu-id="80873-244">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-244">[C#]</span></span>         | <span data-ttu-id="80873-245">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="80873-245">Web/MVC/SPA</span></span>                           | <span data-ttu-id="80873-246">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-246">2.0</span></span>        |
| <span data-ttu-id="80873-247">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="80873-247">Razor Class Library</span></span>                          | [<span data-ttu-id="80873-248">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="80873-248">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="80873-249">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-249">[C#]</span></span>         | <span data-ttu-id="80873-250">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="80873-250">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="80873-251">2.1</span><span class="sxs-lookup"><span data-stu-id="80873-251">2.1</span></span>        |
| <span data-ttu-id="80873-252">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="80873-252">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="80873-253">webAPI</span><span class="sxs-lookup"><span data-stu-id="80873-253">webapi</span></span>](#webapi)               | <span data-ttu-id="80873-254">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="80873-254">[C#], F#</span></span>     | <span data-ttu-id="80873-255">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="80873-255">Web/WebAPI</span></span>                            | <span data-ttu-id="80873-256">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-256">1.0</span></span>        |
| <span data-ttu-id="80873-257">ASP.NET Core serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="80873-257">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="80873-258">grpc</span><span class="sxs-lookup"><span data-stu-id="80873-258">grpc</span></span>](#web-others)             | <span data-ttu-id="80873-259">[C#]</span><span class="sxs-lookup"><span data-stu-id="80873-259">[C#]</span></span>         | <span data-ttu-id="80873-260">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="80873-260">Web/gRPC</span></span>                              | <span data-ttu-id="80873-261">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-261">3.0</span></span>        |
| <span data-ttu-id="80873-262">arquivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="80873-262">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="80873-263">Config</span><span class="sxs-lookup"><span data-stu-id="80873-263">Config</span></span>                                | <span data-ttu-id="80873-264">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-264">3.0</span></span>        |
| <span data-ttu-id="80873-265">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="80873-265">global.json file</span></span>                             | [<span data-ttu-id="80873-266">globaljson</span><span class="sxs-lookup"><span data-stu-id="80873-266">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="80873-267">Config</span><span class="sxs-lookup"><span data-stu-id="80873-267">Config</span></span>                                | <span data-ttu-id="80873-268">2.0</span><span class="sxs-lookup"><span data-stu-id="80873-268">2.0</span></span>        |
| <span data-ttu-id="80873-269">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="80873-269">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="80873-270">Config</span><span class="sxs-lookup"><span data-stu-id="80873-270">Config</span></span>                                | <span data-ttu-id="80873-271">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-271">1.0</span></span>        |
| <span data-ttu-id="80873-272">Arquivo de manifesto da ferramenta local dotnet</span><span class="sxs-lookup"><span data-stu-id="80873-272">Dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="80873-273">Config</span><span class="sxs-lookup"><span data-stu-id="80873-273">Config</span></span>                                | <span data-ttu-id="80873-274">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-274">3.0</span></span>        |
| <span data-ttu-id="80873-275">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="80873-275">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="80873-276">Config</span><span class="sxs-lookup"><span data-stu-id="80873-276">Config</span></span>                                | <span data-ttu-id="80873-277">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-277">1.0</span></span>        |
| <span data-ttu-id="80873-278">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="80873-278">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="80873-279">Solução</span><span class="sxs-lookup"><span data-stu-id="80873-279">Solution</span></span>                              | <span data-ttu-id="80873-280">1.0</span><span class="sxs-lookup"><span data-stu-id="80873-280">1.0</span></span>        |
| <span data-ttu-id="80873-281">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="80873-281">Protocol Buffer File</span></span>                         | [<span data-ttu-id="80873-282">proto</span><span class="sxs-lookup"><span data-stu-id="80873-282">proto</span></span>](#namespace)             |              | <span data-ttu-id="80873-283">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="80873-283">Web/gRPC</span></span>                              | <span data-ttu-id="80873-284">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-284">3.0</span></span>        |

## <a name="options"></a><span data-ttu-id="80873-285">Opções</span><span class="sxs-lookup"><span data-stu-id="80873-285">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="80873-286">Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="80873-286">Displays a summary of what would happen if the given command were run if it would result in a template creation.</span></span> <span data-ttu-id="80873-287">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-287">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="80873-288">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="80873-288">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="80873-289">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="80873-289">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="80873-290">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="80873-290">Prints out help for the command.</span></span> <span data-ttu-id="80873-291">Ele pode ser invocado para o `dotnet new` próprio comando ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="80873-291">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="80873-292">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="80873-292">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="80873-293">Instala um pacote de modelos do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="80873-293">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="80873-294">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="80873-294">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="80873-295">Por padrão, `dotnet new` \* o passa para a versão, que representa a versão de pacote estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="80873-295">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="80873-296">Veja um exemplo na seção [exemplos](#examples) .</span><span class="sxs-lookup"><span data-stu-id="80873-296">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="80873-297">Se uma versão do modelo já tiver sido instalada quando você executar esse comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="80873-297">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="80873-298">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="80873-298">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="80873-299">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="80873-299">Lists templates containing the specified name.</span></span> <span data-ttu-id="80873-300">Se nenhum nome for especificado, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="80873-300">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="80873-301">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="80873-301">The language of the template to create.</span></span> <span data-ttu-id="80873-302">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="80873-302">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="80873-303">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="80873-303">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="80873-304">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="80873-304">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="80873-305">Nesses casos, coloque o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="80873-305">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="80873-306">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="80873-306">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="80873-307">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="80873-307">The name for the created output.</span></span> <span data-ttu-id="80873-308">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="80873-308">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="80873-309">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="80873-309">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="80873-310">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="80873-310">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="80873-311">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="80873-311">Location to place the generated output.</span></span> <span data-ttu-id="80873-312">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="80873-312">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="80873-313">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="80873-313">Filters templates based on available types.</span></span> <span data-ttu-id="80873-314">Os valores predefinidos são `project` , `item` e `other` .</span><span class="sxs-lookup"><span data-stu-id="80873-314">Predefined values are `project`, `item`, and `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="80873-315">Desinstala um pacote de modelos no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="80873-315">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="80873-316">Quando o `<PATH|NUGET_ID>` valor não for especificado, todos os pacotes de modelos instalados atualmente e seus modelos associados serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="80873-316">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="80873-317">Ao especificar `NUGET_ID` , não inclua o número de versão.</span><span class="sxs-lookup"><span data-stu-id="80873-317">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="80873-318">Se você não especificar um parâmetro para essa opção, o comando listará os modelos instalados e os detalhes sobre eles.</span><span class="sxs-lookup"><span data-stu-id="80873-318">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="80873-319">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="80873-319">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="80873-320">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="80873-320">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="80873-321">Não inclua uma barra de diretório final de encerramento no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="80873-321">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="80873-322">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="80873-322">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="80873-323">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="80873-323">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="80873-324">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="80873-324">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="80873-325">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="80873-325">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="80873-326">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="80873-326">Template options</span></span>

<span data-ttu-id="80873-327">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="80873-327">Each project template may have additional options available.</span></span> <span data-ttu-id="80873-328">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="80873-328">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="80873-329">console</span><span class="sxs-lookup"><span data-stu-id="80873-329">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-330">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-330">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-331">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="80873-331">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="80873-332">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-332">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-333">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-333">SDK version</span></span> | <span data-ttu-id="80873-334">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-334">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-335">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-335">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-336">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-336">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="80873-337">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="80873-337">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="80873-338">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="80873-338">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="80873-339">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="80873-339">Not supported for F#.</span></span> <span data-ttu-id="80873-340">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-340">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="80873-341">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="80873-341">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-342">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-342">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="80873-343">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-343">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="80873-344">classlib</span><span class="sxs-lookup"><span data-stu-id="80873-344">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-345">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-345">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-346">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="80873-346">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="80873-347">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="80873-347">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="80873-348">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="80873-348">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="80873-349">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="80873-349">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="80873-350">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="80873-350">Not supported for F#.</span></span> <span data-ttu-id="80873-351">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-351">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="80873-352">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="80873-352">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-353">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-353">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="80873-354">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="80873-354">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-355">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-355">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-356">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="80873-356">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="80873-357">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="80873-357">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="80873-358">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="80873-358">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="80873-359">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="80873-359">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="80873-360">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="80873-360">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-361">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-361">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="80873-362">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="80873-362">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="80873-363">Define a `LangVersion` propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="80873-363">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="80873-364">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="80873-364">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="80873-365">Para obter uma lista de versões padrão do C#, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="80873-365">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-366">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-366">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="80873-367">trabalho, grpc</span><span class="sxs-lookup"><span data-stu-id="80873-367">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-368">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-368">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-369">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="80873-369">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="80873-370">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="80873-370">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-371">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-371">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-372">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-372">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="80873-373">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="80873-373">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-374">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-374">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-375">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="80873-375">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="80873-376">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-376">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-377">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-377">SDK version</span></span> | <span data-ttu-id="80873-378">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-378">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-379">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-379">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-380">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-380">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="80873-381">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="80873-381">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-382">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-382">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="80873-383">NUnit</span><span class="sxs-lookup"><span data-stu-id="80873-383">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-384">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-384">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="80873-385">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-385">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-386">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-386">SDK version</span></span> | <span data-ttu-id="80873-387">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-387">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-388">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-388">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-389">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-389">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="80873-390">2.2</span><span class="sxs-lookup"><span data-stu-id="80873-390">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="80873-391">2.1</span><span class="sxs-lookup"><span data-stu-id="80873-391">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="80873-392">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="80873-392">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-393">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-393">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="80873-394">página</span><span class="sxs-lookup"><span data-stu-id="80873-394">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="80873-395">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-395">Namespace for the generated code.</span></span> <span data-ttu-id="80873-396">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="80873-396">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="80873-397">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="80873-397">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="80873-398">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="80873-398">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="80873-399">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-399">Namespace for the generated code.</span></span> <span data-ttu-id="80873-400">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="80873-400">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="80873-401">blazorserver</span><span class="sxs-lookup"><span data-stu-id="80873-401">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="80873-402">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="80873-402">The type of authentication to use.</span></span> <span data-ttu-id="80873-403">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="80873-403">The possible values are:</span></span>

  - <span data-ttu-id="80873-404">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="80873-404">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="80873-405">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="80873-405">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="80873-406">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="80873-406">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="80873-407">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="80873-407">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="80873-408">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="80873-408">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="80873-409">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="80873-409">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="80873-410">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-410">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="80873-411">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-412">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="80873-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="80873-413">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-413">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="80873-414">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-414">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="80873-415">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-415">The reset password policy ID for this project.</span></span> <span data-ttu-id="80873-416">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-416">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="80873-417">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-417">The edit profile policy ID for this project.</span></span> <span data-ttu-id="80873-418">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-418">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="80873-419">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-419">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="80873-420">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-420">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="80873-421">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="80873-421">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="80873-422">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-422">The Client ID for this project.</span></span> <span data-ttu-id="80873-423">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-423">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="80873-424">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="80873-424">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="80873-425">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="80873-425">The domain for the directory tenant.</span></span> <span data-ttu-id="80873-426">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-426">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-427">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="80873-427">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="80873-428">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-428">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="80873-429">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-429">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="80873-430">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="80873-430">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="80873-431">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="80873-431">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="80873-432">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-432">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-433">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="80873-433">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="80873-434">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="80873-434">Allows this application read-access to the directory.</span></span> <span data-ttu-id="80873-435">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-435">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-436">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-436">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="80873-437">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80873-437">Turns off HTTPS.</span></span> <span data-ttu-id="80873-438">Essa opção só se aplica se `Individual` , `IndividualB2C` , `SingleOrg` ou `MultiOrg` não estiverem sendo usados para `--auth` .</span><span class="sxs-lookup"><span data-stu-id="80873-438">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="80873-439">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="80873-439">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="80873-440">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-440">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-441">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-441">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="80873-442">web</span><span class="sxs-lookup"><span data-stu-id="80873-442">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-443">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-443">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-444">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-444">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-445">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-445">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="80873-446">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-446">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-447">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-447">SDK version</span></span> | <span data-ttu-id="80873-448">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-448">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-449">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-449">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-450">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-450">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="80873-451">2.1</span><span class="sxs-lookup"><span data-stu-id="80873-451">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="80873-452">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-452">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="80873-453">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80873-453">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="80873-454">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="80873-454">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="80873-455">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="80873-455">The type of authentication to use.</span></span> <span data-ttu-id="80873-456">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="80873-456">The possible values are:</span></span>

  - <span data-ttu-id="80873-457">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="80873-457">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="80873-458">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="80873-458">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="80873-459">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="80873-459">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="80873-460">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="80873-460">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="80873-461">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="80873-461">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="80873-462">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="80873-462">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="80873-463">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-463">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="80873-464">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-464">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-465">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="80873-465">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="80873-466">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-466">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="80873-467">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-467">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="80873-468">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-468">The reset password policy ID for this project.</span></span> <span data-ttu-id="80873-469">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-469">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="80873-470">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-470">The edit profile policy ID for this project.</span></span> <span data-ttu-id="80873-471">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-471">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="80873-472">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-472">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="80873-473">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-473">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="80873-474">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="80873-474">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="80873-475">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-475">The Client ID for this project.</span></span> <span data-ttu-id="80873-476">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-476">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="80873-477">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="80873-477">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="80873-478">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="80873-478">The domain for the directory tenant.</span></span> <span data-ttu-id="80873-479">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-479">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-480">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="80873-480">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="80873-481">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-481">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="80873-482">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-482">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="80873-483">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="80873-483">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="80873-484">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="80873-484">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="80873-485">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-485">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-486">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="80873-486">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="80873-487">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="80873-487">Allows this application read-access to the directory.</span></span> <span data-ttu-id="80873-488">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-488">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-489">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-489">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="80873-490">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80873-490">Turns off HTTPS.</span></span> <span data-ttu-id="80873-491">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="80873-491">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="80873-492">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="80873-492">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="80873-493">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-493">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-494">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-494">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-495">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="80873-495">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="80873-496">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-496">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-497">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-497">SDK version</span></span> | <span data-ttu-id="80873-498">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-498">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-499">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-499">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-500">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-500">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="80873-501">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-501">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="80873-502">Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-502">Includes BrowserLink in the project.</span></span> <span data-ttu-id="80873-503">Opção não disponível no SDK do .NET Core 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="80873-503">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="80873-504">Determina se o projeto está configurado para usar a [compilação de tempo de execução do Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações de depuração.</span><span class="sxs-lookup"><span data-stu-id="80873-504">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="80873-505">Opção disponível desde o SDK do 3.1.201 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80873-505">Option available since .NET Core 3.1.201 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="80873-506">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="80873-506">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="80873-507">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="80873-507">The type of authentication to use.</span></span> <span data-ttu-id="80873-508">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="80873-508">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="80873-509">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="80873-509">The possible values are:</span></span>

  - <span data-ttu-id="80873-510">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="80873-510">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="80873-511">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="80873-511">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-512">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-512">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-513">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-513">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="80873-514">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80873-514">Turns off HTTPS.</span></span> <span data-ttu-id="80873-515">Essa opção se aplica somente se a autenticação for `None` .</span><span class="sxs-lookup"><span data-stu-id="80873-515">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="80873-516">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="80873-516">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="80873-517">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-517">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-518">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="80873-518">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-519">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-519">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-520">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-520">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="80873-521">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-521">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-522">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-522">SDK version</span></span> | <span data-ttu-id="80873-523">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-523">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-524">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-524">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-525">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-525">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="80873-526">2.1</span><span class="sxs-lookup"><span data-stu-id="80873-526">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="80873-527">reactredux</span><span class="sxs-lookup"><span data-stu-id="80873-527">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-528">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-528">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-529">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-529">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-530">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-530">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="80873-531">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-531">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-532">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-532">SDK version</span></span> | <span data-ttu-id="80873-533">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-533">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-534">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-534">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-535">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-535">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="80873-536">2.1</span><span class="sxs-lookup"><span data-stu-id="80873-536">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="80873-537">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-537">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="80873-538">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80873-538">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="80873-539">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="80873-539">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="80873-540">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-540">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="80873-541">Dá suporte à adição de páginas e exibições do Razor tradicionais, além dos componentes dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="80873-541">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="80873-542">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="80873-542">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="80873-543">webapi</span><span class="sxs-lookup"><span data-stu-id="80873-543">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="80873-544">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="80873-544">The type of authentication to use.</span></span> <span data-ttu-id="80873-545">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="80873-545">The possible values are:</span></span>

  - <span data-ttu-id="80873-546">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="80873-546">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="80873-547">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="80873-547">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="80873-548">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="80873-548">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="80873-549">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="80873-549">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="80873-550">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-550">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="80873-551">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-551">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="80873-552">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="80873-552">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="80873-553">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-553">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="80873-554">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="80873-554">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="80873-555">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-555">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="80873-556">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-556">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="80873-557">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="80873-557">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="80873-558">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-558">The Client ID for this project.</span></span> <span data-ttu-id="80873-559">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-559">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="80873-560">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="80873-560">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="80873-561">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="80873-561">The domain for the directory tenant.</span></span> <span data-ttu-id="80873-562">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-562">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="80873-563">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="80873-563">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="80873-564">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="80873-564">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="80873-565">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="80873-565">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="80873-566">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="80873-566">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="80873-567">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="80873-567">Allows this application read-access to the directory.</span></span> <span data-ttu-id="80873-568">Aplica-se somente à `SingleOrg` autenticação.</span><span class="sxs-lookup"><span data-stu-id="80873-568">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="80873-569">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="80873-569">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="80873-570">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="80873-570">Turns off HTTPS.</span></span> <span data-ttu-id="80873-571">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="80873-571">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="80873-572">Essa opção só se aplica se `IndividualB2C` ou `SingleOrg` não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="80873-572">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="80873-573">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="80873-573">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="80873-574">Aplica-se somente à `IndividualB2C` autenticação.</span><span class="sxs-lookup"><span data-stu-id="80873-574">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="80873-575">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="80873-575">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="80873-576">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="80873-576">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="80873-577">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="80873-577">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="80873-578">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="80873-578">SDK version</span></span> | <span data-ttu-id="80873-579">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="80873-579">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="80873-580">3.1</span><span class="sxs-lookup"><span data-stu-id="80873-580">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="80873-581">3.0</span><span class="sxs-lookup"><span data-stu-id="80873-581">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="80873-582">2.1</span><span class="sxs-lookup"><span data-stu-id="80873-582">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="80873-583">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="80873-583">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="80873-584">globaljson</span><span class="sxs-lookup"><span data-stu-id="80873-584">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="80873-585">Especifica a versão do SDK do .NET Core a ser usada no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="80873-585">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="80873-586">Exemplos</span><span class="sxs-lookup"><span data-stu-id="80873-586">Examples</span></span>

- <span data-ttu-id="80873-587">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="80873-587">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="80873-588">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="80873-588">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- <span data-ttu-id="80873-589">Crie um projeto de biblioteca de classe .NET Standard no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="80873-589">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="80873-590">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="80873-590">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="80873-591">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="80873-591">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="80873-592">Listar todos os modelos disponíveis para modelos de aplicativo de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="80873-592">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="80873-593">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="80873-593">List all templates matching the *we* substring.</span></span> <span data-ttu-id="80873-594">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="80873-594">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="80873-595">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="80873-595">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="80873-596">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="80873-596">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="80873-597">Instale a versão 2,0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="80873-597">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="80873-598">Liste os modelos instalados e os detalhes sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="80873-598">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="80873-599">Crie um *global. JSON* no diretório atual definindo a versão do SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="80873-599">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="80873-600">Confira também</span><span class="sxs-lookup"><span data-stu-id="80873-600">See also</span></span>

- [<span data-ttu-id="80873-601">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="80873-601">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="80873-602">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="80873-602">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="80873-603">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="80873-603">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="80873-604">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="80873-604">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
