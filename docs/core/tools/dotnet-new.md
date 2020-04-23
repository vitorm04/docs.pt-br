---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 04/10/2020
ms.openlocfilehash: 1979f98a6005a414acc64c5eaa086a88aca9f033
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102821"
---
# <a name="dotnet-new"></a><span data-ttu-id="d2239-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2239-103">dotnet new</span></span>

<span data-ttu-id="d2239-104">**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d2239-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d2239-105">Nome</span><span class="sxs-lookup"><span data-stu-id="d2239-105">Name</span></span>

<span data-ttu-id="d2239-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d2239-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2239-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d2239-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="d2239-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2239-108">Description</span></span>

<span data-ttu-id="d2239-109">O `dotnet new` comando cria um projeto .NET Core ou outros artefatos baseados em um modelo.</span><span class="sxs-lookup"><span data-stu-id="d2239-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="d2239-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="d2239-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="d2239-111">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="d2239-111">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="d2239-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d2239-112">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="d2239-113">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="d2239-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="d2239-114">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="d2239-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="d2239-115">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="d2239-115">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="d2239-116">Você pode `dotnet new --list` correr para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="d2239-116">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="d2239-117">Se `TEMPLATE` o valor não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto** da tabela retornada, uma correspondência de substring será realizada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="d2239-117">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="d2239-118">Começando com o .NET Core 3.0 SDK, a CLI `dotnet new` procura modelos em NuGet.org quando você invoca o comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="d2239-118">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="d2239-119">Se a CLI não conseguir encontrar uma `dotnet new`correspondência de modelo ao invocar, nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="d2239-119">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="d2239-120">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="d2239-120">If there's a newer version of the template available.</span></span> <span data-ttu-id="d2239-121">Neste caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="d2239-121">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="d2239-122">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d2239-122">The command contains a default list of templates.</span></span> <span data-ttu-id="d2239-123">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2239-123">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="d2239-124">A tabela a seguir mostra os modelos que vêm pré-instalados com o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-124">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="d2239-125">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d2239-125">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="d2239-126">Clique no link nome curto para ver as opções específicas de modelo.</span><span class="sxs-lookup"><span data-stu-id="d2239-126">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="d2239-127">Modelos</span><span class="sxs-lookup"><span data-stu-id="d2239-127">Templates</span></span>                                    | <span data-ttu-id="d2239-128">Nome curto</span><span class="sxs-lookup"><span data-stu-id="d2239-128">Short name</span></span>                      | <span data-ttu-id="d2239-129">Linguagem</span><span class="sxs-lookup"><span data-stu-id="d2239-129">Language</span></span>     | <span data-ttu-id="d2239-130">Marcas</span><span class="sxs-lookup"><span data-stu-id="d2239-130">Tags</span></span>                                  | <span data-ttu-id="d2239-131">Introduzido</span><span class="sxs-lookup"><span data-stu-id="d2239-131">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="d2239-132">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="d2239-132">Console Application</span></span>                          | [<span data-ttu-id="d2239-133">Console</span><span class="sxs-lookup"><span data-stu-id="d2239-133">console</span></span>](#console)             | <span data-ttu-id="d2239-134">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2239-134">[C#], F#, VB</span></span> | <span data-ttu-id="d2239-135">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="d2239-135">Common/Console</span></span>                        | <span data-ttu-id="d2239-136">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-136">1.0</span></span>        |
| <span data-ttu-id="d2239-137">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d2239-137">Class library</span></span>                                | [<span data-ttu-id="d2239-138">classlib</span><span class="sxs-lookup"><span data-stu-id="d2239-138">classlib</span></span>](#classlib)           | <span data-ttu-id="d2239-139">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2239-139">[C#], F#, VB</span></span> | <span data-ttu-id="d2239-140">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="d2239-140">Common/Library</span></span>                        | <span data-ttu-id="d2239-141">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-141">1.0</span></span>        |
| <span data-ttu-id="d2239-142">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-142">WPF Application</span></span>                              | [<span data-ttu-id="d2239-143">Wpf</span><span class="sxs-lookup"><span data-stu-id="d2239-143">wpf</span></span>](#wpf)                     | <span data-ttu-id="d2239-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-144">[C#]</span></span>         | <span data-ttu-id="d2239-145">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-145">Common/WPF</span></span>                            | <span data-ttu-id="d2239-146">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-146">3.0</span></span>        |
| <span data-ttu-id="d2239-147">Biblioteca de classe WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-147">WPF Class library</span></span>                            | [<span data-ttu-id="d2239-148">wpflib</span><span class="sxs-lookup"><span data-stu-id="d2239-148">wpflib</span></span>](#wpf)                  | <span data-ttu-id="d2239-149">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-149">[C#]</span></span>         | <span data-ttu-id="d2239-150">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-150">Common/WPF</span></span>                            | <span data-ttu-id="d2239-151">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-151">3.0</span></span>        |
| <span data-ttu-id="d2239-152">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-152">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="d2239-153">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="d2239-153">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="d2239-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-154">[C#]</span></span>         | <span data-ttu-id="d2239-155">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-155">Common/WPF</span></span>                            | <span data-ttu-id="d2239-156">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-156">3.0</span></span>        |
| <span data-ttu-id="d2239-157">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-157">WPF User Control Library</span></span>                     | [<span data-ttu-id="d2239-158">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d2239-158">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="d2239-159">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-159">[C#]</span></span>         | <span data-ttu-id="d2239-160">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2239-160">Common/WPF</span></span>                            | <span data-ttu-id="d2239-161">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-161">3.0</span></span>        |
| <span data-ttu-id="d2239-162">Aplicativo Formulários do Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="d2239-162">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="d2239-163">Winforms</span><span class="sxs-lookup"><span data-stu-id="d2239-163">winforms</span></span>](#winforms)           | <span data-ttu-id="d2239-164">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-164">[C#]</span></span>         | <span data-ttu-id="d2239-165">Formas comuns/winforms</span><span class="sxs-lookup"><span data-stu-id="d2239-165">Common/WinForms</span></span>                       | <span data-ttu-id="d2239-166">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-166">3.0</span></span>        |
| <span data-ttu-id="d2239-167">Biblioteca de classes de Formulários do Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="d2239-167">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="d2239-168">winformslib</span><span class="sxs-lookup"><span data-stu-id="d2239-168">winformslib</span></span>](#winforms)        | <span data-ttu-id="d2239-169">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-169">[C#]</span></span>         | <span data-ttu-id="d2239-170">Formas comuns/winforms</span><span class="sxs-lookup"><span data-stu-id="d2239-170">Common/WinForms</span></span>                       | <span data-ttu-id="d2239-171">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-171">3.0</span></span>        |
| <span data-ttu-id="d2239-172">Serviço ao Trabalhador</span><span class="sxs-lookup"><span data-stu-id="d2239-172">Worker Service</span></span>                               | [<span data-ttu-id="d2239-173">Trabalhador</span><span class="sxs-lookup"><span data-stu-id="d2239-173">worker</span></span>](#web-others)           | <span data-ttu-id="d2239-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-174">[C#]</span></span>         | <span data-ttu-id="d2239-175">Comum/Trabalhador/Web</span><span class="sxs-lookup"><span data-stu-id="d2239-175">Common/Worker/Web</span></span>                     | <span data-ttu-id="d2239-176">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-176">3.0</span></span>        |
| <span data-ttu-id="d2239-177">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="d2239-177">Unit Test Project</span></span>                            | [<span data-ttu-id="d2239-178">Mstest</span><span class="sxs-lookup"><span data-stu-id="d2239-178">mstest</span></span>](#test)                 | <span data-ttu-id="d2239-179">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2239-179">[C#], F#, VB</span></span> | <span data-ttu-id="d2239-180">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="d2239-180">Test/MSTest</span></span>                           | <span data-ttu-id="d2239-181">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-181">1.0</span></span>        |
| <span data-ttu-id="d2239-182">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="d2239-182">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="d2239-183">Nunit</span><span class="sxs-lookup"><span data-stu-id="d2239-183">nunit</span></span>](#nunit)                  | <span data-ttu-id="d2239-184">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2239-184">[C#], F#, VB</span></span> | <span data-ttu-id="d2239-185">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="d2239-185">Test/NUnit</span></span>                            | <span data-ttu-id="d2239-186">2.1.400</span><span class="sxs-lookup"><span data-stu-id="d2239-186">2.1.400</span></span>    |
| <span data-ttu-id="d2239-187">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="d2239-187">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="d2239-188">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2239-188">[C#], F#, VB</span></span> | <span data-ttu-id="d2239-189">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="d2239-189">Test/NUnit</span></span>                            | <span data-ttu-id="d2239-190">2.2</span><span class="sxs-lookup"><span data-stu-id="d2239-190">2.2</span></span>        |
| <span data-ttu-id="d2239-191">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="d2239-191">xUnit Test Project</span></span>                           | [<span data-ttu-id="d2239-192">Xunit</span><span class="sxs-lookup"><span data-stu-id="d2239-192">xunit</span></span>](#test)                  | <span data-ttu-id="d2239-193">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2239-193">[C#], F#, VB</span></span> | <span data-ttu-id="d2239-194">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="d2239-194">Test/xUnit</span></span>                            | <span data-ttu-id="d2239-195">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-195">1.0</span></span>        |
| <span data-ttu-id="d2239-196">Componente da navalha</span><span class="sxs-lookup"><span data-stu-id="d2239-196">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="d2239-197">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-197">[C#]</span></span>         | <span data-ttu-id="d2239-198">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2239-198">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2239-199">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-199">3.0</span></span>        |
| <span data-ttu-id="d2239-200">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="d2239-200">Razor Page</span></span>                                   | [<span data-ttu-id="d2239-201">Página</span><span class="sxs-lookup"><span data-stu-id="d2239-201">page</span></span>](#page)                   | <span data-ttu-id="d2239-202">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-202">[C#]</span></span>         | <span data-ttu-id="d2239-203">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2239-203">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2239-204">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-204">2.0</span></span>        |
| <span data-ttu-id="d2239-205">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="d2239-205">MVC ViewImports</span></span>                              | [<span data-ttu-id="d2239-206">verimportações</span><span class="sxs-lookup"><span data-stu-id="d2239-206">viewimports</span></span>](#namespace)       | <span data-ttu-id="d2239-207">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-207">[C#]</span></span>         | <span data-ttu-id="d2239-208">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2239-208">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2239-209">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-209">2.0</span></span>        |
| <span data-ttu-id="d2239-210">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d2239-210">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="d2239-211">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-211">[C#]</span></span>         | <span data-ttu-id="d2239-212">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2239-212">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2239-213">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-213">2.0</span></span>        |
| <span data-ttu-id="d2239-214">Aplicativo Blazor Server</span><span class="sxs-lookup"><span data-stu-id="d2239-214">Blazor Server App</span></span>                            | [<span data-ttu-id="d2239-215">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d2239-215">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="d2239-216">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-216">[C#]</span></span>         | <span data-ttu-id="d2239-217">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="d2239-217">Web/Blazor</span></span>                            | <span data-ttu-id="d2239-218">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-218">3.0</span></span>        |
| <span data-ttu-id="d2239-219">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="d2239-219">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="d2239-220">Web</span><span class="sxs-lookup"><span data-stu-id="d2239-220">web</span></span>](#web)                     | <span data-ttu-id="d2239-221">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d2239-221">[C#], F#</span></span>     | <span data-ttu-id="d2239-222">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="d2239-222">Web/Empty</span></span>                             | <span data-ttu-id="d2239-223">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-223">1.0</span></span>        |
| <span data-ttu-id="d2239-224">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="d2239-224">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="d2239-225">Mvc</span><span class="sxs-lookup"><span data-stu-id="d2239-225">mvc</span></span>](#web-options)             | <span data-ttu-id="d2239-226">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d2239-226">[C#], F#</span></span>     | <span data-ttu-id="d2239-227">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="d2239-227">Web/MVC</span></span>                               | <span data-ttu-id="d2239-228">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-228">1.0</span></span>        |
| <span data-ttu-id="d2239-229">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2239-229">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="d2239-230">webapp, navalha</span><span class="sxs-lookup"><span data-stu-id="d2239-230">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="d2239-231">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-231">[C#]</span></span>         | <span data-ttu-id="d2239-232">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="d2239-232">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="d2239-233">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="d2239-233">2.2, 2.0</span></span>   |
| <span data-ttu-id="d2239-234">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="d2239-234">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="d2239-235">angular</span><span class="sxs-lookup"><span data-stu-id="d2239-235">angular</span></span>](#spa)                 | <span data-ttu-id="d2239-236">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-236">[C#]</span></span>         | <span data-ttu-id="d2239-237">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2239-237">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2239-238">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-238">2.0</span></span>        |
| <span data-ttu-id="d2239-239">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="d2239-239">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="d2239-240">Reagir</span><span class="sxs-lookup"><span data-stu-id="d2239-240">react</span></span>](#spa)                   | <span data-ttu-id="d2239-241">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-241">[C#]</span></span>         | <span data-ttu-id="d2239-242">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2239-242">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2239-243">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-243">2.0</span></span>        |
| <span data-ttu-id="d2239-244">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="d2239-244">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="d2239-245">reactredux</span><span class="sxs-lookup"><span data-stu-id="d2239-245">reactredux</span></span>](#reactredux)       | <span data-ttu-id="d2239-246">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-246">[C#]</span></span>         | <span data-ttu-id="d2239-247">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2239-247">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2239-248">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-248">2.0</span></span>        |
| <span data-ttu-id="d2239-249">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="d2239-249">Razor Class Library</span></span>                          | [<span data-ttu-id="d2239-250">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d2239-250">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="d2239-251">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-251">[C#]</span></span>         | <span data-ttu-id="d2239-252">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="d2239-252">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="d2239-253">2.1</span><span class="sxs-lookup"><span data-stu-id="d2239-253">2.1</span></span>        |
| <span data-ttu-id="d2239-254">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2239-254">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="d2239-255">webapi</span><span class="sxs-lookup"><span data-stu-id="d2239-255">webapi</span></span>](#webapi)               | <span data-ttu-id="d2239-256">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d2239-256">[C#], F#</span></span>     | <span data-ttu-id="d2239-257">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="d2239-257">Web/WebAPI</span></span>                            | <span data-ttu-id="d2239-258">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-258">1.0</span></span>        |
| <span data-ttu-id="d2239-259">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="d2239-259">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="d2239-260">grpc</span><span class="sxs-lookup"><span data-stu-id="d2239-260">grpc</span></span>](#web-others)             | <span data-ttu-id="d2239-261">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2239-261">[C#]</span></span>         | <span data-ttu-id="d2239-262">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d2239-262">Web/gRPC</span></span>                              | <span data-ttu-id="d2239-263">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-263">3.0</span></span>        |
| <span data-ttu-id="d2239-264">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="d2239-264">Protocol Buffer File</span></span>                         | [<span data-ttu-id="d2239-265">Proto</span><span class="sxs-lookup"><span data-stu-id="d2239-265">proto</span></span>](#namespace)             |              | <span data-ttu-id="d2239-266">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d2239-266">Web/gRPC</span></span>                              | <span data-ttu-id="d2239-267">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-267">3.0</span></span>        |
| <span data-ttu-id="d2239-268">dotnet arquivo gitignore</span><span class="sxs-lookup"><span data-stu-id="d2239-268">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="d2239-269">Config</span><span class="sxs-lookup"><span data-stu-id="d2239-269">Config</span></span>                                | <span data-ttu-id="d2239-270">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-270">3.0</span></span>        |
| <span data-ttu-id="d2239-271">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="d2239-271">global.json file</span></span>                             | [<span data-ttu-id="d2239-272">globaljson</span><span class="sxs-lookup"><span data-stu-id="d2239-272">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="d2239-273">Config</span><span class="sxs-lookup"><span data-stu-id="d2239-273">Config</span></span>                                | <span data-ttu-id="d2239-274">2,0</span><span class="sxs-lookup"><span data-stu-id="d2239-274">2.0</span></span>        |
| <span data-ttu-id="d2239-275">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d2239-275">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="d2239-276">Config</span><span class="sxs-lookup"><span data-stu-id="d2239-276">Config</span></span>                                | <span data-ttu-id="d2239-277">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-277">1.0</span></span>        |
| <span data-ttu-id="d2239-278">dotnet arquivo manifesto ferramenta local</span><span class="sxs-lookup"><span data-stu-id="d2239-278">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="d2239-279">Config</span><span class="sxs-lookup"><span data-stu-id="d2239-279">Config</span></span>                                | <span data-ttu-id="d2239-280">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-280">3.0</span></span>        |
| <span data-ttu-id="d2239-281">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d2239-281">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="d2239-282">Config</span><span class="sxs-lookup"><span data-stu-id="d2239-282">Config</span></span>                                | <span data-ttu-id="d2239-283">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-283">1.0</span></span>        |
| <span data-ttu-id="d2239-284">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="d2239-284">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="d2239-285">Solução</span><span class="sxs-lookup"><span data-stu-id="d2239-285">Solution</span></span>                              | <span data-ttu-id="d2239-286">1.0</span><span class="sxs-lookup"><span data-stu-id="d2239-286">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="d2239-287">Opções</span><span class="sxs-lookup"><span data-stu-id="d2239-287">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="d2239-288">Exibe um resumo do que aconteceria se o comando dado fosse executado.</span><span class="sxs-lookup"><span data-stu-id="d2239-288">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="d2239-289">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-289">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="d2239-290">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="d2239-290">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d2239-291">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="d2239-291">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d2239-292">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d2239-292">Prints out help for the command.</span></span> <span data-ttu-id="d2239-293">Ele pode ser invocado para o `dotnet new` comando em si ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="d2239-293">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="d2239-294">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d2239-294">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="d2239-295">Instala um pacote de `PATH` `NUGET_ID` modelo si mesmo ou fornecido.</span><span class="sxs-lookup"><span data-stu-id="d2239-295">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d2239-296">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="d2239-296">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="d2239-297">Por `dotnet new` padrão, \* passa para a versão, que representa a versão mais recente do pacote estável.</span><span class="sxs-lookup"><span data-stu-id="d2239-297">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="d2239-298">Veja um exemplo na seção [Exemplos.](#examples)</span><span class="sxs-lookup"><span data-stu-id="d2239-298">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="d2239-299">Se uma versão do modelo já estiver instalada quando você executar este comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão foi especificada.</span><span class="sxs-lookup"><span data-stu-id="d2239-299">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="d2239-300">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="d2239-300">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="d2239-301">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d2239-301">Lists templates containing the specified name.</span></span> <span data-ttu-id="d2239-302">Se nenhum nome for especificado, lista todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="d2239-302">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="d2239-303">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d2239-303">The language of the template to create.</span></span> <span data-ttu-id="d2239-304">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d2239-304">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d2239-305">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d2239-305">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d2239-306">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="d2239-306">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d2239-307">Nesses casos, inclui o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="d2239-307">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="d2239-308">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="d2239-308">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="d2239-309">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d2239-309">The name for the created output.</span></span> <span data-ttu-id="d2239-310">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d2239-310">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="d2239-311">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="d2239-311">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="d2239-312">Disponível desde .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-312">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d2239-313">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d2239-313">Location to place the generated output.</span></span> <span data-ttu-id="d2239-314">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d2239-314">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="d2239-315">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2239-315">Filters templates based on available types.</span></span> <span data-ttu-id="d2239-316">Os valores `project` `item`predefinidos são, ou `other`.</span><span class="sxs-lookup"><span data-stu-id="d2239-316">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="d2239-317">Desinstala um pacote `PATH` de `NUGET_ID` modelo no ou fornecido.</span><span class="sxs-lookup"><span data-stu-id="d2239-317">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d2239-318">Quando `<PATH|NUGET_ID>` o valor não é especificado, todos os pacotes de modelos instalados no momento e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="d2239-318">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="d2239-319">Ao `NUGET_ID`especificar, não inclua o número da versão.</span><span class="sxs-lookup"><span data-stu-id="d2239-319">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="d2239-320">Se você não especificar um parâmetro para essa opção, o comando listaos os modelos e detalhes instalados sobre eles.</span><span class="sxs-lookup"><span data-stu-id="d2239-320">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d2239-321">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="d2239-321">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d2239-322">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="d2239-322">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="d2239-323">Não inclua uma barra final de diretório de terminação no seu caminho de modelo.</span><span class="sxs-lookup"><span data-stu-id="d2239-323">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="d2239-324">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="d2239-324">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="d2239-325">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2239-325">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="d2239-326">Verifique se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="d2239-326">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="d2239-327">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2239-327">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="d2239-328">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="d2239-328">Template options</span></span>

<span data-ttu-id="d2239-329">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2239-329">Each project template may have additional options available.</span></span> <span data-ttu-id="d2239-330">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="d2239-330">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="d2239-331">console</span><span class="sxs-lookup"><span data-stu-id="d2239-331">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-332">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-332">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-333">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2239-333">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2239-334">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-334">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-335">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-335">SDK version</span></span> | <span data-ttu-id="d2239-336">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-336">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-337">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-337">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-338">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-338">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2239-339">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2239-339">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2239-340">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2239-340">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d2239-341">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="d2239-341">Not supported for F#.</span></span> <span data-ttu-id="d2239-342">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-342">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2239-343">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2239-343">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-344">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-344">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="d2239-345">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-345">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="d2239-346">classlib</span><span class="sxs-lookup"><span data-stu-id="d2239-346">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-347">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-347">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-348">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d2239-348">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d2239-349">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d2239-349">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2239-350">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2239-350">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2239-351">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2239-351">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d2239-352">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="d2239-352">Not supported for F#.</span></span> <span data-ttu-id="d2239-353">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-353">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2239-354">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2239-354">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-355">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-355">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="d2239-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d2239-356">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-357">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-357">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-358">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="d2239-358">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d2239-359">Disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-359">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2239-360">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2239-360">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2239-361">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2239-361">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d2239-362">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2239-362">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-363">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-363">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="d2239-364">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="d2239-364">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2239-365">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2239-365">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2239-366">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2239-366">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d2239-367">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2239-367">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-368">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-368">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="d2239-369">trabalhador, grpc</span><span class="sxs-lookup"><span data-stu-id="d2239-369">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-370">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-370">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-371">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="d2239-371">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d2239-372">Disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-372">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-373">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-373">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-374">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-374">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="d2239-375">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="d2239-375">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-376">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-376">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-377">Opção disponível desde .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-377">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2239-378">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-378">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-379">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-379">SDK version</span></span> | <span data-ttu-id="d2239-380">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-380">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-381">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-381">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-382">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-382">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d2239-383">Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d2239-383">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-384">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-384">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="d2239-385">Nunit</span><span class="sxs-lookup"><span data-stu-id="d2239-385">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-386">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-386">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="d2239-387">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-387">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-388">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-388">SDK version</span></span> | <span data-ttu-id="d2239-389">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-389">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-390">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-390">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-391">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-391">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2239-392">2.2</span><span class="sxs-lookup"><span data-stu-id="d2239-392">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="d2239-393">2.1</span><span class="sxs-lookup"><span data-stu-id="d2239-393">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d2239-394">Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d2239-394">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-395">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-395">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="d2239-396">página</span><span class="sxs-lookup"><span data-stu-id="d2239-396">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d2239-397">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-397">Namespace for the generated code.</span></span> <span data-ttu-id="d2239-398">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d2239-398">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="d2239-399">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="d2239-399">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="d2239-400">verimportações, proto</span><span class="sxs-lookup"><span data-stu-id="d2239-400">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d2239-401">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-401">Namespace for the generated code.</span></span> <span data-ttu-id="d2239-402">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d2239-402">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="d2239-403">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d2239-403">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2239-404">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2239-404">The type of authentication to use.</span></span> <span data-ttu-id="d2239-405">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2239-405">The possible values are:</span></span>

  - <span data-ttu-id="d2239-406">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2239-406">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2239-407">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d2239-407">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d2239-408">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d2239-408">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2239-409">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d2239-409">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2239-410">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d2239-410">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d2239-411">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2239-411">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2239-412">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-412">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2239-413">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-413">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-414">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2239-414">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2239-415">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-415">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2239-416">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-416">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d2239-417">O iD da política de senha redefinida para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-417">The reset password policy ID for this project.</span></span> <span data-ttu-id="d2239-418">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-418">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d2239-419">O ID de política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-419">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d2239-420">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-420">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2239-421">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-421">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2239-422">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-422">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2239-423">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2239-423">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2239-424">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-424">The Client ID for this project.</span></span> <span data-ttu-id="d2239-425">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-425">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2239-426">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2239-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2239-427">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="d2239-427">The domain for the directory tenant.</span></span> <span data-ttu-id="d2239-428">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-429">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2239-429">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2239-430">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-430">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2239-431">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2239-432">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2239-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d2239-433">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d2239-433">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d2239-434">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-434">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-435">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d2239-435">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2239-436">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d2239-436">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2239-437">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-437">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-438">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-438">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2239-439">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2239-439">Turns off HTTPS.</span></span> <span data-ttu-id="d2239-440">Esta opção só `Individual`se `IndividualB2C` `SingleOrg`aplica `MultiOrg` se , , `--auth`ou não estiver sendo usado para .</span><span class="sxs-lookup"><span data-stu-id="d2239-440">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2239-441">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2239-441">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2239-442">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-442">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-443">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-443">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="d2239-444">web</span><span class="sxs-lookup"><span data-stu-id="d2239-444">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-445">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-445">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-446">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-446">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-447">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-447">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2239-448">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-448">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-449">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-449">SDK version</span></span> | <span data-ttu-id="d2239-450">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-450">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-451">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-451">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-452">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-452">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2239-453">2.1</span><span class="sxs-lookup"><span data-stu-id="d2239-453">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d2239-454">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-454">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2239-455">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2239-455">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="d2239-456">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="d2239-456">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2239-457">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2239-457">The type of authentication to use.</span></span> <span data-ttu-id="d2239-458">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2239-458">The possible values are:</span></span>

  - <span data-ttu-id="d2239-459">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2239-459">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2239-460">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d2239-460">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d2239-461">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d2239-461">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2239-462">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d2239-462">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2239-463">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d2239-463">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d2239-464">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2239-464">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2239-465">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-465">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2239-466">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-466">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-467">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2239-467">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2239-468">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-468">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2239-469">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-469">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d2239-470">O iD da política de senha redefinida para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-470">The reset password policy ID for this project.</span></span> <span data-ttu-id="d2239-471">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-471">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d2239-472">O ID de política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-472">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d2239-473">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-473">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2239-474">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-474">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2239-475">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-475">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2239-476">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2239-476">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2239-477">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-477">The Client ID for this project.</span></span> <span data-ttu-id="d2239-478">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-478">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2239-479">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2239-479">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2239-480">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="d2239-480">The domain for the directory tenant.</span></span> <span data-ttu-id="d2239-481">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-481">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-482">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2239-482">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2239-483">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-483">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2239-484">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-484">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2239-485">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2239-485">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d2239-486">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d2239-486">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d2239-487">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-487">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-488">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d2239-488">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2239-489">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d2239-489">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2239-490">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-490">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-491">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-491">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2239-492">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2239-492">Turns off HTTPS.</span></span> <span data-ttu-id="d2239-493">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="d2239-493">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2239-494">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2239-494">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2239-495">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-495">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-496">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-496">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-497">Opção disponível desde .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-497">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2239-498">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-498">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-499">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-499">SDK version</span></span> | <span data-ttu-id="d2239-500">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-500">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-501">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-501">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-502">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-502">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="d2239-503">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-503">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="d2239-504">Inclui o BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-504">Includes BrowserLink in the project.</span></span> <span data-ttu-id="d2239-505">Opção não disponível em .NET Core 2.2 e 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-505">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="d2239-506">Determina se o projeto está configurado para usar a [compilação Razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações Debug.</span><span class="sxs-lookup"><span data-stu-id="d2239-506">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="d2239-507">Opção disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-507">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="d2239-508">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="d2239-508">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2239-509">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2239-509">The type of authentication to use.</span></span> <span data-ttu-id="d2239-510">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2239-510">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="d2239-511">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2239-511">The possible values are:</span></span>

  - <span data-ttu-id="d2239-512">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2239-512">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2239-513">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d2239-513">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-514">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-514">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-515">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-515">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2239-516">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2239-516">Turns off HTTPS.</span></span> <span data-ttu-id="d2239-517">Essa opção só se aplica `None`se a autenticação for .</span><span class="sxs-lookup"><span data-stu-id="d2239-517">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2239-518">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2239-518">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2239-519">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-519">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-520">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2239-520">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-521">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-521">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-522">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-522">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2239-523">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-523">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-524">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-524">SDK version</span></span> | <span data-ttu-id="d2239-525">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-525">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-526">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-526">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-527">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-527">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2239-528">2.1</span><span class="sxs-lookup"><span data-stu-id="d2239-528">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="d2239-529">reactredux</span><span class="sxs-lookup"><span data-stu-id="d2239-529">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-530">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-530">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-531">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-531">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-532">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-532">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2239-533">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-533">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-534">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-534">SDK version</span></span> | <span data-ttu-id="d2239-535">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-535">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-536">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-536">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-537">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-537">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2239-538">2.1</span><span class="sxs-lookup"><span data-stu-id="d2239-538">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="d2239-539">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2239-540">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2239-540">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="d2239-541">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d2239-541">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2239-542">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-542">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="d2239-543">Suporta a adição de páginas e visualizações tradicionais de navalha, além de componentes para esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d2239-543">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="d2239-544">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2239-544">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="d2239-545">webapi</span><span class="sxs-lookup"><span data-stu-id="d2239-545">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2239-546">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2239-546">The type of authentication to use.</span></span> <span data-ttu-id="d2239-547">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2239-547">The possible values are:</span></span>

  - <span data-ttu-id="d2239-548">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2239-548">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2239-549">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d2239-549">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2239-550">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d2239-550">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2239-551">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2239-551">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2239-552">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-552">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2239-553">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-553">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2239-554">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2239-554">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2239-555">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-555">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2239-556">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2239-556">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2239-557">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-557">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2239-558">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-558">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2239-559">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2239-559">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2239-560">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-560">The Client ID for this project.</span></span> <span data-ttu-id="d2239-561">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d2239-562">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2239-562">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2239-563">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="d2239-563">The domain for the directory tenant.</span></span> <span data-ttu-id="d2239-564">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-564">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d2239-565">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2239-565">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2239-566">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2239-566">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2239-567">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2239-567">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2239-568">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2239-568">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2239-569">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d2239-569">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2239-570">Só se `SingleOrg` aplica à autenticação.</span><span class="sxs-lookup"><span data-stu-id="d2239-570">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2239-571">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2239-571">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2239-572">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2239-572">Turns off HTTPS.</span></span> <span data-ttu-id="d2239-573">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="d2239-573">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="d2239-574">Essa opção só `IndividualB2C` se `SingleOrg` aplica se ou não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="d2239-574">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2239-575">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2239-575">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2239-576">Só se `IndividualB2C` aplica à autenticação.</span><span class="sxs-lookup"><span data-stu-id="d2239-576">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2239-577">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2239-577">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2239-578">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2239-578">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2239-579">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2239-579">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2239-580">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2239-580">SDK version</span></span> | <span data-ttu-id="d2239-581">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2239-581">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2239-582">3.1</span><span class="sxs-lookup"><span data-stu-id="d2239-582">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2239-583">3.0</span><span class="sxs-lookup"><span data-stu-id="d2239-583">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2239-584">2.1</span><span class="sxs-lookup"><span data-stu-id="d2239-584">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d2239-585">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2239-585">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="d2239-586">globaljson</span><span class="sxs-lookup"><span data-stu-id="d2239-586">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="d2239-587">Especifica a versão do .NET Core SDK para usar no arquivo *global.json.*</span><span class="sxs-lookup"><span data-stu-id="d2239-587">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="d2239-588">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d2239-588">Examples</span></span>

- <span data-ttu-id="d2239-589">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="d2239-589">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="d2239-590">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d2239-590">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="d2239-591">Criar um projeto de biblioteca de classe .NET padrão no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="d2239-591">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="d2239-592">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="d2239-592">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="d2239-593">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="d2239-593">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="d2239-594">Liste todos os modelos disponíveis para os modelos spa (Single Page Application, aplicativo de página única):</span><span class="sxs-lookup"><span data-stu-id="d2239-594">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="d2239-595">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="d2239-595">List all templates matching the *we* substring.</span></span> <span data-ttu-id="d2239-596">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="d2239-596">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="d2239-597">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="d2239-597">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="d2239-598">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="d2239-598">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="d2239-599">Instale a versão 2.0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="d2239-599">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="d2239-600">Liste os modelos e detalhes instalados sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="d2239-600">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="d2239-601">Crie um *global.json* no diretório atual definindo a versão SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="d2239-601">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="d2239-602">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2239-602">See also</span></span>

- [<span data-ttu-id="d2239-603">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2239-603">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="d2239-604">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="d2239-604">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="d2239-605">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="d2239-605">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="d2239-606">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2239-606">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
